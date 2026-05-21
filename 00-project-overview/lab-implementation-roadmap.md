# Lab Implementation Roadmap

This file tracks the implementation sequence for the MD-102 Intune virtual company lab.

The roadmap reflects the completed state of the project across identity, device enrollment, configuration profiles, application deployment, endpoint security, compliance, Conditional Access, remote actions, monitoring, and troubleshooting.

---

## Purpose

The purpose of this roadmap is to keep the MD-102 lab project organized and to show how each section connects to the full Microsoft Intune and Microsoft Entra endpoint management flow.

This file tracks:

- Which labs are completed
- Which labs are still in progress
- Which labs are intentionally removed from scope
- How the labs connect to the overall endpoint management project
- The final hands-on sequence completed across the repository

---

## Current Project Status

The project is complete across all major hands-on sections.

Completed areas:

- Project overview documentation
- Device inventory documentation
- Microsoft Entra ID users and groups
- License assignment
- Windows OOBE enrollment
- Windows Autopilot user-driven enrollment
- Windows BYOD enrollment
- Android BYOD work profile enrollment
- iOS/iPadOS BYOD enrollment admin prerequisites
- Windows configuration profiles
- Corporate wallpaper policy
- USB storage restriction policy
- Microsoft Store app deployment
- Win32 app deployment with 7-Zip
- Microsoft 365 Apps deployment
- Android Managed Google Play app deployment
- Microsoft Defender Antivirus endpoint security policy
- Windows Firewall endpoint security policy
- BitLocker encryption endpoint security policy
- Attack Surface Reduction policy in Audit mode
- Windows Security Baseline deployment and troubleshooting
- Windows basic compliance policy
- Conditional Access report-only compliant device test
- Managed noncompliant BYOD device test
- Conditional Access enforced mode test
- Device sync remote action
- Restart, Retire, and Wipe remote actions
- Collect diagnostics remote action
- Device monitoring and reports
- Intune enrollment troubleshooting case study
- Configuration policy conflict troubleshooting case study
- Remote actions diagnostics troubleshooting case study
- Troubleshooting summary

One item remains in progress:

```text
02-device-enrollment/ios-byod-enrollment.md
```

Admin prerequisites for iOS/iPadOS BYOD enrollment are completed. Physical iPhone/iPad enrollment is pending hardware availability.

One previously planned item was removed from scope:

```text
05-application-deployment/company-portal-self-service-apps.md
```

This was removed because self-service app behavior was already covered in the Microsoft Store app deployment lab.

---

## Implementation Phases

| Phase | Area | Status |
|---|---|---|
| Phase 00 | GitHub repository and project structure | Completed |
| Phase 01 | Project overview documentation | Completed |
| Phase 02 | Identity and groups | Completed |
| Phase 03 | Device enrollment | Completed - iOS physical enrollment pending |
| Phase 04 | Configuration profiles | Completed |
| Phase 05 | Application deployment | Completed |
| Phase 06 | Endpoint security policies | Completed |
| Phase 07 | Compliance and Conditional Access | Completed |
| Phase 08 | Remote actions and monitoring | Completed |
| Phase 09 | Troubleshooting documentation | Completed |
| Phase 10 | Optional iOS/iPadOS physical enrollment | Pending hardware availability |

> [!NOTE]
> Device enrollment is marked as completed with one exception. Windows OOBE, Windows Autopilot, Windows BYOD, and Android BYOD are completed. iOS/iPadOS admin prerequisites are completed, but physical iPhone/iPad enrollment is pending hardware availability.

---

## Detailed Implementation Status

