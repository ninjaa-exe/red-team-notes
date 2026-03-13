# Gobuster

Gobuster is a tool used for brute-forcing URIs (directories and files) in web applications.

It is commonly used during the **enumeration phase** of penetration testing to discover hidden directories, files or subdomains.

---

# Installation

Gobuster is included in Kali Linux.

If not installed:

```bash
sudo apt install gobuster
```

Verify installation: ``` gobuster --version ```

---

# Basic Directory Enumeration

Basic directory brute force: ```bash gobuster dir -u http://target.com -w /usr/share/wordlists/dirb/common.txt ```

Parameters:

- ```dir``` → directory enumeration mode

- ```-u``` → target URL

- ```-w``` → wordlist

---

# Using Extensions

Sometimes web applications use specific file extensions.

Example: ```bash gobuster dir -u http://target.com -w wordlist.txt -x php,txt,html ```

This tests files such as:

- index.php

- login.php

- admin.html

---

# Increasing Threads

Speed up scanning with multiple threads: ```bash gobuster dir -u http://target.com -w wordlist.txt -t 50 ```

Parameter:

- ```-t``` → number of threads

---

# Ignoring Status Codes

Sometimes certain HTTP responses should be ignored.

Example: ```bash gobuster dir -u http://target.com -w wordlist.txt -b 403,404 ```

Parameter:

- ```-b``` → blacklist status codes

---

# Subdomain Enumeration

Gobuster can also brute force subdomains.

Example: ``` gobuster dns -d example.com -w subdomains.txt ```

Parameters:

- ```dns``` → DNS enumeration mode

- ```-d``` → target domain

---

# Output Results

Save results to a file: ```bash gobuster dir -u http://target.com -w wordlist.txt -o results.txt ```

---

# Common Wordlists

Useful wordlists in Kali:

```
/usr/share/wordlists/dirb/common.txt
/usr/share/seclists/Discovery/Web-Content/
```
SecLists is one of the most widely used collections of wordlists.

---

# Notes

Directory brute forcing can generate a large number of requests.

Adjust scan speed and thread count depending on the environment to avoid detection or server overload.

Always perform enumeration only in **authorized environments.**