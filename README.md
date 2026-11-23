# Nmap-Based Network Assessment

A network security assessment project using Nmap and Metasploit to identify exposed services, analyze network configurations, and validate a known vulnerability in an isolated virtual lab environment.

## Project Overview

This project demonstrates a practical network assessment workflow using Kali Linux and Metasploitable2. It focuses on host discovery, port scanning, service and version detection, SMB enumeration, and controlled vulnerability validation.

## Objectives

- Identify and verify the target system.
- Discover open and filtered network ports.
- Detect running services and their versions.
- Perform SMB enumeration and selected script checks.
- Investigate the vsftpd 2.3.4 FTP vulnerability.
- Validate the finding in an isolated lab environment.
- Document results, limitations, and security recommendations.

## Tools & Technologies

| Tool | Purpose |
|---|---|
| Kali Linux | Assessment workstation |
| Nmap | Host discovery and port scanning |
| Metasploit Framework | Vulnerability validation |
| VMware | Virtual lab environment |
| Metasploitable2 | Intentionally vulnerable target |

## Lab Environment

| Component | IP Address |
|---|---|
| Kali Linux | 192.168.2.129 |
| Metasploitable2 | 192.168.2.128 |
| Network | Host-only |

All practical testing was conducted within an isolated virtual lab.

## Methodology

### 1. Network Discovery
Identified the target machine and confirmed connectivity between the virtual machines.

### 2. Port Scanning & Service Detection
Used Nmap service/version detection:

```bash
sudo nmap -sV 192.168.2.128
```

The recorded scan identified 23 open TCP ports and 71 filtered TCP ports in the scanned default port set.

### 3. Service Enumeration

Key observed services included:

- FTP – vsftpd 2.3.4
- SSH – OpenSSH 4.7p1
- SMB – Samba 3.0.20-Debian
- HTTP – Apache 2.2.8
- Tomcat – 5.5

Additional services were recorded in the project report.

### 4. Vulnerability Validation

Investigated the FTP service using the Metasploit module:

`exploit/unix/ftp/vsftpd_234_backdoor`

The module check reported that the target appeared vulnerable. The controlled lab execution opened a Meterpreter session.

### 5. Session Verification

The following checks were documented:

- `getuid` – Reported root as the session user.
- `sysinfo` – Reported Ubuntu 8.04 on i686 architecture.

## Key Findings

- The FTP service was successfully validated as vulnerable in the lab.
- Anonymous FTP access was observed.
- SMB shares and users were enumerated.
- Legacy Apache and Tomcat services were identified.
- Two selected SMB vulnerability script checks returned false, while another returned an error.

**Important:** The broader vulnerability scan timed out. Therefore, the project does not claim a complete vulnerability assessment or that all identified services were exploitable.

## Security Recommendations

- Remove or upgrade obsolete services.
- Disable anonymous FTP access where unnecessary.
- Replace traditional FTP with secure file transfer.
- Restrict SMB access and review share permissions.
- Apply network segmentation and firewall restrictions.
- Monitor authentication and service logs.
- Conduct authorized retesting after remediation.

## Project Report

For complete methodology, screenshots, practical evidence, results, and analysis:

[View Final Project Report (PDF)](Final_Report_Nmap.pdf)

## Conclusion

This project demonstrates how Nmap and Metasploit can be used together for network discovery, service identification, and controlled vulnerability validation.

It also highlights the importance of interpreting scan results carefully, documenting limitations, and following security best practices.

## Author

**Rajvir Singh**

**Student ID:** 24BET10080

**Project:** Nmap-Based Network Assessment
