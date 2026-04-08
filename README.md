# SOC Home Lab — Detection Engineering & Blue Team Practice

## Overview
A fully operational SOC home lab built to simulate real-world attacker 
behaviour, validate detections, and develop analyst workflows. All 
simulations are mapped to MITRE ATT&CK techniques with documented 
evidence and structured incident reports.

## Lab Architecture

| Component | Details |
|---|---|
| SIEM | Wazuh 4.x running on Ubuntu 22.04 Server |
| Endpoint | Windows 10 with Sysmon (SwiftOnSecurity config, hardened) |
| Monitoring | File Integrity Monitoring (FIM) across Desktop, Downloads, AppData, ProgramData |
| Virtualisation | VMware Workstation |
| Framework | MITRE ATT&CK for detection mapping |

## What This Lab Can Detect

- Suspicious PowerShell and CMD execution
- Registry Run key persistence
- LOLBin usage (certutil, mshta, wmic)
- Scheduled task creation
- File drops in monitored paths
- New service installation
- Hosts file modification
- Execution of unsigned binaries from Temp

## Case Studies

| # | Technique | MITRE ID | Status |
|---|---|---|---|
| 1 | Suspicious PowerShell Execution | T1059.001 | ✅ Documented |
| 2 | Registry Run Key Persistence | T1547.001 | ✅ Documented |
| 3 | LOLBin Execution via certutil.exe | T1105 | ✅ Documented |

## Repository Structure
