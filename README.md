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

## 2. METHODOLOGY, SCANNING & ANALYSIS 

**Step 1: Initial Port Scanning (Nmap)**

```bash

nmap -sC -sV -Pn 10.49.160.141
```

* Result scanning

![Nmap Scan Results](screenshots/nmapscancrop.png)


| Port | State | Service | Version | Potential Risk | Severity |
|:----:|:-----:|---------|---------|----------------|:--------:|
| 80 | Open | HTTP | IIS / Umbraco CMS | Web attack surface; admin panel exposure; potential RCE | High |
| 3389 | Open | RDP | Microsoft Terminal Services | Brute-force attacks; credential reuse; BlueKeep (CVE-2019-0708) | Critical |
