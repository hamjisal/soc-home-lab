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

- **Detection rule:** Powershell.exe spawned a powershell process which executed a base64 encoded command  
- **Wazuh alert level:** 12  
- **Triggered rule ID:** 92057  
- **Additional related alerts:**  
  - Executable file dropped in folder commonly used by malware (Level 15, Rule ID 92213)  
  - Discovery activity via `net.exe` (Level 3, Rule ID 92039)  
  - Suspicious file creation in Windows root folder (Level 9, Rule ID 92205)


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

Wazuh successfully detected the simulated encoded PowerShell activity on the Win10-Lab endpoint. The key alert was:

- **Rule description:** Powershell.exe spawned a powershell process which executed a base64 encoded command  
- **Rule level:** 12  
- **Rule ID:** 92057  

In addition to that, Wazuh also raised related alerts for an executable file dropped in a folder commonly used by malware (Level 15, Rule ID 92213) and discovery activity such as `net.exe` account enumeration. Together, these events show that the Sysmon → Wazuh pipeline is working as intended and that this lab can reliably detect suspicious PowerShell execution and early-stage attacker behaviour.


## Screenshots
## Sysmon Event ID 1 – Process Creation

![Sysmon Event](images/sysmon-event-id-1.png)

## Wazuh Detection – Encoded PowerShell Command

![Wazuh Alert](images/wazuh-encoded-command-alert.png)



