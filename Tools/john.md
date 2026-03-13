# John the Ripper

John the Ripper is a password cracking tool used to recover plaintext passwords from hashed values.

It supports many hash formats including:

- MD5
- SHA1
- SHA256
- NTLM
- bcrypt
- Unix password hashes

John is commonly used during penetration testing to crack password hashes obtained from compromised systems.

---

# Installation

John the Ripper is included in Kali Linux.

If not installed:

```bash
sudo apt install john
```

Verify installation: ```bash john --list=build=info ```

---

# Basic Usage

Basic cracking attempt using a wordlist: ```bash john hashes.txt --wordlist=rockyou.txt ```

This attempts to match passwords from the wordlist against the provided hashes.

---

# Viewing Cracked Passwords

After a cracking session finishes: ```bash john --show hashes.txt ```

This displays recovered passwords.

---

# Identifying Hash Formats

Sometimes it is necessary to specify the hash format manually.

Example: ```bash john hashes.txt --format=NT ```

List supported formats: ```bash john --list=formats ```

---

# Wordlist Attacks

Wordlist attacks are the most common approach.

Example: ```bash john hashes.txt --wordlist=/usr/share/wordlists/rockyou.txt ```

Common wordlists:

```
/usr/share/wordlists/rockyou.txt
/usr/share/seclists/Passwords/
```

---

# Rule-Based Attacks

John can mutate words from a wordlist using rules.

Example: ```bash john hashes.txt --wordlist=rockyou.txt --rules ```

Rules generate variations such as:

- Password123

- password!

- P@ssword

---

# Incremental Mode (Brute Force)

Incremental mode attempts many combinations automatically.

Example: ```bash john hashes.txt --incremental ```

This method is slower but can discover passwords not present in wordlists.

---

# Cracking Linux Password Hashes

Combine ```/etc/passwd``` and ```/etc/shadow``` using unshadow:

```bash
unshadow passwd shadow > hashes.txt
john hashes.txt
```

---

# Cracking Windows Hashes

Windows NTLM hashes can also be cracked.

Example: ```bash john ntlm_hashes.txt --format=NT ```

---

# Session Management

Save a cracking session: ```bash john hashes.txt --session=session_name ```

Resume session: ```bash john --restore=session_name ```

---

# Notes

Password cracking is usually performed offline after obtaining password hashes.

Wordlist attacks with good dictionaries are typically much faster than brute-force attacks.

Always perform password cracking only in **authorized environments.**