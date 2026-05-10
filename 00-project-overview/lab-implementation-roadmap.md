# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap will be updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration and troubleshooting labs.

---

## Current Project Status

The project is currently in the foundation setup phase.

Completed foundation documentation:

- README created
- Company scenario documented
- Device inventory documented

Current focus:

- Complete the project overview roadmap
- Create identity and group documentation
- Start the first hands-on Microsoft Entra ID and Intune preparation labs

---

## Implementation Phases

| Phase | Task | Status |
|---|---|---|
| Phase 0 | Create GitHub repository | Completed |
| Phase 1 | Create initial README | Completed |
| Phase 2 | Create company scenario documentation | Completed |
| Phase 3 | Create device inventory documentation | Completed |
| Phase 4 | Create lab implementation roadmap | Completed |
| Phase 5 | Create Microsoft Entra ID users documentation | Planned |
| Phase 6 | Create Microsoft Entra ID groups documentation | Planned |
| Phase 7 | Assign Intune licenses to lab users | Planned |
| Phase 8 | Configure automatic MDM enrollment | Planned |
| Phase 9 | Enroll corporate Windows device WIN-CORP-001 | Planned |
| Phase 10 | Create Windows basic compliance policy | Planned |
| Phase 11 | Create Conditional Access policy in Report-only mode | Planned |
| Phase 12 | Test compliant corporate Windows sign-in | Planned |
| Phase 13 | Test unmanaged BYOD sign-in | Planned |
| Phase 14 | Create basic Windows configuration profile | Planned |
| Phase 15 | Deploy Microsoft Store apps | Planned |
| Phase 16 | Deploy Win32 app using Intune | Planned |
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

This section will document:

- Lab admin account
- Standard test users
- Pilot users
- Microsoft Entra ID security groups
- Group assignment strategy
- License assignment plan

### 02 - Device Enrollment

| File | Status |
|---|---|
| 02-device-enrollment/windows-oobe-enrollment.md | Planned |
| 02-device-enrollment/windows-autopilot-user-driven-enrollment.md | Planned |
| 02-device-enrollment/windows-byod-enrollment.md | Planned |
| 02-device-enrollment/android-byod-enrollment.md | Planned |
| 02-device-enrollment/ios-byod-enrollment.md | Planned |

This section will document Windows corporate enrollment, Windows Autopilot, and BYOD enrollment scenarios.

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
| 05-application-deployment/microsoft-store-app-deployment.md | Planned |
| 05-application-deployment/win32-app-deployment-7zip.md | Planned |
| 05-application-deployment/microsoft-365-apps-autopilot-deployment.md | Planned |
| 05-application-deployment/company-portal-self-service-apps.md | Planned |

This section will document Microsoft Store app, Win32 app, Microsoft 365 Apps, and Company Portal app deployment scenarios.

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

## First Hands-On Lab Sequence

The first hands-on labs should be completed in this order:

1. Create Microsoft Entra ID lab users.
2. Create Microsoft Entra ID security groups.
3. Assign Intune licenses to test users.
4. Configure automatic MDM enrollment.
5. Enroll WIN-CORP-001 through Windows OOBE.
6. Confirm WIN-CORP-001 appears in Intune.
7. Create a basic Windows compliance policy.
8. Confirm WIN-CORP-001 reports compliant.
9. Create Conditional Access policy in Report-only mode.
10. Test compliant corporate device access.
11. Test unmanaged BYOD access.

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

---

## Current Status Summary

| Area | Status |
|---|---|
| Repository created | Completed |
| README created | Completed |
| Company scenario created | Completed |
| Device inventory created | Completed |
| Lab roadmap created | Completed |
| Identity and groups lab | Planned |
| First Windows enrollment lab | Planned |

---

## Next Step

Continue to the Windows OOBE enrollment lab:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

This will be the first hands-on preparation step before Windows device enrollment.
