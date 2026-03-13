# Burp Suite

Burp Suite is a web security testing platform used to analyze and manipulate HTTP/HTTPS traffic between a browser and a web application.

It is commonly used during **web application penetration testing** to identify vulnerabilities such as:

- SQL injection
- Cross-Site Scripting (XSS)
- authentication flaws
- access control issues

---

# Installation

Burp Suite is included in Kali Linux.

If not installed:

```bash
sudo apt install burpsuite
```

Start Burp Suite: ```bash burpsuite ```

---

# Basic Workflow

Typical web testing workflow with Burp:

1. Configure the browser proxy

2. Intercept requests

3. Analyze requests and responses

4. Modify requests

5. Test for vulnerabilities

---

# Proxy Configuration

Burp Suite acts as an intercepting proxy between the browser and the target application.

Default proxy settings:
```
IP: 127.0.0.1
Port: 8080
```

Configure your browser to use this proxy.

---


# Intercepting Requests

Enable interception: ``` Proxy → Intercept → Intercept is ON ```

When a request is captured, it can be:

- viewed

- modified

- forwarded

- dropped

---

# Repeater

The Repeater tool allows sending modified HTTP requests multiple times.

Common uses:

testing parameters

manipulating cookies

testing authentication logic

Workflow: ``` Right Click Request → Send to Repeater ```

Then modify the request and click Send.

---

# Intruder

Intruder is used for automated attacks against parameters.

Examples:

- brute force login forms

- testing parameter values

- fuzzing inputs

Steps:

1. Send request to Intruder

2. Select attack positions

3. Choose payload type

4. Launch attack

---

# Decoder

Decoder is used to encode or decode data.

Common formats:

- Base64

- URL encoding

- HTML encoding

Workflow: ``` Send data to Decoder → choose decode method ```

---

# Comparer

Comparer allows comparing two pieces of data.

Useful for:

- analyzing response differences

- comparing authentication tokens

- testing parameter changes

---

Useful Tips

Disable interception when browsing normally to avoid blocking requests.

Use Burp together with tools such as:

- SQLMap

- ffuf

- Gobuster

---

# Notes

Burp Suite Community Edition provides the core functionality needed for manual web application testing.

Always perform web security testing only in **authorized environments.**