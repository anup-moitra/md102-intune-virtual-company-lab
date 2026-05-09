# MD-102 Intune Virtual Company Lab

Hands-on MD-102 lab project simulating a small virtual company using Microsoft Intune, Microsoft Entra ID, Windows devices, BYOD scenarios, Windows Autopilot, configuration profiles, compliance policies, Conditional Access, application deployment, endpoint security, remote actions, monitoring, and troubleshooting.

## Project Overview

This repository documents my hands-on learning journey for **MD-102: Endpoint Administrator**.

The goal of this project is to build a practical virtual company environment and apply modern endpoint management concepts step by step.

This project demonstrates real-world Microsoft Intune administration skills, including:

- Microsoft Entra ID users and groups
- Intune license assignment
- Windows device enrollment
- Windows Autopilot provisioning
- Configuration profiles
- Compliance policies
- Conditional Access requiring compliant devices
- Corporate and BYOD access testing
- Microsoft Store app deployment
- Win32 app deployment
- Microsoft 365 Apps deployment
- Endpoint security policies
- Remote actions, monitoring, and troubleshooting

## Virtual Company Scenario

This lab simulates a small company named:

```text
Contoso Startup Lab
```

The virtual company includes:

- Corporate Windows laptops
- Personal/BYOD Windows laptops
- Planned Android BYOD devices
- Planned iOS BYOD devices
- Microsoft Entra ID users and security groups
- Microsoft Intune device management
- Microsoft 365 Apps licensing and deployment
- Endpoint security and compliance controls

## Current Lab Status

The project has moved from planning into active hands-on implementation.

| Area | Status |
|---|---|
| GitHub repository and project structure | Completed |
| Microsoft Intune tenant / trial verification | Completed |
| Microsoft Entra ID users and groups | Completed |
| Intune license assignment | Completed |
| Microsoft 365 Business Premium trial/license assignment | Completed |
| Automatic MDM enrollment configuration | Completed |
| Corporate Windows OOBE enrollment | Completed |
| WIN-CORP-001 Intune enrollment | Completed |
| Windows compliance policy | Completed |
| Conditional Access requiring compliant device | Completed |
| Compliant corporate device Report-only test | Completed |
| Unmanaged BYOD Report-only failure test | Completed |
| Basic Windows configuration profile | Completed |
| Corporate wallpaper configuration profile | Completed |
| Microsoft Store app deployment | Completed |
| Win32 app deployment with 7-Zip | Completed |
| Defender Antivirus endpoint security policy | Completed |
| Windows Autopilot deployment profile | Completed |
| Autopilot hardware hash import and profile assignment | Completed |
| Autopilot user-driven OOBE enrollment verification | Completed |
| Microsoft 365 Apps deployment for Autopilot lab | Completed |
| Microsoft 365 Apps install verification | Completed |
| Word sign-in verification with User 01 | Completed |
| Excel and PowerPoint installation as selected Microsoft 365 Apps | Completed |
| BYOD enrollment labs | Planned |
| Additional endpoint security labs | Planned |
| Remote actions and monitoring | Planned |
| Troubleshooting labs | Planned |
| Sanitized screenshots | Added as available |

## Completed Hands-on Labs

### Identity and Group Preparation

Completed:

- Microsoft Entra ID lab users created
- Lab admin user created
- Standard test users created
- Security groups created
- Pilot user group created
- Windows user group created
- BYOD/mobile user groups created
- Intune licenses assigned to lab users
- Microsoft 365 Business Premium license assigned to User 01 for Office app testing

Main file:

```text
01-identity-and-groups/users-and-groups.md
```

### Corporate Windows Enrollment

Completed:

- Corporate Windows 11 device enrolled through Windows OOBE
- Device joined to Microsoft Entra ID
- Device enrolled into Microsoft Intune
- Device marked as corporate-owned
- Primary user confirmed as `user01`
- Device reported compliant

Test device:

```text
WIN-CORP-001
```

Main file:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

### Windows Autopilot User-Driven Enrollment

Completed:

- Autopilot device group created
- Autopilot deployment profile created
- Hardware hash collected from OOBE device
- Autopilot hardware hash CSV imported into Intune
- Autopilot device added to the Autopilot device group
- Autopilot profile status changed from Not assigned to Assigned
- OOBE sign-in completed with User 01
- Device connected to Microsoft Entra ID
- Device appeared in Intune Windows devices
- Device ownership displayed as corporate
- Device compliance displayed as compliant
- Sanitized screenshots added

Main file:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

### Windows Compliance Policy

Completed:

- Basic Windows compliance policy created
- Policy assigned and tested
- WIN-CORP-001 reported compliant
- Compliance result used later by Conditional Access

Main file:

```text
04-compliance-and-conditional-access/windows-basic-compliance-policy.md
```

### Conditional Access Requiring Compliant Devices

Completed:

- Conditional Access policy created in Report-only mode
- Policy required device to be marked as compliant
- Office 365 selected as target resource
- Compliant corporate device test completed
- Unmanaged BYOD browser sign-in test completed

Policy name:

```text
CA001 - Require compliant device for pilot users
```

Result summary:

