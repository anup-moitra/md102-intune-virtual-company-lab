# Lab Implementation Roadmap

This file tracks the implementation sequence for the MD-102 Intune virtual company lab.

The roadmap is now updated to reflect the current project state after completing the Compliance and Conditional Access labs in Section 04.

---

## Purpose

The purpose of this roadmap is to keep the MD-102 lab project organized as each section is created, tested, documented, and updated in GitHub.

This file helps track:

- Which labs are completed
- Which labs are in progress
- Which labs are planned next
- How each lab connects to the full Microsoft Intune and Microsoft Entra endpoint management flow

---

## Current Project Status

The project has progressed beyond the early Windows enrollment stage.

The lab environment now includes completed work across identity, enrollment, configuration profiles, application deployment, endpoint security, compliance policies, and Conditional Access testing.

Completed major areas:

- Project overview documentation
- Device inventory documentation
- Microsoft Entra ID users and groups
- License assignment planning
- Windows OOBE enrollment
- Windows Autopilot user-driven enrollment
- Windows BYOD enrollment
- Android BYOD work profile enrollment
- iOS/iPadOS BYOD enrollment prerequisites
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
- Windows basic compliance policy
- Conditional Access report-only compliant device test
- Managed noncompliant BYOD device test
- Conditional Access enforced mode test

Current focus:

- Clean up tracking documentation so README and roadmap match the completed labs
- Continue with Conditional Access troubleshooting documentation
- Continue with remote actions and monitoring labs
- Later return to optional iOS physical device enrollment, Attack Surface Reduction, and Windows Security Baseline labs

---

## Implementation Phases

| Phase | Area | Status |
|---|---|---|
| Phase 00 | GitHub repository and project structure | Completed |
| Phase 01 | Project overview documentation | Completed |
| Phase 02 | Identity and groups | Completed |
| Phase 03 | Device enrollment | Mostly completed |
| Phase 04 | Configuration profiles | Completed |
| Phase 05 | Application deployment | Completed |
| Phase 06 | Core endpoint security policies | Completed |
| Phase 07 | Compliance and Conditional Access | Completed |
| Phase 08 | Remote actions and monitoring | Planned |
| Phase 09 | Troubleshooting documentation | Planned |
| Phase 10 | Advanced endpoint security | Planned |
| Phase 11 | Optional device platform expansion | Planned |

> [!NOTE]
> Device enrollment is marked as mostly completed because Windows OOBE, Windows Autopilot, Windows BYOD, and Android BYOD are completed. iOS/iPadOS admin prerequisites are completed, but physical iPhone/iPad enrollment is still pending.

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
| Configure automatic MDM enrollment | Completed / validated during enrollment labs |
| Enroll corporate Windows device WIN-CORP-001 | Completed |
| Configure Windows Autopilot user-driven enrollment | Completed |
| Enroll Autopilot Windows device WINAUTO452 | Completed |
| Test Windows BYOD enrollment | Completed |
| Test Android BYOD enrollment | Completed |
| Prepare iOS/iPadOS BYOD enrollment prerequisites | Completed |
| Complete physical iOS/iPadOS BYOD enrollment | Pending |
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
| Create Windows basic compliance policy | Completed |
| Create Conditional Access policy in Report-only mode | Completed |
| Test compliant device Conditional Access result | Completed |
| Create managed noncompliant BYOD test | Completed |
| Test report-only failure for noncompliant BYOD device | Completed |
| Create Conditional Access enforced mode policy | Completed |
| Test enforced block for noncompliant BYOD device | Completed |
| Configure Attack Surface Reduction policy | Planned |
| Configure Windows Security Baseline | Planned |
| Test remote actions and monitoring | Planned |
| Create Conditional Access troubleshooting documentation | Recommended next |
| Create general Intune troubleshooting documentation | Planned |

---

## Section Roadmap

### 00 - Project Overview

| File | Status |
|---|---|
| `README.md` | Completed / updated |
| `00-project-overview/company-scenario.md` | Completed |
| `00-project-overview/device-inventory.md` | Completed |
| `00-project-overview/lab-implementation-roadmap.md` | Completed / updated |

This section documents the project structure, virtual company scenario, lab inventory, and implementation tracking.

---

### 01 - Identity and Groups

