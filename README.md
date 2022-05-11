# Introduction To The SQLi

Whole Repository is dedicated to SQL Injection

This Repository is contains Mostly every Type of SQLi - That can be performed on the Target Machine

### What SQLi is ??

SQL injection is a technique through which attackers can execute their own malicious Malicious Payload

### Causes of SQLi ??

- Applications will often need dynamic SQL queries to be able to display content 
based on different conditions To allow for dynamic SQL queries But,
**Developers often concatenate user input directly into the SQL statement.**
String concatenation becomes the most common mistake that leads to SQL injection vulnerability

- **Input field must be sanitized**. otherwise The query will be vulnerable to SQL injection Attack

## Vulnerabe Code

### Dynamic SQL query in a login from

A PHP Code 

```Markdown
$query = "SELECT * FROM users WHERE username='" + $_POST["user"] + "' AND password= '" + $_POST["password"]$ + '";"
```
*How can we Make Above Code Vulnerable*

```Markdown
SELECT * FROM users WHERE username = '' OR 1=1-- -' AND password = ''
```
- If the attacker supplies the value  ```' OR 1=1-- -``` inside the name parameter
  - Query might return more than one user
  - Most applications will process the first user returned
  - Meaning that the attacker can exploit this and log in as the first user the query returned
- ```--``` Sequence is a comment indicator in SQL and causes the rest of the query to be commented out.
- In SQL, a string is enclosed within either a single quote (') or a double quote ("). The single quote (') in the input is used to close the string literal.
  - If the attacker enters **' OR 1=1-- - in the name parameter and leaves the password blank**
    - ``` SELECT * FROM users WHERE username = '' OR 1=1-- -' AND password = '' ```
- If the Database executes the above query Then, The Attacker bypasses the authentication mechanism and get Logged in as First User
- The reason for using  ```-- -``` instead of ```--``` is primarily because of how MySQL handles the double-dash comment style
 -  A ```--```  sequence to the end of the line. In MYSQL, the ```--``` (double-dash) comment style requires the second dash to be followed by at least **one whitespace or control character (such as a space, tab, newline, and so on).**

[Go to the next page](/)
