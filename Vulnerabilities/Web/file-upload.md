# File Upload Vulnerability

File upload vulnerabilities occur when a web application allows users to upload files without proper validation or restrictions.

If not properly secured, an attacker may upload malicious files that can be executed on the server.

This can lead to serious consequences such as:

- remote code execution
- server compromise
- data theft
- malware distribution

---

# Basic Example

A website allows users to upload profile pictures.

If the application does not validate file types correctly, an attacker might upload a malicious script instead of an image.

Example malicious file:

```php
<?php system($_GET['cmd']); ?>
```

If the file is uploaded and accessible via the web server, an attacker could execute commands: ``` http://target.com/uploads/shell.php?cmd=id ```

# Common Exploitation Techniques

## Uploading Web Shells

Attackers may upload scripts that allow remote command execution.

Examples:

- PHP web shells

- ASP web shells

- JSP web shells

Example simple PHP web shell: ```php <?php system($_GET['cmd']); ?> ```

---

## File Extension Bypass

Some applications only check file extensions.

Attackers may bypass this by using alternative extensions.

Examples:

```
shell.php.jpg
shell.php.png
shell.phtml
```

Some servers still interpret these files as executable scripts.

---

## MIME Type Manipulation

Applications may check the file type using the MIME header.

Example request header: ``` Content-Type: image/jpeg ```

An attacker may modify the header while uploading a malicious file.

Tools such as Burp Suite can intercept and modify these requests.

---

## Double Extensions

Some filters only check the last extension.

Example: ``` shell.php.jpg ```

If the server processes the first extension, the file may still execute.

---

## Upload Directory Misconfiguration

Sometimes uploaded files are stored in directories accessible through the web server.

Example:

```
/uploads/
/images/
/files/
```

If scripts can be executed in these directories, attackers may gain remote access.

---

# Detection

File upload vulnerabilities can be identified by testing the upload functionality with different file types.

Tests may include:

- uploading script files

- modifying file extensions

- altering MIME types

- uploading large or unusual files

Tools commonly used:

- Burp Suite

- browser developer tools

---

# Prevention

Secure file upload mechanisms should include:

strict file type validation

server-side file verification

renaming uploaded files

storing uploads outside the web root

disabling script execution in upload directories

Example Apache configuration: ```apache php_flag engine off ```

This prevents PHP execution in the upload directory.

---

# Notes

File upload vulnerabilities are often chained with other weaknesses to achieve full system compromise.

Proper validation and secure storage of uploaded files are essential to prevent exploitation.