| Task | Status |
|---|---|
| Create GitHub repository | Completed |
| Create initial README | Completed |
| Create company scenario documentation | Completed |
| Create device inventory documentation | Completed |
| Create lab implementation roadmap | Completed |
| Create Microsoft Entra ID users documentation | Completed |
| Create Microsoft Entra ID groups documentation | Completed |
| Assign Intune licenses to lab users | Completed |
| Configure automatic MDM enrollment | Completed |
| Enroll corporate Windows device WIN-CORP-001 | Completed |
| Configure Windows Autopilot user-driven enrollment | Completed |
| Enroll Autopilot Windows device WINAUTO452 | Completed |
| Test Windows BYOD enrollment | Completed |
| Test Android BYOD enrollment | Completed |
| Prepare iOS/iPadOS BYOD enrollment prerequisites | Completed |
| Complete physical iOS/iPadOS BYOD enrollment | Pending - hardware required |
| Create Windows basic configuration profile | Completed |
| Deploy corporate wallpaper policy | Completed |
| Deploy USB storage restriction policy | Completed |
| Deploy Microsoft Store apps | Completed |
| Deploy Win32 app using Intune | Completed |
| Deploy Microsoft 365 Apps | Completed |
| Deploy Android Managed Google Play apps | Completed |
| Configure Defender Antivirus policy | Completed |
| Configure Windows Firewall policy | Completed |
| Configure BitLocker encryption policy | Completed |
| Configure Attack Surface Reduction policy | Completed |
| Configure Windows Security Baseline | Completed |
| Create Windows basic compliance policy | Completed |
| Create Conditional Access policy in Report-only mode | Completed |
| Test compliant device Conditional Access result | Completed |
| Create managed noncompliant BYOD test | Completed |
| Test report-only failure for noncompliant BYOD device | Completed |
| Create Conditional Access enforced mode policy | Completed |
| Test enforced block for noncompliant BYOD device | Completed |
| Execute device sync remote action | Completed |
| Execute restart remote action | Completed |
| Execute retire remote action | Completed |
| Execute wipe remote action | Completed |
| Execute collect diagnostics remote action | Completed |
| Review Intune device monitoring and reports | Completed |
| Create Intune enrollment troubleshooting documentation | Completed |
| Create configuration policy conflict troubleshooting documentation | Completed |
| Create remote actions diagnostics troubleshooting documentation | Completed |
| Create troubleshooting summary documentation | Completed |
| Remove Company Portal self-service app lab from scope | Completed |

---

## Section Roadmap

### 00 - Project Overview

| File | Status |
|---|---|
| `README.md` | Completed / updated |
| `00-project-overview/company-scenario.md` | Completed |
| `00-project-overview/device-inventory.md` | Completed / final lifecycle cleanup pending |
| `00-project-overview/lab-implementation-roadmap.md` | Completed / updated |

This section documents the project structure, virtual company scenario, lab inventory, and implementation tracking.

---

### 01 - Identity and Groups

| File | Status |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Completed |

Completed work:

- Lab admin account created
- Standard test users created
- Pilot users identified
- Microsoft Entra ID security groups created
- Group assignment strategy documented
- License assignment completed
- Groups reused across enrollment, apps, configuration profiles, endpoint security, compliance, Conditional Access, and remote actions

---

### 02 - Device Enrollment

| File | Status |
|---|---|
| `02-device-enrollment/windows-oobe-enrollment.md` | Completed |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Completed |
| `02-device-enrollment/windows-byod-enrollment.md` | Completed |
| `02-device-enrollment/android-byod-enrollment.md` | Completed |
| `02-device-enrollment/ios-byod-enrollment.md` | In Progress - admin prerequisites completed |

Completed enrollment results:

| Device | Enrollment type | Result |
|---|---|---|
| WIN-CORP-001 | Windows OOBE / corporate enrollment | Enrolled in Intune, later wiped during remote actions lab |
| WINAUTO452 | Windows Autopilot user-driven enrollment | Enrolled and managed by Intune, later retired during remote actions lab |
| WIN-BYOD-001 | Windows BYOD enrollment | Enrolled as personal device |
| ANDROID-BYOD-001 | Android Enterprise BYOD work profile | Work profile enrolled |
| IOS-BYOD-001 | iOS/iPadOS BYOD | Admin prerequisites completed, physical device pending |

> [!NOTE]
> The iOS/iPadOS lab has admin prerequisites completed, including Apple MDM push certificate preparation. Physical iPhone/iPad enrollment remains pending.

---

### 03 - Configuration Profiles

| File | Status |
|---|---|
| `03-configuration-profiles/windows-basic-configuration-profile.md` | Completed |
| `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Completed |
| `03-configuration-profiles/windows-device-restrictions-profile.md` | Completed |

Completed results:

| Lab | Result |
|---|---|
| Windows basic configuration profile | Created and validated |
| Corporate wallpaper ADMX policy | Wallpaper staged and applied successfully |
| USB storage restriction policy | USB/removable storage blocked successfully |

---

### 04 - Compliance and Conditional Access

| File | Status |
|---|---|
| `04-compliance-and-conditional-access/windows-basic-compliance-policy.md` | Completed |
| `04-compliance-and-conditional-access/conditional-access-compliant-device.md` | Completed |
| `04-compliance-and-conditional-access/managed-noncompliant-device-test.md` | Completed |
| `04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md` | Completed |

Completed compliance and Conditional Access results:

| Lab | Result |
|---|---|
| Windows basic compliance policy | WINAUTO452 became compliant |
| Conditional Access compliant device test | Report-only result showed Success for compliant device |
| Managed noncompliant device test | Report-only result showed Failure for noncompliant BYOD device |
| Conditional Access enforced mode test | Access was blocked for noncompliant BYOD device |

Completed flow:

```text
Intune compliance policy
-> Device compliance state
-> Microsoft Entra Conditional Access evaluation
-> Report-only testing
-> Enforced access blocking
```

---

### 05 - Application Deployment

| File | Status |
|---|---|
| `05-application-deployment/microsoft-store-app-deployment.md` | Completed |
| `05-application-deployment/win32-app-deployment-7zip.md` | Completed |
| `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Completed |
| `05-application-deployment/android-managed-google-play-app-deployment.md` | Completed |
| `05-application-deployment/company-portal-self-service-apps.md` | Removed from scope |

