# MD-102 Intune Virtual Company Lab

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![MD-102](https://img.shields.io/badge/Exam-MD--102-blue.svg)](https://learn.microsoft.com/en-us/credentials/certifications/modern-desktop/)
[![Microsoft Intune](https://img.shields.io/badge/Microsoft-Intune-0078D4?logo=microsoft)](https://learn.microsoft.com/en-us/mem/intune/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Android%20%7C%20iOS-lightgrey.svg)](#)

Hands-on MD-102 lab project simulating a small virtual company using Microsoft Intune, Microsoft Entra ID, Windows devices, BYOD scenarios, Windows Autopilot, configuration profiles, compliance policies, Conditional Access, application deployment, endpoint security, remote actions, monitoring, and troubleshooting.

---

## How to Use This Repo

This repository is organised as a numbered lab series. Each folder covers a distinct area of Microsoft Intune endpoint management. Start with `00-project-overview` to understand the virtual company scenario, then follow the numbered folders in order. Every lab folder contains markdown files documenting the objective, configuration steps, test results, and sanitised screenshots for that topic.

---

## Virtual Company Scenario

This lab simulates a small company named **Contoso Startup Lab**, consisting of:

- Corporate-owned Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD devices
- iOS BYOD devices
- Microsoft Entra ID users and security groups
- Microsoft Intune device management
- Microsoft 365 Apps licensing and deployment
- Endpoint security and compliance controls

---

## Lab Index

| # | Area | Lab Files |
|---|---|---|
| 00 | Project Overview | [company-scenario.md](00-project-overview/company-scenario.md) <br> [device-inventory.md](00-project-overview/device-inventory.md) <br> [lab-implementation-roadmap.md](00-project-overview/lab-implementation-roadmap.md) |
| 01 | Identity and Groups | [users-and-groups.md](01-identity-and-groups/users-and-groups.md) |
| 02 | Device Enrollment | [windows-oobe-enrollment.md](02-device-enrollment/windows-oobe-enrollment.md) <br> [windows-autopilot-user-driven-enrollment.md](02-device-enrollment/windows-autopilot-user-driven-enrollment.md) <br> [windows-byod-enrollment.md](02-device-enrollment/windows-byod-enrollment.md) <br> [android-byod-enrollment.md](02-device-enrollment/android-byod-enrollment.md) <br> [ios-byod-enrollment.md](02-device-enrollment/ios-byod-enrollment.md) |
| 03 | Configuration Profiles | [windows-basic-configuration-profile.md](03-configuration-profiles/windows-basic-configuration-profile.md) <br> [windows-corporate-wallpaper-policy.md](03-configuration-profiles/windows-corporate-wallpaper-policy.md) <br> [windows-device-restrictions-profile.md](03-configuration-profiles/windows-device-restrictions-profile.md) |
| 04 | Compliance and Conditional Access | [windows-basic-compliance-policy.md](04-compliance-and-conditional-access/windows-basic-compliance-policy.md) <br> [conditional-access-compliant-device.md](04-compliance-and-conditional-access/conditional-access-compliant-device.md) <br> [managed-noncompliant-device-test.md](04-compliance-and-conditional-access/managed-noncompliant-device-test.md) <br> [conditional-access-enforced-mode-test.md](04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md) |
| 05 | Application Deployment | [microsoft-store-app-deployment.md](05-application-deployment/microsoft-store-app-deployment.md) <br> [win32-app-deployment-7zip.md](05-application-deployment/win32-app-deployment-7zip.md) <br> [microsoft-365-apps-autopilot-deployment.md](05-application-deployment/microsoft-365-apps-autopilot-deployment.md) <br> [company-portal-self-service-apps.md](05-application-deployment/company-portal-self-service-apps.md) |
| 06 | Endpoint Security | [windows-defender-antivirus-policy.md](06-endpoint-security/windows-defender-antivirus-policy.md) <br> [windows-firewall-policy.md](06-endpoint-security/windows-firewall-policy.md) <br> [bitlocker-encryption-policy.md](06-endpoint-security/bitlocker-encryption-policy.md) <br> [attack-surface-reduction-policy.md](06-endpoint-security/attack-surface-reduction-policy.md) <br> [windows-security-baseline.md](06-endpoint-security/windows-security-baseline.md) |
| 07 | Remote Actions and Monitoring | [device-sync-remote-actions.md](07-remote-actions-and-monitoring/device-sync-remote-actions.md) <br> [restart-retire-wipe-actions.md](07-remote-actions-and-monitoring/restart-retire-wipe-actions.md) <br> [collect-diagnostics.md](07-remote-actions-and-monitoring/collect-diagnostics.md) <br> [device-monitoring-and-reports.md](07-remote-actions-and-monitoring/device-monitoring-and-reports.md) |
| 08 | Troubleshooting | [autopilot-motherboard-replacement-troubleshooting.md](08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md) <br> [office-app-signin-troubleshooting.md](08-troubleshooting/office-app-signin-troubleshooting.md) <br> [intune-enrollment-troubleshooting.md](08-troubleshooting/intune-enrollment-troubleshooting.md) <br> [conditional-access-troubleshooting.md](08-troubleshooting/conditional-access-troubleshooting.md) |

---

## Repository Structure

```
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
├── 08-troubleshooting/
│   ├── autopilot-motherboard-replacement-troubleshooting.md
│   ├── office-app-signin-troubleshooting.md
│   ├── intune-enrollment-troubleshooting.md
│   └── conditional-access-troubleshooting.md
├── assets/
│   └── wallpapers/
│       └── Wallpaper.jpg
└── screenshots/
    └── sanitized/
        ├── identity-and-groups/
        ├── device-enrollment/
        ├── compliance/
        ├── conditional-access/
        ├── configuration-profiles/
        ├── application-deployment/
        ├── endpoint-security/
        ├── remote-actions-and-monitoring/
        └── troubleshooting/
```

---

## Skills Demonstrated

- Microsoft Intune administration
- Microsoft Entra ID — users, groups, and licensing
- Windows device enrollment — OOBE and Autopilot
- BYOD enrollment — Windows, Android, and iOS
- Configuration profile creation and assignment
- Compliance policy creation and validation
- Conditional Access — report-only and enforced modes
- Application deployment — Microsoft Store, Win32, and Microsoft 365 Apps
- Company Portal self-service app deployment
- Endpoint security — Defender Antivirus, Windows Firewall, BitLocker, ASR, and Security Baseline
- BitLocker recovery key escrow verification
- Remote device actions — sync, restart, retire, wipe, and diagnostics collection
- Intune monitoring and reporting
- Troubleshooting — Autopilot, enrollment, Office sign-in, and Conditional Access
- Security-aware documentation and sanitised screenshot practices
- GitHub documentation and structured lab organisation

---

## Test Devices Used

| Device Name | Type | Ownership | OS | Enrollment Method |
|---|---|---|---|---|
| WIN-CORP-001 | Physical laptop | Corporate | Windows 11 | OOBE |
| WIN-CORP-002 | Physical laptop | Corporate | Windows 11 | Windows Autopilot |
| WIN-BYOD-001 | Personal laptop | BYOD | Windows 11 | Entra ID registration |
| Android device | Mobile | BYOD | Android | Android Enterprise |
| iOS device | Mobile | BYOD | iOS | Apple MDM |

---

## Documentation Standards

Every lab file in this repository follows a consistent structure:

- **Objective** — what the lab is testing or demonstrating
- **Lab context** — how it fits into the virtual company scenario
- **Important concepts** — key theory behind the configuration
- **Configuration details** — exact settings used in Intune
- **Steps performed** — step-by-step walkthrough
- **Test result** — what happened and what was confirmed
- **Screenshots** — sanitised evidence of the lab outcome
- **Troubleshooting notes** — any issues encountered and how they were resolved
- **Security and privacy notes** — what sensitive data was excluded or sanitised
- **Current status** — final outcome of the lab

---

## Screenshot and Privacy Standards

All screenshots in this repository are sanitised before upload.

Not published in this repository:

- Real tenant IDs or tenant names
- Full real email addresses
- Passwords or credentials
- MFA QR codes
- Device serial numbers or device IDs
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Production company data

Safe to show:

- Fictional lab user display names
- Sanitised device names such as WIN-CORP-001
- Policy names and configuration settings
- App names and deployment status
- Compliance results and Conditional Access outcomes
- Managed and compliant status after sensitive details are hidden

---

## Disclaimer

This is a public learning and portfolio repository. All company names, users, groups, devices, screenshots, and lab details are fictional, test-only, or sanitised. No real production data, tenant secrets, credentials, device serial numbers, BitLocker recovery keys, Autopilot hardware hashes, or confidential information is published in this repository.

---

## License

This project is licensed under the [MIT License](LICENSE).
