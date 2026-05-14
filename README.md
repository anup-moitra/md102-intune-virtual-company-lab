# MD-102 Intune Virtual Company Lab

This repository documents a hands-on Microsoft Intune and MD-102 lab environment.

The project simulates a small company using Microsoft Entra ID, Microsoft Intune, Windows device enrollment, Windows Autopilot, BYOD enrollment, configuration profiles, application deployment, endpoint security, compliance policies, Conditional Access, remote actions, monitoring, and troubleshooting.

---

## Project goal

The goal of this project is to build practical Microsoft Intune administration experience and document each lab in a professional GitHub portfolio format.

This project demonstrates real-world endpoint administration skills, including:

- Microsoft Entra ID user and group management
- Intune device enrollment
- Windows Autopilot provisioning
- Windows BYOD enrollment
- Android Enterprise BYOD work profile enrollment
- iOS/iPadOS BYOD enrollment preparation
- Microsoft Store app deployment
- Win32 app deployment
- Microsoft 365 Apps deployment
- Android Managed Google Play app deployment
- Windows configuration profiles
- Corporate wallpaper deployment
- USB storage restriction policy
- Microsoft Defender Antivirus policy
- Windows Firewall policy
- BitLocker encryption policy
- Future Attack Surface Reduction and Security Baseline testing
- Future compliance, Conditional Access, remote actions, monitoring, and troubleshooting labs

---

## Virtual company scenario

The lab company is called **Contoso Startup Lab**.

Contoso Startup Lab represents a small organization with a mixed device environment.

The company includes:

- Corporate-owned Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD devices
- iOS/iPadOS BYOD devices
- Microsoft Entra ID users and groups
- Microsoft Intune device management
- Microsoft 365 Apps
- Configuration profiles
- Endpoint security policies
- Planned compliance and Conditional Access controls
- Planned remote actions and monitoring workflows

Detailed scenario documentation:

```text
00-project-overview/company-scenario.md
```

---

## Lab sections

| Section | Area |
|---|---|
| 00 | Project Overview |
| 01 | Identity and Groups |
| 02 | Device Enrollment |
| 03 | Configuration Profiles |
| 04 | Compliance and Conditional Access |
| 05 | Application Deployment |
| 06 | Endpoint Security |
| 07 | Remote Actions and Monitoring |
| 08 | Troubleshooting |

---

## Repository structure

```text
md102-intune-virtual-company-lab/
├── README.md
├── 00-project-overview/
│   ├── company-scenario.md
│   ├── device-inventory.md
│   └── lab-implementation-roadmap.md
├── 01-identity-and-groups/
│   └── users-and-groups.md
├── 02-device-enrollment/
│   ├── windows-oobe-enrollment.md
│   ├── windows-autopilot-user-driven-enrollment.md
│   ├── windows-byod-enrollment.md
│   ├── android-byod-enrollment.md
│   └── ios-byod-enrollment.md
├── 03-configuration-profiles/
│   ├── windows-basic-configuration-profile.md
│   ├── windows-corporate-wallpaper-policy.md
│   └── windows-device-restrictions-profile.md
├── 04-compliance-and-conditional-access/
│   ├── windows-basic-compliance-policy.md
│   ├── conditional-access-compliant-device.md
│   ├── managed-noncompliant-device-test.md
│   └── conditional-access-enforced-mode-test.md
├── 05-application-deployment/
│   ├── microsoft-store-app-deployment.md
│   ├── win32-app-deployment-7zip.md
│   ├── microsoft-365-apps-autopilot-deployment.md
│   ├── android-managed-google-play-app-deployment.md
│   └── company-portal-self-service-apps.md
├── 06-endpoint-security/
│   ├── windows-defender-antivirus-policy.md
│   ├── windows-firewall-policy.md
│   ├── bitlocker-encryption-policy.md
│   ├── attack-surface-reduction-policy.md
│   └── windows-security-baseline.md
├── 07-remote-actions-and-monitoring/
│   ├── device-sync-remote-actions.md
│   ├── restart-retire-wipe-actions.md
│   ├── collect-diagnostics.md
│   └── device-monitoring-and-reports.md
└── 08-troubleshooting/
    ├── intune-enrollment-troubleshooting.md
    ├── conditional-access-troubleshooting.md
    ├── office-app-signin-troubleshooting.md
    └── autopilot-motherboard-replacement-troubleshooting.md
```

