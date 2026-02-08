
Paste:

```markdown
# Attempted Lateral Movement Using Remote Logon (Contained)

## Case Information
- Case ID: ra639058096351022135_-847381402
- Date Opened: February 4, 2026
- Severity: Medium
- Status: Closed – Contained
- Affected Host: MTS-ContractorPC1

---

## Executive Summary
Microsoft Defender detected and blocked multiple remote authentication attempts targeting the Administrator account.

The activity originated from external IP addresses:
- 109.205.211.14
- 185.214.96.27

Behavior matched credential stuffing and attempted lateral movement.

Security controls blocked the activity before compromise.

---

## Timeline (UTC)

| Time | Event |
|------|------|
| 13:31–13:40 | Multiple NTLM authentication attempts blocked |
| 13:37 | Silent deletion of OneDriveSetup.exe via cmd.exe |
| 13:40–16:24 | ContainedUserLogonBlocked events recorded |
| Post activity | No successful logon detected |

---

## Technical Analysis

### Authentication
- Repeated NTLM authentication attempts
- Targeted privileged account
- Activity blocked before session creation

### Process Activity
Observed processes:
- cmd.exe
- rundll32.exe

cmd.exe was used to silently delete files in AppData.

---

## MITRE ATT&CK Mapping

| Technique | Description |
|----------|-------------|
| T1021 | Remote Services |
| T1110 | Brute Force |
| T1078 | Valid Accounts |
| T1070.004 | Indicator Removal |

---

## Impact
- No successful authentication
- No lateral movement
- No persistence mechanisms
- Attempt contained

---

## Response Actions
- Blocked IP addresses
- Reviewed administrator activity
- Executed threat hunting queries

---

## Recommendations
- Enforce MFA
- Restrict NTLM authentication
- Limit administrator account usage
- Monitor AppData changes
