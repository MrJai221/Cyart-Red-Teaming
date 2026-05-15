# Incident Response Report: VSFTPD Backdoor Exploitation

## 1. Executive Summary
A critical vulnerability in the VSFTPD 2.3.4 service was exploited, allowing unauthorized root access to the server. The attack was detected via Wazuh and contained using CrowdSec/Iptables.

## 2. Timeline
- **10:00 AM**: Nmap scan detects VSFTPD 2.3.4 on Port 21.
- **10:15 AM**: Metasploit `vsftpd_234_backdoor` module launched.
- **10:17 AM**: Root shell established on Port 6200 (T1190).
- **10:20 AM**: Alert triggered in Wazuh SIEM.
- **10:25 AM**: Attacker IP blocked; service isolated.

## 3. Technical Findings
| Alert | Tactic | Technique |
| :--- | :--- | :--- |
| VSFTPD Exploit | Initial Access | T1190 (Exploit Public-Facing App) |
| Port 6200 Bind | Command & Control | T1071 (Application Layer Protocol) |

## 4. Remediation
1. **Patch**: Upgrade VSFTPD to a secure version.
2. **Hardening**: Implement a firewall rule to block all traffic on Port 6200.
3. **Recovery**: Rebuild the system from a clean image to ensure no persistence.