> [!NOTE]
> Some files are planned future labs and will be completed as the hands-on project progresses.

---

## Current project status

| Task | Status |
|---|---|
| GitHub repository created | Completed |
| Initial README created | Completed |
| Project overview folder created | Completed |
| Company scenario documented | Completed |
| Device inventory documented | Completed |
| Lab roadmap documented | Completed |
| Identity and groups lab | Completed |
| Windows OOBE enrollment lab | Completed |
| Windows Autopilot user-driven enrollment lab | Completed |
| Windows BYOD enrollment lab | Completed |
| Android BYOD work profile enrollment lab | Completed |
| iOS BYOD enrollment lab | In Progress / Admin prerequisites completed |
| Windows basic configuration profile lab | Completed |
| Corporate wallpaper ADMX configuration profile lab | Completed |
| USB storage block device restrictions lab | Completed |
| Microsoft Store app deployment lab | Completed |
| Win32 7-Zip app deployment lab | Completed |
| Microsoft 365 Apps deployment lab | Completed |
| Android Managed Google Play app deployment lab | Completed |
| Defender Antivirus endpoint security lab | Completed |
| Windows Firewall endpoint security lab | Completed |
| BitLocker encryption endpoint security lab | Completed |
| Attack Surface Reduction policy lab | Next / Planned |
| Windows Security Baseline lab | Planned |
| Compliance and Conditional Access labs | Planned |
| Company Portal self-service app lab | Optional / Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting documentation | Planned |

---

## Completed labs

### 01 - Identity and Groups

Documented in:

```text
01-identity-and-groups/users-and-groups.md
```

Completed work:

- Created lab users
- Created Microsoft Entra ID security groups
- Configured group memberships
- Assigned license to user01
- Prepared pilot assignment group
- Prepared Autopilot device group
- Prepared BYOD user group
- Reused groups for enrollment, apps, configuration profiles, and endpoint security targeting

---

### 02 - Device Enrollment

Completed enrollment labs:

| Lab | File | Result |
|---|---|---|
| Windows OOBE enrollment | `02-device-enrollment/windows-oobe-enrollment.md` | WIN-CORP-001 enrolled and visible in Intune |
| Windows Autopilot user-driven enrollment | `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | WINAUTO452 enrolled as corporate-owned and compliant |
| Windows BYOD enrollment | `02-device-enrollment/windows-byod-enrollment.md` | WIN-BYOD-001 enrolled as personal, Intune managed, and compliant |
| Android BYOD enrollment | `02-device-enrollment/android-byod-enrollment.md` | ANDROID-BYOD-001 enrolled with Android Enterprise work profile |
| iOS BYOD enrollment | `02-device-enrollment/ios-byod-enrollment.md` | Admin prerequisites completed; physical iPhone/iPad enrollment pending |

---

### 03 - Configuration Profiles

Completed configuration profile labs:

| Lab | File | Result |
|---|---|---|
| Windows basic configuration profile | `03-configuration-profiles/windows-basic-configuration-profile.md` | Created and validated |
| Corporate wallpaper ADMX policy | `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Wallpaper staged and applied successfully |
| USB storage block policy | `03-configuration-profiles/windows-device-restrictions-profile.md` | USB/removable storage blocked successfully |

---

### 05 - Application Deployment

Completed application deployment labs:

