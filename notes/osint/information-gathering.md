# Information Gathering (OSINT)

Information gathering is the first phase of a penetration test.

The goal is to collect as much information as possible about a target before interacting directly with its infrastructure.

This phase focuses primarily on **passive reconnaissance**, meaning techniques that do not directly interact with the target systems.

---

## Passive Reconnaissance

Passive reconnaissance involves gathering information from publicly available sources.

Examples include:

- search engines
- company websites
- social media
- public databases
- leaked data sources

This information can help identify:

- domains
- subdomains
- employees
- email formats
- technologies used by the organization

---

## Useful OSINT Resources

Common platforms used during reconnaissance:

- Hunter.io
- HaveIBeenPwned
- LinkedIn
- Wayback Machine
- Shodan
- Google Hacking Database

These platforms help identify:

- exposed services
- employee information
- breach data
- historical web content

---

## Search Engine Techniques (Google Dorking)

Search engines can reveal sensitive information if used correctly.

Examples of useful queries:

```
site:example.com
filetype:pdf
intitle:"index of"
inurl:admin
```

These queries may reveal:

- exposed documents

- backup files

- login portals

- internal resources

---

## Email Discovery

Email addresses are often useful during security assessments.

Possible discovery sources:

- company websites

- LinkedIn profiles

- breach databases

- OSINT tools

Example tools:

- Hunter.io

- EmailHippo

- HaveIBeenPwned

---

## Historical Data

The Wayback Machine allows viewing archived versions of websites.

Useful for discovering:

- old endpoints

- removed content

- previous infrastructure

- outdated technologies

Example usage: https://web.archive.org

---

## Infrastructure Discovery

Public infrastructure can sometimes be identified through OSINT.

Examples:

- exposed IP addresses

- DNS records

- public services

Tools commonly used:

- Shodan

- Censys

- DNSdumpster

---

## Notes

OSINT techniques should always be used responsibly and within legal boundaries.

Information gathered during this phase should be verified through multiple sources before being considered reliable.