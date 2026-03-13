# Windows Privilege Escalation

Privilege escalation in Windows occurs when a user gains higher privileges on a system.

In many cases, the goal is to obtain **Administrator** or **SYSTEM** privileges after gaining initial access.

Privilege escalation typically involves identifying misconfigurations, weak permissions or vulnerable services.

---

# Initial Enumeration

The first step is gathering information about the system.

Useful commands:

```powershell
whoami
whoami /priv
whoami /groups
systeminfo 
```

These commands reveal:

- current user privileges

- group memberships

- system version

- potential privilege escalation vectors

---

## Checking Installed Programs

Installed applications may contain vulnerable software.

```powershell wmic product get name,version ```

Look for outdated or vulnerable software.

---

## User and Group Enumeration

Check users and groups on the system.

```powershell
net user
net localgroup
net localgroup administrators
```
This helps identify privileged accounts or misconfigured group memberships.

---

## Service Misconfigurations

Misconfigured Windows services may allow privilege escalation.

List services: ```powershell sc query ```

Check service configuration: ```powershell sc qc <service_name> ```

Look for:

- services running as SYSTEM

- writable service binaries

- writable service directories

If the binary path is writable, it may be possible to replace it with a malicious executable.

---

## Unquoted Service Paths

Some Windows services use unquoted paths.

Example: ``` C:\Program Files\Some Service\service.exe ```

Windows may interpret this path incorrectly if spaces exist, allowing an attacker to place a malicious executable in a higher directory.

Search for unquoted services: ```powershell wmic service get name,displayname,pathname,startmode ```

Look for services where the path contains spaces but is not wrapped in quotes.

---

## Weak File Permissions

Improper file permissions may allow users to modify important binaries.

Check file permissions: ```powershell icacls "C:\path\to\file" ```

Look for write access for low-privileged users.

---

## Scheduled Tasks

Scheduled tasks may run with elevated privileges.

List scheduled tasks: ```powershell schtasks /query /fo LIST /v ```

Look for:

- tasks running as SYSTEM

- writable scripts or executables

---

## Credential Discovery

Sometimes credentials are stored in configuration files or system memory.

Common places to check:

```
C:\Users\
C:\ProgramData\
C:\Windows\Panther\
C:\Windows\System32\config\
```

Tools commonly used:

- Mimikatz

- LaZagne

---

## Token Privileges

Certain privileges may allow privilege escalation.

Example: ```powershell whoami /priv ```

Look for privileges such as:

- SeImpersonatePrivilege

- SeAssignPrimaryTokenPrivilege

These may allow attacks like Potato attacks.

---

## Automated Enumeration Tools

Several tools automate Windows privilege escalation checks.

Examples:

- WinPEAS

- PowerUp

- Seatbelt

Example: ```powershell .\winPEAS.exe ```

These tools help identify common misconfigurations and vulnerabilities.

---

## Useful Files and Locations

Some files may contain sensitive information.

Examples:

```
C:\Windows\System32\config\SAM
C:\Windows\NTDS\NTDS.dit
C:\Users\<user>\AppData\
```

These files may contain credential data or useful configuration details.

---

## Notes

Privilege escalation techniques depend heavily on system configuration.

Not all systems will contain exploitable misconfigurations.

Always perform these techniques in authorized environments, such as labs, CTFs or permitted security assessments.