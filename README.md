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
| Autopilot device import and profile assignment | Completed |
| Microsoft 365 Apps deployment for Autopilot lab | Created / In progress |
| Autopilot OOBE enrollment verification | In progress |
| Microsoft 365 Apps install and sign-in verification | In progress |
| BYOD enrollment labs | Planned |
| Additional endpoint security labs | Planned |
| Remote actions and monitoring | Planned |
| Troubleshooting labs | Planned |
| Sanitized screenshots | In progress / added as available |

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

Main files:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
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

## Current In-Progress Labs

### Windows Autopilot User-Driven Enrollment

Completed so far:

- Autopilot device group created
- Autopilot deployment profile created
- Hardware hash collected/imported
- Autopilot device added to group
- Autopilot profile assigned successfully

Pending verification:

- Complete OOBE sign-in as User 01
- Confirm device appears under Windows devices in Intune
- Confirm Microsoft Entra joined status
- Confirm Intune managed status
- Confirm primary user and compliance state

Main file:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

### Microsoft 365 Apps Deployment for Autopilot

Completed so far:

- Microsoft 365 Business Premium trial activated
- User 01 licensed for Microsoft 365 Apps
- Microsoft 365 Apps deployment created in Intune
- Outlook, Excel, and PowerPoint selected
- App assigned as Required to GRP-Pilot-Users

Pending verification:

- Confirm app install status
- Open Outlook, Excel, and PowerPoint
- Confirm sign-in/activation as User 01

Main file:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

## Planned / Upcoming Labs

Next planned work:

1. Complete Autopilot OOBE sign-in with `user01`.
2. Confirm the Autopilot device appears in Intune.
3. Confirm Microsoft Entra join and Intune enrollment.
4. Confirm Microsoft 365 Apps install status.
5. Test Outlook, Excel, and PowerPoint sign-in.
6. Update Autopilot and Microsoft 365 Apps docs from `In progress` to `Completed`.
7. Continue with Windows BYOD enrollment.
8. Continue with Android/iOS BYOD enrollment.
9. Continue with Firewall, BitLocker, ASR, and remote actions labs.

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

## Current Focus

The current focus is:

```text
Complete Autopilot enrollment verification and Microsoft 365 Apps deployment/sign-in testing.
```

After this is complete, update these files:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
00-project-overview/lab-implementation-roadmap.md
README.md
```

## Disclaimer

This is a public learning repository.

All company names, users, groups, devices, screenshots, and lab details are fictional, test-only, or sanitized.

No real production data, tenant secrets, credentials, device serial numbers, BitLocker recovery keys, Autopilot hardware hashes, or confidential information should be published.
