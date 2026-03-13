# CVE (Common Vulnerabilities and Exposures)

CVE stands for **Common Vulnerabilities and Exposures**.

It is a publicly available list of known cybersecurity vulnerabilities maintained by the MITRE Corporation.

Each vulnerability is assigned a unique identifier.

Example:

```text
CVE-2021-44228
```

This identifier refers to the **Log4Shell vulnerability** in the Log4j library.

---

# CVE Identifier Format

A CVE ID follows this format: ``` CVE-YEAR-ID ```

Example: ``` CVE-2017-0144 ```

Components:

- CVE → vulnerability identifier

- YEAR → year the vulnerability was published

- ID → unique identifier

---

# Finding CVEs

During penetration testing, CVEs are often discovered by identifying software versions.

Example workflow:

1. Discover service using Nmap

2. Identify version information

3. Search for known vulnerabilities

Example Nmap scan: ```bash nmap -sV target_ip ```

Output example: ``` Apache httpd 2.4.49 ```

Then search for vulnerabilities related to that version.

---

# Useful CVE Databases

Common resources used to search for vulnerabilities:

- NVD (National Vulnerability Database)
https://nvd.nist.gov

- MITRE CVE Database
https://cve.mitre.org

- Exploit-DB
https://www.exploit-db.com

- CVE Details
https://www.cvedetails.com

These databases provide:

- vulnerability descriptions

- severity ratings

- affected software versions

- references and exploits

---

# CVSS (Common Vulnerability Scoring System)

Many CVEs include a CVSS score, which indicates the severity of a vulnerability.

CVSS scores range from: ``` 0.0 – 10.0 ```

Severity levels:

```
0.0 – 3.9   Low
4.0 – 6.9   Medium
7.0 – 8.9   High
9.0 – 10.0  Critical
```

The score considers factors such as:

- attack complexity

- required privileges

- user interaction

- impact on confidentiality, integrity and availability

---

# Searching for Exploits

After identifying a CVE, penetration testers often search for public exploits.

Example using Searchsploit: ```bash searchsploit apache 2.4.49 ```

Example output: ``` Apache 2.4.49 - Path Traversal ```

Searchsploit retrieves exploits from the Exploit-DB database.

---

# Notes

Not every CVE has a publicly available exploit.

Even when exploits exist, they may require modification depending on the target environment.

Understanding the vulnerability and affected software is important before attempting exploitation.

Always perform vulnerability testing only in **authorized environments.**