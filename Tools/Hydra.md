# Hydra

Hydra is a fast network login cracker used to perform brute force attacks against various services.

It supports many protocols, including:

- SSH
- FTP
- HTTP
- HTTPS
- SMB
- RDP
- Telnet

Hydra is commonly used during penetration testing to test **weak or reused credentials**.

---

# Installation

Hydra is included in Kali Linux.

If not installed:

```bash
sudo apt install hydra
```

Verify installation: ```bash hydra -h ```

---

# Basic Usage

Basic syntax: ```bash hydra -l username -P wordlist.txt service://target ```

Parameters:

- ```-l``` → single username

- ```-L``` → username list

- ```-p``` → single password

- ```-P``` → password list

---

# SSH Brute Force

Example: ```bash hydra -l root -P rockyou.txt ssh://target_ip ```

This attempts to authenticate with username root using passwords from the wordlist.

---

# FTP Brute Force

Example: ```bash hydra -l ftp -P rockyou.txt ftp://target_ip ```

Useful when anonymous login is disabled.

---

# HTTP Login Form

Hydra can brute force web login forms.

Example: ```bash hydra -l admin -P rockyou.txt target.com http-post-form "/login.php:user=^USER^&pass=^PASS^:F=incorrect" ```

Parameters:

- ```^USER^``` → placeholder for usernames

- ```^PASS^``` → placeholder for passwords

- ```F=``` → failure message

---

# Multiple Usernames

Example using a username list: ```bash hydra -L users.txt -P passwords.txt ssh://target_ip ```

---

# Increasing Speed

Use multiple threads: ```bash hydra -l admin -P passwords.txt ssh://target_ip -t 16 ```

Parameter:

- ```-t``` → number of parallel tasks

---

# Output Results

Save results to a file: ```bash hydra -l admin -P passwords.txt ssh://target_ip -o results.txt ```

---

# Common Wordlists

Common wordlists in Kali Linux:

```
/usr/share/wordlists/rockyou.txt
/usr/share/seclists/Passwords/
```

SecLists is widely used during password attacks.

---

# Notes

Brute force attacks generate many authentication attempts and may trigger account lockouts or detection systems.

Always perform credential testing only in **authorized environments.**