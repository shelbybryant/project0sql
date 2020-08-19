# project0sql
This is my sql code for project 0

```sql
--creating customer TABLE

DROP TABLE IF EXISTS customers CASCADE;

CREATE TABLE customers (
	customer_id INTEGER PRIMARY KEY,
	first_name VARCHAR(30),
	last_name VARCHAR(30),
	customer_password VARCHAR (30),
	phone_number VARCHAR(30),
	street_address VARCHAR(30),
	city VARCHAR(30),
	state VARCHAR(30),
	zip_code INTEGER,
	account_number_fk INTEGER REFERENCES accounts(account_number)
);


--making accounts

DROP TABLE IF EXISTS accounts;

CREATE TABLE accounts (
	account_number INTEGER PRIMARY KEY,
	checkings_balance NUMERIC(9,2),
	savings_balance NUMERIC(9,2),
	previous_checking_transaction NUMERIC(9,2),
	previous_saving_transaction NUMERIC(9,2),
	approved_account BOOLEAN,
	canceled_account BOOLEAN
);

--employee

DROP TABLE IF EXISTS employees;

CREATE TABLE employees (
	employee_id INTEGER,
	first_name VARCHAR (30),
	last_name VARCHAR (30),
	employee_password VARCHAR (30),
	is_admin BOOLEAN
);

--making employees

INSERT INTO employees (employee_id, first_name, last_name, employee_password, is_admin)
	VALUES (1, 'Leslie', 'Knope', 'pawnee', TRUE),
	(2, 'Andy', 'Dwyer', 'mouserat', FALSE);

--dummy info

INSERT INTO accounts (account_number, checkings_balance, savings_balance, previous_checking_transaction, previous_saving_transaction, approved_account, canceled_account)
	VALUES (1,3000.01, 5025.75, 3.00, 50.50, TRUE, TRUE),	
	 (2, 500.25, 1234.56, 50.01, 35.67, TRUE, FALSE);

INSERT INTO customers (customer_id, first_name, last_name, customer_password, phone_number, street_address, city, state, zip_code, account_number_fk)
	VALUES (1, 'Obi', 'Wan', 'theforce', '234567890', '234 star wars', 'Bedford', 'Tatoine', 47421, 1),	
	 (2, 'Shelby', 'Bryant', 'password', '12345678', '123 Easy Street', 'Bloomington', 'IN', 47403, 2);
	

--using a join 

	SELECT * FROM customers JOIN accounts ON account_number = account_number_fk;

```
