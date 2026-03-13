# Brute Force

Brute force attacks attempt to discover credentials or cryptographic keys by systematically trying many possibilities.

These techniques are commonly used during penetration testing when authentication mechanisms are present.

---

## Common Approaches

---

### Wordlist Attacks
Using a predefined list of common passwords.

Example tools:
- Hydra
- John the Ripper
- Hashcat

---

### Password Spraying
Testing a small number of common passwords against many accounts.

Example: ```bash hydra -L users.txt -p Password123 ssh://target ```

---

### Dictionary + Mutation
Applying mutation rules to a wordlist.

Example with John: ```bash john --wordlist=rockyou.txt --rules hashes.txt ```

---

### Keyspace Brute Force
Trying every possible combination.

Usually used when the keyspace is small (e.g. PIN codes).

Example: ```bash crunch 4 4 0123456789 ```

---

## Low Hanging Fruit

Many systems still use:

- default credentials
- weak passwords
- reused passwords

These should always be tested first.

---

## Notes

Brute force attacks can generate significant noise and may trigger detection systems.
Always perform these techniques in authorized environments.