| File | Status |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Completed |

This section documents:

- Lab admin account
- Standard test users
- Pilot users
- Microsoft Entra ID security groups
- Group assignment strategy
- License assignment plan
- Groups reused across enrollment, apps, configuration profiles, endpoint security, compliance, and Conditional Access

---

### 02 - Device Enrollment

| File | Status |
|---|---|
| `02-device-enrollment/windows-oobe-enrollment.md` | Completed |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Completed |
| `02-device-enrollment/windows-byod-enrollment.md` | Completed |
| `02-device-enrollment/android-byod-enrollment.md` | Completed |
| `02-device-enrollment/ios-byod-enrollment.md` | In Progress / Admin prerequisites completed |

This section documents corporate Windows enrollment, Windows Autopilot, Windows BYOD, Android BYOD, and iOS/iPadOS enrollment preparation.

Completed enrollment results:

| Device | Enrollment type | Result |
|---|---|---|
| WIN-CORP-001 | Windows OOBE / corporate enrollment | Enrolled in Intune |
| WINAUTO452 | Windows Autopilot user-driven enrollment | Enrolled and managed by Intune |
| WIN-BYOD-001 | Windows BYOD enrollment | Enrolled as personal device |
| ANDROID-BYOD-001 | Android Enterprise BYOD work profile | Work profile enrolled |

> [!NOTE]
> The iOS/iPadOS lab has admin prerequisites completed, including Apple MDM push certificate preparation. Physical iPhone/iPad enrollment remains pending.

---

### 03 - Configuration Profiles

| File | Status |
|---|---|
| `03-configuration-profiles/windows-basic-configuration-profile.md` | Completed |
| `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Completed |
| `03-configuration-profiles/windows-device-restrictions-profile.md` | Completed |

This section validates basic Windows device configuration and user experience control through Intune configuration profiles.

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

Completed compliance and Conditional Access labs:

| Lab | File | Result |
|---|---|---|
| Windows basic compliance policy | `04-compliance-and-conditional-access/windows-basic-compliance-policy.md` | WINAUTO452 became compliant after Secure Boot remediation |
| Conditional Access compliant device | `04-compliance-and-conditional-access/conditional-access-compliant-device.md` | Report-only result showed Success for compliant device |
| Managed noncompliant device test | `04-compliance-and-conditional-access/managed-noncompliant-device-test.md` | Report-only result showed Failure for noncompliant BYOD device |
| Conditional Access enforced mode test | `04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md` | Access was blocked for noncompliant BYOD device |

This section validates the full compliance and access-control flow:

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
| `05-application-deployment/company-portal-self-service-apps.md` | Optional / Planned |

Completed application deployment results:

| Lab | Result |
|---|---|
| Microsoft Store app deployment | Required and available Store apps validated |
| Win32 7-Zip app deployment | 7-Zip packaged as `.intunewin` and deployed |
| Microsoft 365 Apps deployment | Microsoft 365 Apps installed and validated after Autopilot |
| Android Managed Google Play app deployment | Outlook and Teams installed in Android Work profile |

---

### 06 - Endpoint Security

| File | Status |
|---|---|
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Completed |
| `06-endpoint-security/windows-firewall-policy.md` | Completed |
| `06-endpoint-security/bitlocker-encryption-policy.md` | Completed |
| `06-endpoint-security/attack-surface-reduction-policy.md` | Planned |
| `06-endpoint-security/windows-security-baseline.md` | Planned |

Completed endpoint security results:

| Lab | Result |
|---|---|
| Defender Antivirus policy | Success on WINAUTO452 |
| Windows Firewall policy | Success on WINAUTO452 |
| BitLocker encryption policy | Fully encrypted / Protection On |

Planned advanced endpoint security work:

- Attack Surface Reduction policy
- Windows Security Baseline

---

### 07 - Remote Actions and Monitoring

| File | Status |
|---|---|
| `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Planned |
| `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` | Planned |
| `07-remote-actions-and-monitoring/collect-diagnostics.md` | Planned |
| `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Planned |

This section will validate common Intune administrator actions such as device sync, restart, retire, wipe, diagnostics collection, and device monitoring reports.

---

### 08 - Troubleshooting

| File | Status |
|---|---|
| `08-troubleshooting/intune-enrollment-troubleshooting.md` | Planned |
| `08-troubleshooting/conditional-access-troubleshooting.md` | Recommended next |
| `08-troubleshooting/office-app-signin-troubleshooting.md` | Planned |
| `08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md` | Planned |

This section will document troubleshooting scenarios based on real lab behavior.

Recommended first troubleshooting lab:

```text
08-troubleshooting/conditional-access-troubleshooting.md
```

Reason:

- The Section 04 labs already produced report-only success, report-only failure, and enforced block examples.
- These are strong source scenarios for a practical Conditional Access troubleshooting document.

---

## Completed Hands-On Lab Sequence

The early hands-on sequence has now been completed and expanded into a larger endpoint management workflow.

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
| 11 | Deploy Windows configuration profiles | Completed |
| 12 | Deploy Microsoft Store apps | Completed |
| 13 | Deploy Win32 7-Zip app | Completed |
| 14 | Deploy Microsoft 365 Apps | Completed |
| 15 | Deploy Android Managed Google Play apps | Completed |
| 16 | Configure Defender Antivirus policy | Completed |
| 17 | Configure Windows Firewall policy | Completed |
| 18 | Configure BitLocker encryption policy | Completed |
| 19 | Create Windows basic compliance policy | Completed |
| 20 | Validate compliant device state | Completed |
| 21 | Create Conditional Access report-only policy | Completed |
| 22 | Validate report-only success for compliant device | Completed |
| 23 | Create managed noncompliant BYOD test | Completed |
| 24 | Validate report-only failure for noncompliant BYOD device | Completed |
| 25 | Create enforced Conditional Access policy | Completed |
| 26 | Validate access blocked for noncompliant BYOD device | Completed |

---

## Modern Endpoint Management Flow Completed So Far

The completed labs now demonstrate this practical Microsoft Intune and Microsoft Entra flow:

```text
Microsoft Entra users and groups
-> Intune license assignment
-> Device enrollment
-> Windows OOBE enrollment
-> Windows Autopilot provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> Configuration profiles
-> App deployment
-> Endpoint security policies
-> Compliance policy evaluation
-> Conditional Access report-only testing
-> Conditional Access enforced blocking
```

This is a strong MD-102 style project flow because it connects identity, device management, app deployment, security policy, compliance, and access control.

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
- BitLocker recovery keys
- Production company data
- Unsanitized screenshots

Screenshots should be stored in organized folders under:

```text
screenshots/sanitized/
```

Current screenshot folders include:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/endpoint-security/
screenshots/sanitized/compliance-and-conditional-access/
```

