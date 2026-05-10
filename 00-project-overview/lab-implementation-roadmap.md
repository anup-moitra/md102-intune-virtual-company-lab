# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap will be updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration, application deployment, endpoint security, monitoring, and troubleshooting labs.

---

## Current Project Status

The project has completed the foundation documentation, the first identity lab, the first Windows device enrollment lab, and the Microsoft Store app deployment lab.

Completed work:

- README created
- Company scenario documented
- Device inventory documented
- Lab implementation roadmap documented
- Microsoft Entra ID users and groups created
- user01 license assignment completed
- Windows OOBE enrollment for WIN-CORP-001 completed
- Intune enrollment issue documented and resolved with manual MDM enrollment
- Microsoft Store app deployment completed
- Required Microsoft Store apps verified in Company Portal
- Available Microsoft Store apps verified in Company Portal

Current focus:

- Continue with Win32 7-Zip app deployment
- Package and upload a Win32 app to Intune
- Configure install command, uninstall command, and detection rule
- Assign the Win32 app to the pilot group
- Verify installation on WIN-CORP-001

> [!NOTE]
> The project is not being completed strictly in folder order. Microsoft Store app deployment was completed before some compliance, Conditional Access, and Autopilot labs. This roadmap reflects the actual hands-on progress.

---

## Implementation Phases

| Phase | Task | Status |
|---|---|---|
| Phase 0 | Create GitHub repository | Completed |
| Phase 1 | Create initial README | Completed |
| Phase 2 | Create company scenario documentation | Completed |
| Phase 3 | Create device inventory documentation | Completed |
| Phase 4 | Create lab implementation roadmap | Completed |
| Phase 5 | Create Microsoft Entra ID users documentation | Completed |
| Phase 6 | Create Microsoft Entra ID groups documentation | Completed |
| Phase 7 | Assign Intune licenses to lab users | Completed |
| Phase 8 | Configure automatic MDM enrollment | In progress / needs review |
| Phase 9 | Enroll corporate Windows device WIN-CORP-001 | Completed |
| Phase 10 | Create Windows basic compliance policy | Planned |
| Phase 11 | Create Conditional Access policy in Report-only mode | Planned |
| Phase 12 | Test compliant corporate Windows sign-in | Planned |
| Phase 13 | Test unmanaged BYOD sign-in | Planned |
| Phase 14 | Create basic Windows configuration profile | Planned |
| Phase 15 | Deploy Microsoft Store apps | Completed |
| Phase 16 | Deploy Win32 app using Intune | Next |
| Phase 17 | Configure Defender Antivirus policy | Planned |
| Phase 18 | Configure Windows Firewall policy | Planned |
| Phase 19 | Configure BitLocker encryption policy | Planned |
| Phase 20 | Configure Windows Autopilot | Planned |
| Phase 21 | Deploy Microsoft 365 Apps | Planned |
| Phase 22 | Test Windows BYOD enrollment | Planned |
| Phase 23 | Test Android BYOD enrollment | Planned |
| Phase 24 | Test iOS BYOD enrollment | Planned |
| Phase 25 | Configure Attack Surface Reduction policy | Planned |
| Phase 26 | Configure Windows Security Baseline | Planned |
| Phase 27 | Test remote actions and monitoring | Planned |
| Phase 28 | Create troubleshooting documentation | Planned |

> [!NOTE]
> Automatic MDM enrollment remains marked as `In progress / needs review` because the first Windows OOBE lab required manual MDM enrollment troubleshooting. The issue is documented in the Windows OOBE enrollment lab.

---

## Section Roadmap

### 00 - Project Overview

| File | Status |
|---|---|
| README.md | Completed |
| 00-project-overview/company-scenario.md | Completed |
| 00-project-overview/device-inventory.md | Completed |
| 00-project-overview/lab-implementation-roadmap.md | Completed |

### 01 - Identity and Groups

| File | Status |
|---|---|
| 01-identity-and-groups/users-and-groups.md | Completed |

This section documents:

- Lab admin account
- Standard test users
- Pilot users
- Microsoft Entra ID security groups
- Group assignment strategy
- License assignment plan
- Screenshots for identity setup

### 02 - Device Enrollment

| File | Status |
|---|---|
| 02-device-enrollment/windows-oobe-enrollment.md | Completed |
| 02-device-enrollment/windows-autopilot-user-driven-enrollment.md | Planned |
| 02-device-enrollment/windows-byod-enrollment.md | Planned |
| 02-device-enrollment/android-byod-enrollment.md | Planned |
| 02-device-enrollment/ios-byod-enrollment.md | Planned |

This section documents Windows corporate enrollment, Windows Autopilot, and BYOD enrollment scenarios.

The Windows OOBE enrollment lab is completed for:

```text
WIN-CORP-001
```

The lab also documents the troubleshooting path where the device initially showed `MDM: None` in Microsoft Entra ID and was later enrolled into Intune using manual MDM enrollment.

### 03 - Configuration Profiles

| File | Status |
|---|---|
| 03-configuration-profiles/windows-basic-configuration-profile.md | Planned |
| 03-configuration-profiles/windows-corporate-wallpaper-policy.md | Planned |
| 03-configuration-profiles/windows-device-restrictions-profile.md | Planned |

This section will document Windows configuration settings pushed by Microsoft Intune.

### 04 - Compliance and Conditional Access

| File | Status |
|---|---|
| 04-compliance-and-conditional-access/windows-basic-compliance-policy.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-compliant-device.md | Planned |
| 04-compliance-and-conditional-access/managed-noncompliant-device-test.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md | Planned |

