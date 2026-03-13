# Nmap

Nmap (Network Mapper) is one of the most widely used tools for network discovery and service enumeration.

It is commonly used during the **enumeration phase** of penetration testing to identify open ports, running services and potential vulnerabilities.

---

# Installation

Kali Linux usually includes Nmap by default.

If not installed:

```bash
sudo apt install nmap
```

Verify installation: ```bash nmap --version ```

---

# Basic Usage

Basic scan of a target: ```bash nmap target_ip ```

Scan multiple targets: ```bash nmap target_ip1 target_ip2 ```

Scan a subnet: ```bash nmap 192.168.1.0/24 ```

---

# Common Scan Options

## Service Version Detection

```bash
nmap -sV target_ip
```

Identifies service versions running on open ports.

---

## Default Script Scan
```bash
nmap -sC target_ip
```

Runs default Nmap scripts to gather additional information.

---

## Full Port Scan
```bash
nmap -p- target_ip
```

Scans all 65535 ports.

---

## Aggressive Scan
```bash
nmap -A target_ip
```

Includes:

- OS detection

- version detection

- script scanning

- traceroute

---

## Useful Combinations

A common scan during pentesting:
```bash
nmap -sC -sV -p- target_ip
```

This performs:

- default script scan

- service version detection

- full port scan

---

## OS Detection
```bash
nmap -O target_ip
```

Attempts to identify the operating system of the target.

---

## UDP Scan
```bash
nmap -sU target_ip
```

Scans UDP services.

UDP scans are usually slower than TCP scans.

---

## Output Options

Save results to a file:
```bash
nmap -oN scan.txt target_ip
```

Save results in multiple formats:
```bash
nmap -oA scan target_ip
```

Scans UDP services.

UDP scans are usually slower than TCP scans.

---

# Notes

Nmap scans can generate noticeable network traffic.

During real engagements it is important to adjust scan speed and techniques to avoid detection.

Always perform scans in **authorized environments** only.