Completed application deployment results:

| Lab | Result |
|---|---|
| Microsoft Store app deployment | Required and available Store apps validated |
| Win32 7-Zip app deployment | 7-Zip packaged as `.intunewin` and deployed |
| Microsoft 365 Apps deployment | Microsoft 365 Apps installed and validated after Autopilot |
| Android Managed Google Play app deployment | Outlook and Teams installed in Android Work profile |
| Company Portal self-service app lab | Removed because self-service app behavior was already demonstrated in Microsoft Store app deployment |

---

### 06 - Endpoint Security

| File | Status |
|---|---|
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Completed |
| `06-endpoint-security/windows-firewall-policy.md` | Completed |
| `06-endpoint-security/bitlocker-encryption-policy.md` | Completed |
| `06-endpoint-security/attack-surface-reduction-policy.md` | Completed |
| `06-endpoint-security/windows-security-baseline.md` | Completed |

Completed endpoint security results:

| Lab | Result |
|---|---|
| Defender Antivirus policy | Success on WINAUTO452 |
| Windows Firewall policy | Success on WINAUTO452 |
| BitLocker encryption policy | Fully encrypted, Protection On |
| Attack Surface Reduction policy | Deployed in Audit mode, Success on WINAUTO452, validated with PowerShell |
| Windows Security Baseline | Conflicts and Error 65000 investigated, remediated, final status Success |

---

### 07 - Remote Actions and Monitoring

| File | Status |
|---|---|
| `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Completed |
| `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` | Completed |
| `07-remote-actions-and-monitoring/collect-diagnostics.md` | Completed |
| `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Completed |

Completed remote actions and monitoring results:

| Lab | Result |
|---|---|
| Device sync remote action | Sync initiated from Intune and verified from local Windows Settings |
| Restart, Retire, and Wipe actions | All actions confirmed in Device Actions report |
| Collect diagnostics | Action completed and verified from Device action status |
| Device monitoring and reports | Device inventory, action history, noncompliant devices report, and policy assignment status reviewed |

Remote actions tested:

| Action | Device | Result |
|---|---|---|
| Sync | WINAUTO452 | Completed |
| Restart | WINAUTO452 | Completed |
| Retire | WINAUTO452 | Completed |
| Wipe | WIN-CORP-001 | Completed |
| Collect diagnostics | WINAUTO452 | Completed |

---

### 08 - Troubleshooting

| File | Status |
|---|---|
| `08-troubleshooting/intune-enrollment-troubleshooting.md` | Completed |
| `08-troubleshooting/configuration-policy-conflict-troubleshooting.md` | Completed |
| `08-troubleshooting/remote-actions-diagnostics-troubleshooting.md` | Completed |
| `08-troubleshooting/troubleshooting-summary.md` | Completed |

Troubleshooting coverage:

| Case study | Issue | Resolution |
|---|---|---|
| Intune enrollment troubleshooting | Device joined Microsoft Entra ID but MDM showed None | Manual MDM enrollment completed |
| Configuration policy conflict troubleshooting | Security Baseline reported Conflict and Error 65000 | Overlapping or unsupported settings set to Not configured |
| Remote actions diagnostics troubleshooting | Expected Device diagnostics report path was not visible in the same way in the tenant | Action validated using device-level Device action status and tenant settings |

---

## Completed Hands-On Lab Sequence

