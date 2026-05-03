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

**Tools Selection**

| Tool | Purpose |
|------|---------|
| Nmap | Port scanning + service detection |
| Nikto | Web vulnerability scanning |
| Curl | HTTP request inspection |
| View Page Source | HTML comment/flag discovery |
| xfreerdp3 | CLI RDP client |
| Remmina | GUI RDP client |

