# Linux Privilege Escalation

Privilege escalation occurs when a user gains higher permissions on a system.

In Linux environments this usually means obtaining **root access** after gaining initial access to the system.

The goal of privilege escalation is to identify misconfigurations, vulnerable services or weak permissions that allow a user to execute commands with higher privileges.

---

# Initial Enumeration

The first step in privilege escalation is collecting system information.

Useful commands:

```bash
id
whoami
uname -a
sudo -l
ps aux
```
These commands help identify:

- current user privileges

- kernel version

- running processes

- sudo permissions

---

## Sudo Permissions

Misconfigured sudo permissions can allow privilege escalation.

Check sudo permissions: ```bash sudo -l ```

Look for:

- commands that can be executed without a password

- binaries that can be abused

Useful reference:

https://gtfobins.github.io

Example: ```bash sudo vim ```

If vim can be executed with sudo, it may allow spawning a shell.

---

## SUID Binaries

SUID (Set User ID) binaries run with the privileges of their owner.

If a vulnerable SUID binary exists, it may allow privilege escalation.

Find SUID files: ```bash find / -perm -4000 2>/dev/null ```

Examples of exploitable binaries:

- find

- vim

- less

- nano

- python

---

## Writable Files and Directories

Improper file permissions may allow attackers to modify important files.

Find writable directories: ```bash find / -writable -type d 2>/dev/null ```

Check for:

- writable scripts executed by root

- writable system configuration files

- writable service binaries

---

## Cron Jobs

Cron jobs run scheduled tasks on Linux systems.

Misconfigured cron jobs may allow privilege escalation if the executed scripts are writable.

Check cron configuration: ```bash cat /etc/crontab / ls -la /etc/cron* ```

Look for:

- scripts executed as root

- writable cron scripts

---

## PATH Abuse

If a program executed by root uses relative paths, it may be possible to manipulate the PATH variable.

Example: ```bash echo $PATH ```

If a writable directory appears early in PATH, an attacker may place a malicious binary there.

---

## Kernel Exploits

Outdated kernels may contain privilege escalation vulnerabilities.

Check kernel version: ```bash uname -a ```

Search for known exploits: ```bash searchsploit linux kernel <version> ```

Useful resources:

- Exploit-DB

- CVE databases

---

## Automated Enumeration Tools

Several tools automate privilege escalation checks.

Examples:

- LinPEAS

- LinEnum

- Linux Smart Enumeration

Example: ``` ./linpeas.sh ```

These tools help identify misconfigurations and potential escalation vectors.

---

## Useful Files to Inspect

Some files may contain sensitive information.

Examples: 
```
/etc/passwd
/etc/shadow
/etc/sudoers
/home/*/.ssh
/root
```

---

## Notes

Privilege escalation techniques depend heavily on system configuration.

Not every system will contain exploitable misconfigurations.

Always perform these techniques only in authorized environments, such as labs, CTF challenges or permitted security assessments.