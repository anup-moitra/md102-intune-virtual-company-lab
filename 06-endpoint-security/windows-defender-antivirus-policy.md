# Microsoft Defender Antivirus Policy with Intune

This file documents the Microsoft Defender Antivirus endpoint security policy lab for the MD-102 Intune virtual company project.

## Objective

Create and test a Microsoft Defender Antivirus policy using Microsoft Intune Endpoint security.

## Lab Environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Operating system | Windows 11 |
| Management | Microsoft Intune |
| Test user | user01 |
| Assignment group | GRP-Pilot-Users |
| Policy area | Endpoint security |
| Policy type | Antivirus |
| Profile | Microsoft Defender Antivirus |

## Policy Details

| Setting | Value |
|---|---|
| Policy name | WIN-CORP-Defender-Antivirus-Policy |
| Platform | Windows |
| Profile | Microsoft Defender Antivirus |
| Assignment | GRP-Pilot-Users |
| Test device | WIN-CORP-001 |
| Policy result | Succeeded |

## Defender Antivirus Settings Configured

| Defender Setting | Configuration |
|---|---|
| Allow Archive Scanning | Allowed |
| Allow Behavior Monitoring | Allowed |
| Allow Cloud Protection | Allowed |
| Allow Realtime Monitoring | Allowed |
| Allow Script Scanning | Allowed |
| Check For Signatures Before Running Scan | Enabled |
| PUA Protection | Block detected items |

## What This Proves

This lab proves that Microsoft Intune can manage Microsoft Defender Antivirus settings using Endpoint security policies.

```text
Admin created Defender Antivirus policy in Intune
→ Policy assigned to GRP-Pilot-Users
→ WIN-CORP-001 synced with Intune
→ Defender Antivirus settings applied
→ Intune showed policy status as Succeeded
```

## Screenshots

Suggested folder:

```text
screenshots/sanitized/endpoint-security/
```

Suggested screenshots:

```text
defender-antivirus-policy-list-sanitized.jpg
defender-antivirus-policy-settings-sanitized.jpg
defender-antivirus-policy-assignment-sanitized.jpg
defender-antivirus-device-status-succeeded-sanitized.jpg
win-corp-001-windows-security-defender-sanitized.jpg
```

## Current Lab Status

Completed:

- Defender Antivirus endpoint security policy created
- Microsoft Defender Antivirus profile selected
- Core Defender Antivirus settings configured
- Policy assigned to GRP-Pilot-Users
- WIN-CORP-001 synced with Intune
- Policy status showed Succeeded

Pending:

- Add screenshots as available
- Create Windows Firewall endpoint security policy lab
- Test BitLocker or disk encryption later
- Test Attack Surface Reduction later
- Test security baseline later
