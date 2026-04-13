# SOC Home Lab — Detection Engineering & Blue Team Practice

## Overview
A fully operational SOC home lab built to simulate real-world attacker 
behaviour, validate detections, and develop analyst workflows. All 
simulations are mapped to MITRE ATT&CK techniques with documented 
evidence and structured incident reports.

## Lab Architecture

| Component | Details |
|---|---|
| SIEM | Wazuh 4.13.1 running on Ubuntu 24.04 Server |
| Endpoint | Windows 10 with Sysmon (SwiftOnSecurity config, hardened) |
| Monitoring | File Integrity Monitoring (FIM) across Desktop, Downloads, AppData, ProgramData |
| Virtualisation | VMware Workstation  Pro 25H2u1 |
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

```.
.
├── lab-setup/
│   ├── wazuh-manager/
│   ├── wazuh-agent/
│   └── sysmon-config/
│
├── case-studies/
│   └── 01-powershell-execution/
│       ├── images/
│       │   ├── sysmon-event-id-1.png
│       │   └── wazuh-encoded-command-alert.png
│       └── README.md
│
└── README.md
```

## Connect With Me

If you'd like to follow my cybersecurity journey or get in touch, you can find me on LinkedIn:

🔗 **www.linkedin.com/in/hamed-salami**

