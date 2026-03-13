# Vulnerabilities

This section documents common security vulnerabilities encountered during penetration testing and security research.

The goal is to explain how these vulnerabilities work, how they can be identified and what their potential impact is.

These notes focus on practical understanding and are intended for use in:

- penetration testing labs
- Capture The Flag (CTF) challenges
- vulnerability research
- general cybersecurity studies

---

# Categories

## Web Vulnerabilities

Common vulnerabilities found in web applications.

Examples include:

- SQL Injection
- Cross-Site Scripting (XSS)
- File Upload vulnerabilities

These vulnerabilities often result from improper input validation or insecure application logic.

---

## Memory Vulnerabilities

Low-level vulnerabilities related to improper memory management.

Example:

- Buffer Overflow

These vulnerabilities are often found in software written in languages such as C or C++.

---

## Public Vulnerabilities (CVE)

Documented vulnerabilities publicly tracked using CVE identifiers.

Examples:

- CVE references
- vulnerability descriptions
- severity ratings (CVSS)

CVE databases are commonly used during penetration testing to identify known vulnerabilities affecting specific software versions.

---

# Structure

```text
vulnerabilities
├── web
│   ├── sql-injection.md
│   ├── xss.md
│   └── file-upload.md
├── buffer-overflow.md
└── cve
    └── README.md
```

---

# Notes

Understanding vulnerabilities is essential for identifying security weaknesses during penetration testing.

All testing and exploitation should only be performed in **authorized environments** such as labs, CTF platforms or permitted security assessments.