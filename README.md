## SK Telecom BPFDoor APT Breach — Security Case Study

This repository contains a security research case study analyzing the
four-year undetected APT attack against SK Telecom, Korea’s largest mobile carrier.
The analysis focuses on how a stealthy Linux backdoor (BPFDoor) compromised
telecom core infrastructure and remained undetected for years.

### Scope
- Victim: SK Telecom (27M subscribers)
- Core system breached: Home Subscriber Server (HSS)
- Attack type: Advanced Persistent Threat (APT)
- Malware: BPFDoor (port-less Linux backdoor)

### Incident Overview
- Data leaked: ~9.8GB of IMSI, SIM authentication keys (Ki), phone numbers, emails, and subscriber profiles
- Impact: Enables SIM cloning, 2FA interception, and large-scale identity theft
- Timeline: Initial compromise around 2021, publicly disclosed in April 2025

### Technical Analysis
- HSS acts as the “crown jewel” of mobile networks, storing subscriber identity and authentication data
- Initial intrusion via VPN and exposed system vulnerabilities
- BPFDoor deployed as a stealth, port-less backdoor enabling long-term persistence and lateral movement
- Remote command-and-control without open listening ports, evading traditional network monitoring

#### Reconstructed 4-Step Attack Chain
1. Initial intrusion
2. Persistence establishment via BPFDoor
3. Privilege escalation and access to HSS servers
4. Data exfiltration (~9.7GB), eventually detected through abnormal outbound traffic

### Root Causes & Failures
- Early warning signs identified in 2022 were not acted on, allowing long-term attacker presence
- Legacy HSS architecture with weak access separation across core systems
- Critical systems operated with insufficient security monitoring and deferred patching
- Severely limited logging created a multi-year visibility gap

### Lessons Learned
- Treat telecom core systems (e.g., HSS) as crown jewels with strict segmentation and dedicated monitoring
- Enforce mandatory logging and least-privilege access, even in legacy environments
- Do not delay security patches on critical systems solely for operational stability
- Act decisively on early compromise indicators to prevent multi-year APT persistence

### AppSec Relevance
- Lack of access segmentation → single-node compromise 
  exposed entire HSS cluster
- 2-year logging gap → forensic investigation impossible
- Patch deferral on critical systems → unmonitored attack surface

### Background
This case study was presented as part of an Information Security Management
course at San Francisco State University.

### Files
- `SKT_Telecom_Breach_Case_Study.pdf`  
  Original presentation slides used for the security research case study

### Author
Harper (Eunhui) Cho  
Information Security Engineering
