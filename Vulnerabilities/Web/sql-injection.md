# SQL Injection

SQL Injection (SQLi) is a web vulnerability that allows an attacker to interfere with queries made to a database.

It occurs when user input is improperly validated and directly included in SQL queries.

Attackers may exploit SQL injection to:

- bypass authentication
- extract sensitive data
- modify database content
- execute administrative operations

---

# Basic Example

Consider the following SQL query:

```sql
SELECT * FROM users WHERE username = 'admin' AND password = 'password';
```

If user input is not sanitized, an attacker could manipulate the query.

Example input: ``` admin' -- ```

Resulting query: ```sql SELECT * FROM users WHERE username = 'admin' -- ' AND password = 'password'; ```

The ```--``` comment operator causes the password check to be ignored.

---

# Common Types of SQL Injection
Authentication Bypass

Allows an attacker to log in without valid credentials.

Example payload: ``` ' OR 1=1 -- ```

Resulting query: ```sql SELECT * FROM users WHERE username = '' OR 1=1 -- ' AND password = ''; ```

Since ```1=1``` is always true, authentication may succeed.

---

# Union-Based Injection

Uses the SQL UNION operator to extract data from other tables.

Example: ``` ' UNION SELECT null, username, password FROM users -- ```

This may allow an attacker to retrieve credentials from the database.

---

# Error-Based Injection

Relies on database error messages to reveal information.

Example: ``` ' AND 1=CONVERT(int,(SELECT @@version)) -- ```

The error message may reveal database version details.

---

# Blind SQL Injection

Occurs when the application does not display database errors.

Attackers must infer information using logical conditions.

Example: ``` ' AND 1=1 -- ``` versus ``` ' AND 1=2 -- ```

Differences in the application response may reveal whether a condition is true or false.

# Time-Based Blind Injection

Uses time delays to infer results.

Example: ```sql ' OR IF(1=1,SLEEP(5),0) -- ```

If the server delays its response, the condition is true.

---

# Detecting SQL Injection

Indicators of SQL injection may include:

- unusual database errors

- unexpected application responses

- delays in server responses

- abnormal login behavior

Manual testing often involves modifying parameters and observing responses.

---

# Exploitation Tools

Common tools used to exploit SQL injection:

- SQLMap

- Burp Suite

- custom scripts

Example using SQLMap: ```bash sqlmap -u "http://target.com/page.php?id=1" --dbs ```

---

# Prevention

Common mitigation techniques include:

- parameterized queries

- prepared statements

- input validation

- least privilege database accounts

Example (prepared statement): ```sql SELECT * FROM users WHERE username = ? AND password = ? ```

---

# Notes

SQL injection vulnerabilities can have severe impact because databases often contain sensitive information.

Modern frameworks reduce the risk of SQL injection when secure coding practices are followed.