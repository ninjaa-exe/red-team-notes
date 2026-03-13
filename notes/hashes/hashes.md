# Hashes

A hash function transforms input data into a fixed-length value.

Hash functions are commonly used for password storage and data integrity.

---

## Properties of Cryptographic Hashes

- deterministic
- fixed output length
- one-way (not reversible)
- collision resistant

Examples:

- MD5
- SHA1
- SHA256
- NTLM

---

## Hash vs Encryption vs Encoding

### Hash
One-way transformation.

Example: password -> 5f4dcc3b5aa765d61d8327deb882cf99

### Encryption
Reversible transformation using a key.

Examples:
- AES
- RSA

### Encoding
Representation format.

Examples:
- Base64
- URL encoding

Encoding is **not encryption**.

---

## Identifying Hashes

Tools:

- hashid
- hash-identifier

Example: ```bash hashid <hash> ```

---

## Cracking Hashes

Common techniques:

- dictionary attacks
- brute force
- rule-based mutations
- rainbow tables

Tools:

- John the Ripper
- Hashcat

Example: ```bash john hashes.txt --wordlist=rockyou.txt ```

---

## Encryption

Encryption is a reversible transformation that uses a key.

Examples:

- AES

- RSA

---

## Encoding

Encoding is a representation format.

Examples:

- Base64

- URL encoding

Encoding is not encryption.

---

## Identifying Hashes

Common tools:

- hashid

- hash-identifier

Example: ```bash hashid 5f4dcc3b5aa765d61d8327deb882cf99 ```

---

## Cracking Hashes

Common techniques:

- Dictionary attacks

- Brute force

- Rule-based mutations

- Rainbow tables

Common tools:

- John the Ripper

- Hashcat

Example with John: ```bash john hashes.txt --wordlist=rockyou.txt ```

Example with Hashcat: ```bash hashcat -m 0 hashes.txt rockyou.txt ```

---

## Windows Hashes
SAM

Windows stores local account password hashes in the SAM database.

Common location: C:\Windows\System32\config\SAM

To extract the necessary registry hives: ```bash reg save HKLM\SAM sam.save / reg save HKLM\SYSTEM system.save ```

Useful tools:

- secretsdump

- mimikatz

Example with Impacket: ```bash secretsdump.py -sam sam.save -system system.save LOCAL ```

NTDS.dit

In Active Directory environments, password hashes can be stored in: C:\Windows\NTDS\NTDS.dit
This file is commonly targeted during post-exploitation.

---

## Linux Password Hashes

Linux password hashes are usually stored in: /etc/shadow

A common workflow is combining /etc/passwd and /etc/shadow before cracking: ```bash unshadow /etc/passwd /etc/shadow > hashes.txt /john hashes.txt ```

---

## Notes

Password cracking is usually performed offline after obtaining password hashes.

Always perform these actions only in authorized environments such as labs, CTFs or permitted security assessments.