| Scenario | Device | Managed | Compliant | Report-only result |
|---|---|---|---|---|
| Corporate compliant device | WIN-CORP-001 | Yes | Yes | Success |
| Unmanaged BYOD device | WIN-BYOD-001 | No | No | Failure |

Main file:

```text
04-compliance-and-conditional-access/conditional-access-compliant-device.md
```

### Basic Windows Configuration Profile

Completed:

- Settings catalog profile created
- Microsoft Edge startup behavior configured
- Profile assigned to pilot users
- WIN-CORP-001 synced with Intune
- Microsoft Edge opened the configured startup site successfully

Profile name:

```text
WIN-CORP-Basic-Configuration-Profile
```

Configured startup URL:

```text
https://anupmoitra.com/
```

Main file:

```text
03-configuration-profiles/windows-basic-configuration-profile.md
```

### Corporate Wallpaper Configuration Profile

Completed:

- Wallpaper image prepared in GitHub assets folder
- PowerShell platform script used to download wallpaper to device
- Settings catalog policy used to configure desktop wallpaper
- Wallpaper applied after sync/restart

Main file:

```text
03-configuration-profiles/windows-corporate-wallpaper-policy.md
```

### Application Deployment

Completed:

- Microsoft Store app deployment tested
- Company Portal deployed as Required
- Spotify deployed as Required
- VLC deployed as Required
- ChatGPT deployed as Available in Company Portal
- 7-Zip packaged and deployed as a Win32 app
- Microsoft 365 Apps deployed for the Autopilot lab
- Word, Excel, and PowerPoint selected in the Microsoft 365 Apps deployment
- Microsoft 365 Apps install verified in Intune
- Microsoft 365 Apps install verified in Company Portal
- Word sign-in verified with User 01

Main files:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

### Endpoint Security

Completed:

- Microsoft Defender Antivirus endpoint security policy created
- Core Defender Antivirus settings configured
- Policy assigned to pilot users
- WIN-CORP-001 reported policy status as Succeeded

Main file:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

## Current Focus

The current focus is to continue with the next endpoint security or management lab.

Recommended next labs:

```text
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
```

## Planned / Upcoming Labs

Next planned work:

1. Continue with Windows Firewall endpoint security policy.
2. Continue with BitLocker encryption policy.
3. Continue with Attack Surface Reduction policy.
4. Continue with Windows Security Baseline.
5. Continue with Windows BYOD enrollment.
6. Continue with Android/iOS BYOD enrollment.
7. Continue with remote actions and monitoring.
8. Continue with troubleshooting labs.

Future planned labs:

- Windows BYOD enrollment
- Android BYOD enrollment
- iOS BYOD enrollment
- Managed but noncompliant device test
- Conditional Access enforced mode test
- Windows Firewall endpoint security policy
- BitLocker disk encryption policy
- Attack Surface Reduction policy
- Windows Security Baseline
- Remote actions and monitoring
- Autopilot / motherboard replacement troubleshooting lab

## Repository Structure

```text
md102-intune-virtual-company-lab/
├── README.md
├── SAFE_UPLOAD_INSTRUCTIONS.md
├── 00-project-overview/
├── 01-identity-and-groups/
├── 02-device-enrollment/
├── 03-configuration-profiles/
├── 04-compliance-and-conditional-access/
├── 05-application-deployment/
├── 06-endpoint-security/
├── 07-remote-actions-and-monitoring/
├── 08-troubleshooting/
├── assets/
└── screenshots/
```

## Documentation Standards

Each lab file should include:

- Objective
- Lab context
- Important concepts
- Configuration details
- Steps performed
- Test result
- Screenshots
- Troubleshooting notes
- Security/privacy notes
- Current status
- Next step

## Screenshot and Privacy Standards

All screenshots must be sanitized before upload.

Do not publish:

- Real tenant IDs
- Full real email addresses
- Passwords
- MFA QR codes
- Device serial numbers
- Device IDs
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Production company data
- Unsanitized screenshots

Safe information to show:

- Fictional lab user names
- Sanitized device names
- Policy names
- App names
- Compliance result
- Conditional Access result
- Managed/compliant status after sensitive details are hidden

## Learning Purpose

This project is a personal learning and portfolio project for **MD-102: Endpoint Administrator**.

It demonstrates practical experience with:

- Microsoft Intune
- Microsoft Entra ID
- Windows device enrollment
- Windows Autopilot
- Configuration profiles
- Compliance policies
- Conditional Access
- Application deployment
- Microsoft 365 Apps deployment
- Endpoint security
- BYOD testing
- Remote actions
- Troubleshooting and documentation

## Recent Completed Milestone

The most recent completed milestone is:

```text
Windows Autopilot user-driven enrollment
+
Microsoft 365 Apps deployment validation
```

This proves the following workflow:

```text
Autopilot hardware hash imported
→ Autopilot profile assigned
→ User 01 signs in during OOBE
→ Device joins Microsoft Entra ID
→ Device enrolls into Intune
→ Microsoft 365 Apps install successfully
→ Word opens and signs in with User 01
```

## Disclaimer

This is a public learning repository.

All company names, users, groups, devices, screenshots, and lab details are fictional, test-only, or sanitized.

No real production data, tenant secrets, credentials, device serial numbers, BitLocker recovery keys, Autopilot hardware hashes, or confidential information should be published.
