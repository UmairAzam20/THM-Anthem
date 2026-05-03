# THM-Anthem

## 1. SCOPE & TARGET DEFINITION 

**Scope Statement**

This vulnerability assessment is conducted within a controlled TryHackMe lab environment against the target machine "Anthem" (Windows-based). The assessment includes full port scanning, service enumeration, web application analysis, credential discovery, RDP exploitation, and privilege escalation. No destructive actions or lateral movement beyond the target is permitted.

**Target Description**

| Field | Value |
|-------|-------|
| Name | Anthem |
| Platform | TryHackMe (THM) |
| OS | Windows |
| IP Address | `10.49.160.141` |
| Difficulty | Easy |

**Justification:**

Windows target with realistic CMS (Umbraco) and RDP misconfigurations – common in enterprise environments.

**Simple Network Diagram**

```bash

[Kali Attack Machine]
    IP: (THM VPN assigned)
           |
           | Port 80 (HTTP)
           | Port 3389 (RDP)
           |
    [Anthem Target]
    IP: 10.49.160.141
           |
           |_ Web: Umbraco CMS (port 80)
           |_ Remote Desktop (port 3389)

```

## Methodology & Tool Mapping

| Phase | Tools Used | Key Findings |
|-------|-----------|--------------|
| **1. Port Scanning** | Nmap | Ports 80 (HTTP), 3389 (RDP) |
| **2. Directory Brute-force** | Gobuster | `/archive`, `/authors`, `/umbraco`, `/install` |
| **3. Web Vuln Scanning** | Nikto, Curl | `/robots.txt` with password |
| **4. Source Code Review** | Browser (Ctrl+U) | Flags 1-4, email pattern JD@anthem.com |
| **5. RDP Exploitation** | xfreerdp3, Remmina | User flag as `SG` |
| **6. Privilege Escalation** | Windows Explorer (hidden files) | Admin password in `C:\backup\restore.txt` |
