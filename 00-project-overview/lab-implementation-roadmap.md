# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap will be updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration and troubleshooting labs.

---

## Current Project Status

The project has completed the foundation documentation, the first identity lab, and the first Windows device enrollment lab.

Completed work:

- README created
- Company scenario documented
- Device inventory documented
- Lab implementation roadmap documented
- Microsoft Entra ID users and groups created
- user01 license assignment completed
- Windows OOBE enrollment for WIN-CORP-001 completed
- Intune enrollment issue documented and resolved with manual MDM enrollment

Current focus:

- Continue with Windows Autopilot user-driven enrollment
- Compare manual OOBE enrollment with Autopilot provisioning
- Continue building the device enrollment section

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
| Phase 8 | Configure automatic MDM enrollment | In progress |
| Phase 9 | Enroll corporate Windows device WIN-CORP-001 | Completed |
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

> [!NOTE]
> Automatic MDM enrollment is marked as `In progress` because the first Windows OOBE lab required manual MDM enrollment troubleshooting. The issue is documented in the Windows OOBE enrollment lab.

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
- Initial screenshots for identity setup

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

### 04 - Compliance and Conditional Access

| File | Status |
|---|---|
| 04-compliance-and-conditional-access/windows-basic-compliance-policy.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-compliant-device.md | Planned |
| 04-compliance-and-conditional-access/managed-noncompliant-device-test.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md | Planned |

### 05 - Application Deployment

| File | Status |
|---|---|
| 05-application-deployment/microsoft-store-app-deployment.md | Planned |
| 05-application-deployment/win32-app-deployment-7zip.md | Planned |
| 05-application-deployment/microsoft-365-apps-autopilot-deployment.md | Planned |
| 05-application-deployment/company-portal-self-service-apps.md | Planned |

### 06 - Endpoint Security

| File | Status |
|---|---|
| 06-endpoint-security/windows-defender-antivirus-policy.md | Planned |
| 06-endpoint-security/windows-firewall-policy.md | Planned |
| 06-endpoint-security/bitlocker-encryption-policy.md | Planned |
| 06-endpoint-security/attack-surface-reduction-policy.md | Planned |
| 06-endpoint-security/windows-security-baseline.md | Planned |

### 07 - Remote Actions and Monitoring

| File | Status |
|---|---|
| 07-remote-actions-and-monitoring/device-sync-remote-actions.md | Planned |
| 07-remote-actions-and-monitoring/restart-retire-wipe-actions.md | Planned |
| 07-remote-actions-and-monitoring/collect-diagnostics.md | Planned |
| 07-remote-actions-and-monitoring/device-monitoring-and-reports.md | Planned |

### 08 - Troubleshooting

| File | Status |
|---|---|
| 08-troubleshooting/intune-enrollment-troubleshooting.md | Planned |
| 08-troubleshooting/conditional-access-troubleshooting.md | Planned |
| 08-troubleshooting/office-app-signin-troubleshooting.md | Planned |
| 08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md | Planned |

---

## First Hands-On Lab Sequence

| Step | Lab Task | Status |
|---|---|---|
| 1 | Create Microsoft Entra ID lab users | Completed |
| 2 | Create Microsoft Entra ID security groups | Completed |
| 3 | Assign Intune licenses to test users | Completed |
| 4 | Configure automatic MDM enrollment | In progress |
| 5 | Enroll WIN-CORP-001 through Windows OOBE | Completed |
| 6 | Confirm WIN-CORP-001 appears in Intune | Completed |
| 7 | Create a basic Windows compliance policy | Planned |
| 8 | Confirm WIN-CORP-001 reports compliant | Planned |
| 9 | Create Conditional Access policy in Report-only mode | Planned |
| 10 | Test compliant corporate device access | Planned |
| 11 | Test unmanaged BYOD access | Planned |

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
| Autopilot enrollment lab | Planned |

---

## Next Step

Continue to the Windows Autopilot user-driven enrollment lab:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

This will compare manual Windows OOBE enrollment with the Autopilot provisioning experience.