| Lab | File | Result |
|---|---|---|
| Microsoft Store app deployment | `05-application-deployment/microsoft-store-app-deployment.md` | Required and available Store apps validated |
| Win32 7-Zip app deployment | `05-application-deployment/win32-app-deployment-7zip.md` | 7-Zip packaged as `.intunewin` and deployed |
| Microsoft 365 Apps deployment | `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Microsoft 365 Apps installed and validated after Autopilot |
| Android Managed Google Play app deployment | `05-application-deployment/android-managed-google-play-app-deployment.md` | Outlook and Teams installed in Android Work profile |

Microsoft Store required apps tested:

```text
Company Portal
VLC UWP
Slack
```

Microsoft Store available apps tested:

```text
ChatGPT
WhatsApp
```

Android Managed Google Play apps tested:

```text
Microsoft Outlook
Microsoft Teams
```

---

### 06 - Endpoint Security

Completed endpoint security labs:

| Lab | File | Result |
|---|---|---|
| Defender Antivirus policy | `06-endpoint-security/windows-defender-antivirus-policy.md` | Success on WINAUTO452 |
| Windows Firewall policy | `06-endpoint-security/windows-firewall-policy.md` | Success on WINAUTO452 |
| BitLocker encryption policy | `06-endpoint-security/bitlocker-encryption-policy.md` | Fully Encrypted / Protection On |

Planned endpoint security labs:

```text
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```

---

## Completed modern endpoint deployment flow

The completed labs now demonstrate this modern endpoint management chain:

```text
Microsoft Entra users and groups
-> Intune enrollment
-> Windows OOBE enrollment
-> Windows Autopilot registration and provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> Microsoft Store app deployment
-> Win32 app deployment
-> Microsoft 365 Apps deployment
-> Android Managed Google Play app deployment
-> Configuration profiles applied
-> Corporate wallpaper deployed
-> USB storage restriction validated
-> Defender Antivirus, Firewall, and BitLocker validated
```

---

## Skills this project demonstrates

This project demonstrates practical skills in:

- Microsoft Intune administration
- Microsoft Entra ID user and group management
- Windows device enrollment
- Windows BYOD enrollment
- Android Enterprise BYOD work profile enrollment
- iOS/iPadOS enrollment preparation
- Apple MDM Push Certificate setup
- Windows Autopilot preparation and deployment
- Microsoft Store app deployment
- Win32 app packaging and deployment
- Microsoft 365 Apps deployment
- Android Managed Google Play app deployment
- Windows configuration profile deployment
- ADMX-backed policy configuration
- PowerShell platform script deployment
- Corporate wallpaper deployment
- USB/removable storage restriction
- Microsoft Defender Antivirus policy deployment
- Windows Firewall policy deployment
- BitLocker encryption policy deployment
- Endpoint security policy reporting
- Compliance and Conditional Access planning
- Remote actions and monitoring planning
- Intune troubleshooting documentation

---

## How to use this repository

This repository is updated as each lab is completed.

Each completed lab document should follow this standard format:

```text
# Lab Title

## Lab status
## Lab objective
## Why this lab matters
## Lab environment
## Prerequisites
## Configuration flow
## Steps performed
## Validation
## Final test result
## Screenshots captured
## Troubleshooting notes
## Enterprise reflection
## Security and privacy notes
## Related labs
## Key learning outcomes
## Lab conclusion
```

---

## Screenshot storage

Sanitized screenshots are stored under:

```text
screenshots/sanitized/
```

Example folders:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/endpoint-security/
```

---

## Privacy and security

This is a public learning repository.

Do not upload sensitive information, including:

- Real tenant IDs
- Full real email addresses
- Passwords
- MFA QR codes
- Device serial numbers
- Device IDs
- Object IDs
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Android IMEI numbers
- Phone numbers
- Unsanitized screenshots
- Production company data

All screenshots must be sanitized before uploading to GitHub.

---

## Next step

Recommended next lab:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Alternative next lab:

```text
02-device-enrollment/ios-byod-enrollment.md
```

The iOS BYOD lab has admin prerequisites completed, but physical iPhone/iPad enrollment is still pending.
