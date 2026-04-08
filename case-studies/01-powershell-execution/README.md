# Case Study 01 — Suspicious PowerShell Execution (T1059.001)

## Scenario
PowerShell is one of the most abused tools in modern attacks. Adversaries use it
for download cradles, encoded execution, and living-off-the-land techniques.
This simulation tests whether Wazuh and Sysmon can detect suspicious PowerShell
activity that mimics real attacker behaviour.

## Environment
- Wazuh SIEM on Ubuntu 24.04
- Windows 10 endpoint with Sysmon (SwiftOnSecurity config)
- Detection rule: [Add rule ID or name once known]

## Attack Simulation
The following command was executed to simulate malicious PowerShell behaviour:

powershell.exe -ExecutionPolicy Bypass -EncodedCommand <base64-string>

### Why this matters
- ExecutionPolicy Bypass ignores security restrictions  
- EncodedCommand hides the real payload  
- Attackers use this pattern for initial access, persistence, and C2 activity  

## Detection
- Sysmon Event ID: 1 (Process Creation)
- Wazuh alert level: [e.g., Level 10]
- Triggered rule: [rule name/ID]
- Screenshot: (add screenshot here)

## Investigation Walkthrough
1. Identify the parent process (e.g., explorer.exe, cmd.exe)
2. Decode the Base64 command to see the real payload
3. Check for network connections (Sysmon Event ID 3)
4. Check for file writes (Sysmon Event ID 11)
5. Decide whether to escalate or close

## MITRE ATT&CK Mapping
- Tactic: Execution
- Technique: T1059.001 — PowerShell
- Relevance: Common in initial access, lateral movement, and C2 communication

## Outcome
Summarise:
- What the detection caught
- What it missed
- Any tuning or improvements you made

## Screenshots
(Add your Wazuh alert screenshot here)
(Add your Sysmon event screenshot here)


