# MD-102 Intune Virtual Company Lab

This repository documents a hands-on Microsoft Intune and MD-102 lab environment.

The project simulates a small company using Microsoft Entra ID, Microsoft Intune, Windows Autopilot, compliance policies, Conditional Access, application deployment, endpoint security, BYOD enrollment, remote actions, monitoring, and troubleshooting.

---

## Project Goal

The goal of this project is to build practical Microsoft Intune administration experience and document each lab in a professional GitHub portfolio format.

This project is designed to show real-world endpoint administration skills, including:

- Creating and managing users and groups
- Enrolling Windows devices into Microsoft Intune
- Configuring compliance policies
- Testing Conditional Access
- Deploying applications
- Managing endpoint security settings
- Using Windows Autopilot
- Supporting BYOD scenarios
- Monitoring and troubleshooting devices

---

## Virtual Company Scenario

The lab company is called **Contoso Startup Lab**.

Contoso Startup Lab represents a small organization with a mixed device environment.

The company includes:

- Corporate-owned Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD devices
- iOS BYOD devices
- Microsoft Entra ID users and groups
- Microsoft Intune device management
- Microsoft 365 Apps
- Conditional Access and compliance controls

---

## Lab Sections

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

## Planned Repository Structure

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

---

## Current Status

| Task | Status |
|---|---|
| GitHub repository created | Planned |
| Initial README created | Completed |
| Project overview folder created | Planned |
| Company scenario documented | Planned |
| Device inventory documented | Planned |
| Lab roadmap documented | Planned |
| First Intune lab started | Planned |

---

## Skills This Project Will Demonstrate

This project will demonstrate practical skills in:

- Microsoft Intune administration
- Microsoft Entra ID user and group management
- Windows device enrollment
- Windows Autopilot
- Device compliance policies
- Conditional Access
- Microsoft Store app deployment
- Win32 app deployment
- Microsoft 365 Apps deployment
- Microsoft Defender Antivirus policy
- Windows Firewall policy
- BitLocker encryption policy
- Attack Surface Reduction policy
- Windows Security Baseline
- BYOD management
- Device monitoring and reports
- Intune troubleshooting

---

## How to Use This Repository

This repository will be updated as each lab is completed.

Each lab document will include:

- Objective
- Lab environment
- Steps performed
- Configuration details
- Test result
- Screenshots
- Troubleshooting notes
- Privacy and security notes

---

## Privacy and Security

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
- Unsanitized screenshots
- Production company data

All screenshots must be sanitized before uploading to GitHub.

---

## Notes

This project is for learning, portfolio building, and MD-102 preparation.

The environment, company name, users, devices, and screenshots are fictional, test-only, or sanitized.