This section will document device compliance and access control testing.

### 05 - Application Deployment

| File | Status |
|---|---|
| 05-application-deployment/microsoft-store-app-deployment.md | Completed |
| 05-application-deployment/win32-app-deployment-7zip.md | Next |
| 05-application-deployment/microsoft-365-apps-autopilot-deployment.md | Planned |
| 05-application-deployment/company-portal-self-service-apps.md | Planned |

This section documents Microsoft Store app, Win32 app, Microsoft 365 Apps, and Company Portal app deployment scenarios.

#### Completed application deployment work

Microsoft Store app deployment has been completed and documented.

Required apps tested:

```text
Company Portal
VLC UWP
Slack
```

Available apps tested:

```text
ChatGPT
WhatsApp
```

Observed result:

```text
Required apps installed automatically.
Available apps appeared in Company Portal for user self-service installation.
```

#### Next application deployment work

The next application deployment lab is:

```text
05-application-deployment/win32-app-deployment-7zip.md
```

This lab will demonstrate Win32 app packaging and deployment using Microsoft Intune.

### 06 - Endpoint Security

| File | Status |
|---|---|
| 06-endpoint-security/windows-defender-antivirus-policy.md | Planned |
| 06-endpoint-security/windows-firewall-policy.md | Planned |
| 06-endpoint-security/bitlocker-encryption-policy.md | Planned |
| 06-endpoint-security/attack-surface-reduction-policy.md | Planned |
| 06-endpoint-security/windows-security-baseline.md | Planned |

This section will document Microsoft Defender, Firewall, BitLocker, Attack Surface Reduction, and Security Baseline labs.

### 07 - Remote Actions and Monitoring

| File | Status |
|---|---|
| 07-remote-actions-and-monitoring/device-sync-remote-actions.md | Planned |
| 07-remote-actions-and-monitoring/restart-retire-wipe-actions.md | Planned |
| 07-remote-actions-and-monitoring/collect-diagnostics.md | Planned |
| 07-remote-actions-and-monitoring/device-monitoring-and-reports.md | Planned |

This section will document device sync, restart, retire, wipe, diagnostics collection, monitoring, and reports.

### 08 - Troubleshooting

| File | Status |
|---|---|
| 08-troubleshooting/intune-enrollment-troubleshooting.md | Planned |
| 08-troubleshooting/conditional-access-troubleshooting.md | Planned |
| 08-troubleshooting/office-app-signin-troubleshooting.md | Planned |
| 08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md | Planned |

This section will document repeatable troubleshooting checklists and realistic support scenarios.

---

## Completed Hands-On Lab Sequence

| Step | Lab Task | Status |
|---|---|---|
| 1 | Create Microsoft Entra ID lab users | Completed |
| 2 | Create Microsoft Entra ID security groups | Completed |
| 3 | Assign Intune licenses to test users | Completed |
| 4 | Configure automatic MDM enrollment | In progress / needs review |
| 5 | Enroll WIN-CORP-001 through Windows OOBE | Completed |
| 6 | Confirm WIN-CORP-001 appears in Intune | Completed |
| 7 | Deploy Microsoft Store apps | Completed |
| 8 | Verify required apps installed | Completed |
| 9 | Verify available apps in Company Portal | Completed |

---

## Upcoming Hands-On Lab Sequence

| Step | Lab Task | Status |
|---|---|---|
| 1 | Prepare 7-Zip installer source folder | Next |
| 2 | Package 7-Zip as `.intunewin` | Planned |
| 3 | Upload Win32 app to Intune | Planned |
| 4 | Configure install and uninstall commands | Planned |
| 5 | Configure detection rule | Planned |
| 6 | Assign app to GRP-Pilot-Users | Planned |
| 7 | Sync WIN-CORP-001 | Planned |
| 8 | Verify 7-Zip installation | Planned |
| 9 | Capture sanitized screenshots | Planned |
| 10 | Update GitHub documentation | Planned |

---

## Documentation Rules

Each lab file should follow a consistent structure:

```text
Objective
Lab environment
Why this lab matters
Prerequisites
Steps performed
Test result
Screenshots
Troubleshooting notes
Security and privacy notes
```

This makes the repository easier to read and easier to present as a portfolio project.

---

## Screenshot Rules

All screenshots must be sanitized before uploading to GitHub.

Do not upload screenshots that show:

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
- Production company data

Screenshots should be stored in:

```text
screenshots/sanitized/
```

Use subfolders for each lab area.

Examples:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/application-deployment/
```

---

## Current Status Summary

| Area | Status |
|---|---|
| Repository created | Completed |
| README created | Completed |
| Company scenario created | Completed |
| Device inventory created | Completed |
| Lab roadmap created | Completed |
| Identity and groups lab | Completed |
| First Windows enrollment lab | Completed |
| Microsoft Store app deployment lab | Completed |
| Win32 app deployment lab | Next |
| Autopilot enrollment lab | Planned |
| Compliance and Conditional Access labs | Planned |
| Configuration profile labs | Planned |
| Endpoint security labs | Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting labs | Planned |

---

## Next Step

Continue to the Win32 7-Zip app deployment lab:

```text
05-application-deployment/win32-app-deployment-7zip.md
```

This next lab will validate Win32 application deployment using Microsoft Intune, including packaging, app upload, install command, uninstall command, detection rule, assignment, endpoint sync, and installation verification.
