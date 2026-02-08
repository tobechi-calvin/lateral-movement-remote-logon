# SOC Incident Report: Attempted Lateral Movement (Blocked)

## Case Overview
- **Case ID:** ra639058096351022135_-847381402  
- **Incident Title:** Attempted Lateral Movement Using Remote Logon (Contained)  
- **Date:** February 4, 2026  
- **Severity:** Medium  
- **Status:** Closed – Contained  
- **Affected Host:** MTS-ContractorPC1  

---

## Executive Summary
On February 4, 2026, Microsoft Defender for Endpoint detected and blocked multiple remote authentication attempts targeting the **Administrator account** on a Windows endpoint.

The activity originated from external IP addresses and displayed patterns consistent with:

- Credential stuffing
- Password spraying
- Attempted lateral movement

Endpoint security controls successfully blocked the attempts, preventing account compromise or lateral spread.

---

## Incident Scope
| Category | Details |
|---------|--------|
| Affected Device | MTS-ContractorPC1 |
| Targeted Account | Administrator |
| Source IPs | 109.205.211.14, 185.214.96.27 |
| Protocol | NTLM |
| Network Type | External |

---

## Timeline (UTC)

| Time | Event |
|------|------|
| 13:31–13:40 | Multiple NTLM authentication attempts blocked |
| 13:37 | Silent deletion of OneDriveSetup.exe via cmd.exe |
| 13:40–16:24 | ContainedUserLogonBlocked events recorded |
| Post-activity | No successful logon or lateral movement observed |

---

## Technical Analysis

### Authentication Findings
- Repeated NTLM logon attempts against privileged account.
- Activity originated from external IP addresses.
- Defender blocked access before session establishment.

### Process Activity
Suspicious processes observed:
- `cmd.exe` – used for silent file deletion.
- `rundll32.exe` – mostly normal Windows activity.

### File System Activity
- Silent deletion of:

- - Located in user AppData directory.
- Likely artifact cleanup behavior.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1021 | Remote Services (Attempted) |
| T1110 | Brute Force / Password Spraying |
| T1078 | Valid Accounts (Attempted) |
| T1070.004 | Indicator Removal on Host |

---

## Impact Assessment
- No successful authentication.
- No lateral movement.
- No persistence detected.
- Attack contained at initial access phase.

---

## Response Actions
- Remote logon attempts blocked by endpoint controls.
- Malicious IP addresses flagged.
- Administrator account activity reviewed.
- Threat hunting conducted for lateral movement indicators.

---

## Security Recommendations
1. Enforce MFA for privileged accounts.
2. Restrict NTLM authentication.
3. Limit local administrator usage.
4. Monitor for repeat activity.
5. Audit AppData and OneDrive modifications.

---

## Tools Used
- Microsoft Defender for Endpoint
- KQL (Microsoft Sentinel)
- Windows Event Logs

---

## Skills Demonstrated
- Incident triage
- Log analysis
- Threat hunting
- MITRE ATT&CK mapping
- Endpoint investigation
- Report writing