Future screenshot folders may include:

```text
screenshots/sanitized/remote-actions-and-monitoring/
screenshots/sanitized/troubleshooting/
```

---

## Current Status Summary

| Area | Status |
|---|---|
| Repository setup | Completed |
| Project overview | Completed |
| Identity and groups | Completed |
| Device enrollment | Mostly completed |
| Configuration profiles | Completed |
| Application deployment | Completed |
| Core endpoint security | Completed |
| Compliance and Conditional Access | Completed |
| iOS/iPadOS physical enrollment | Pending |
| Attack Surface Reduction | Planned |
| Windows Security Baseline | Planned |
| Remote actions and monitoring | Planned |
| Troubleshooting documentation | Planned |

---

## Recommended Next Step

Recommended next lab:

```text
08-troubleshooting/conditional-access-troubleshooting.md
```

Why this should be next:

- The Section 04 Conditional Access labs are completed.
- You already captured report-only success, report-only failure, and enforced failure evidence.
- This makes Conditional Access troubleshooting the most natural follow-up lab.

Alternative next lab:

```text
07-remote-actions-and-monitoring/device-sync-remote-actions.md
```

Why this is also a good next option:

- The lab now has multiple enrolled Windows devices.
- Device sync and remote actions are practical daily Intune admin tasks.
- This will strengthen the operational administration side of the project.

---

## Notes for Future Updates

Update this roadmap whenever a lab moves from Planned to Completed.

When a lab is completed, also update:

```text
README.md
00-project-overview/lab-implementation-roadmap.md
```

If screenshots are added, also confirm that the screenshot folder path is documented in both the lab file and the README.