| Step | Lab Task | Status |
|---|---|---|
| 1 | Create Microsoft Entra ID lab users | Completed |
| 2 | Create Microsoft Entra ID security groups | Completed |
| 3 | Assign Intune licenses to test users | Completed |
| 4 | Configure and validate MDM enrollment behavior | Completed |
| 5 | Enroll WIN-CORP-001 through Windows OOBE | Completed |
| 6 | Confirm WIN-CORP-001 appears in Intune | Completed |
| 7 | Configure Windows Autopilot user-driven enrollment | Completed |
| 8 | Enroll WINAUTO452 using Autopilot | Completed |
| 9 | Enroll WIN-BYOD-001 as Windows BYOD device | Completed |
| 10 | Enroll Android BYOD work profile | Completed |
| 11 | Complete iOS/iPadOS admin prerequisites | Completed |
| 12 | Deploy Windows configuration profiles | Completed |
| 13 | Deploy Microsoft Store apps | Completed |
| 14 | Deploy Win32 7-Zip app | Completed |
| 15 | Deploy Microsoft 365 Apps | Completed |
| 16 | Deploy Android Managed Google Play apps | Completed |
| 17 | Configure Defender Antivirus policy | Completed |
| 18 | Configure Windows Firewall policy | Completed |
| 19 | Configure BitLocker encryption policy | Completed |
| 20 | Configure Attack Surface Reduction policy in Audit mode | Completed |
| 21 | Deploy Windows Security Baseline and remediate conflicts | Completed |
| 22 | Create Windows basic compliance policy | Completed |
| 23 | Validate compliant device state | Completed |
| 24 | Create Conditional Access report-only policy | Completed |
| 25 | Validate report-only success for compliant device | Completed |
| 26 | Create managed noncompliant BYOD test | Completed |
| 27 | Validate report-only failure for noncompliant BYOD device | Completed |
| 28 | Create enforced Conditional Access policy | Completed |
| 29 | Validate access blocked for noncompliant BYOD device | Completed |
| 30 | Execute device sync remote action from Intune | Completed |
| 31 | Validate local Windows sync from Settings | Completed |
| 32 | Execute restart remote action on WINAUTO452 | Completed |
| 33 | Execute retire remote action on WINAUTO452 | Completed |
| 34 | Execute wipe remote action on WIN-CORP-001 | Completed |
| 35 | Validate all remote actions in Device Actions report | Completed |
| 36 | Execute collect diagnostics remote action | Completed |
| 37 | Validate diagnostics from Device action status | Completed |
| 38 | Review Intune device monitoring and reports | Completed |
| 39 | Document Intune enrollment troubleshooting case study | Completed |
| 40 | Document configuration policy conflict troubleshooting case study | Completed |
| 41 | Document remote actions diagnostics troubleshooting case study | Completed |
| 42 | Complete troubleshooting summary | Completed |

---

## Completed Modern Endpoint Management Flow

The completed labs demonstrate this Microsoft Intune and Microsoft Entra endpoint management chain:

```text
Microsoft Entra users and groups
-> Intune license assignment
-> Device enrollment
-> Windows OOBE enrollment
-> Windows Autopilot provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> iOS/iPadOS admin prerequisites
-> Configuration profiles applied
-> Application deployment
-> Endpoint security policies
-> Attack Surface Reduction in Audit mode
-> Windows Security Baseline deployed and troubleshot
-> Compliance policy evaluation
-> Conditional Access report-only testing
-> Conditional Access enforced access blocking
-> Device sync remote action
-> Restart, Retire, and Wipe remote actions
-> Collect diagnostics remote action
-> Device monitoring and reports
-> Troubleshooting case studies documented
```

---

## Current Status Summary

| Area | Status |
|---|---|
| Repository setup | Completed |
| Project overview | Completed |
| Identity and groups | Completed |
| Device enrollment | Completed - iOS physical enrollment pending |
| Configuration profiles | Completed |
| Application deployment | Completed |
| Endpoint security | Completed |
| Compliance and Conditional Access | Completed |
| Remote actions and monitoring | Completed |
| Troubleshooting documentation | Completed |
| iOS/iPadOS physical enrollment | Pending - hardware required |
| Final device inventory lifecycle cleanup | Pending |

---

## Documentation Rules

Each lab file should follow a consistent structure:

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

Troubleshooting files use a case study format instead of the standard lab format.

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
- Android IMEI numbers
- Phone numbers
- Diagnostic ZIP package contents
- Production company data
- Unsanitized screenshots

Screenshots are stored under:

```text
screenshots/sanitized/
```

Screenshot folders used in this project:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/compliance-and-conditional-access/
screenshots/sanitized/endpoint-security/
screenshots/sanitized/remote-actions-and-monitoring/
```

---

## Final Remaining Items

The core hands-on MD-102 lab project is completed.

Remaining documentation/future items:

| Item | Status |
|---|---|
| Update device inventory with final lifecycle states | Pending |
| Optional physical iOS/iPadOS enrollment | Pending hardware availability |
| Final GitHub visual review | Recommended |

---

## Notes for Future Updates

Update this roadmap whenever a new lab is added or an optional pending item is completed.

When a file is added or updated, also check:

```text
README.md
00-project-overview/device-inventory.md
00-project-overview/lab-implementation-roadmap.md
```

This roadmap is currently aligned with the completed lab project, except for the pending device inventory lifecycle cleanup and optional physical iOS/iPadOS enrollment.
