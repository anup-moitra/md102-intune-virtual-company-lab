# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap is updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration, application deployment, endpoint security, BYOD enrollment, monitoring, and troubleshooting labs.

---

## Current project status

The project has completed the foundation documentation, identity and group setup, Windows enrollment labs, Windows Autopilot user-driven enrollment, Windows BYOD enrollment, Android BYOD work profile enrollment, iOS/iPadOS enrollment admin prerequisites, application deployment labs, Windows configuration profile labs, and the first endpoint security policy labs.

Completed work:

- README created
- Company scenario documented
- Device inventory documented
- Lab implementation roadmap documented
- Microsoft Entra ID users and groups created
- user01 license assignment completed
- user03 license assignment verified for BYOD testing
- user04 license verified for iOS/iPadOS BYOD testing
- Automatic MDM enrollment reviewed for Windows enrollment and Autopilot
- Automatic MDM enrollment scoped for BYOD users using `GRP-BYOD-Users`
- Microsoft Entra device join settings reviewed
- Windows OOBE enrollment for `WIN-CORP-001` completed
- Windows Autopilot user-driven enrollment for `WINAUTO452` completed
- Windows BYOD enrollment for `WIN-BYOD-001` completed
- Android BYOD enrollment for `ANDROID-BYOD-001` completed
- Android Enterprise personally owned work profile created
- Android BYOD device verified as Intune managed, Personal, and Compliant
- Microsoft Authenticator deployed to the Android Work profile
- Android Managed Google Play app deployment completed
- Microsoft Outlook and Microsoft Teams installed in Android Work profile
- iOS/iPadOS admin prerequisites completed
- Apple MDM Push Certificate created and active in Intune
- Windows basic configuration profile completed
- Corporate wallpaper ADMX configuration profile completed
- USB storage block device restrictions profile completed
- Microsoft Store app deployment completed
- Win32 7-Zip app deployment completed
- Microsoft 365 Apps deployment completed
- Microsoft Defender Antivirus endpoint security policy completed
- Windows Firewall endpoint security policy completed
- BitLocker encryption endpoint security policy completed
- BitLocker encryption validated locally using `manage-bde -status`

Current focus:

- Continue endpoint security:
  - Attack Surface Reduction
  - Windows Security Baseline
- Complete iOS/iPadOS physical BYOD enrollment when a device is available
- Begin Compliance and Conditional Access labs after endpoint security/BYOD cleanup
- Keep roadmap, README, device inventory, and related lab files aligned after each completed lab

> [!NOTE]
> The project is not being completed strictly in folder order. Microsoft Store app deployment, Win32 app deployment, Microsoft 365 Apps deployment, Windows Autopilot, endpoint security, configuration profiles, Windows BYOD, Android BYOD, and Android app deployment were completed before some compliance, Conditional Access, iOS device enrollment, and remote action labs.

---

## Implementation phases

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
| Phase 8 | Configure/review automatic MDM enrollment | Completed / reviewed |
| Phase 9 | Enroll corporate Windows device WIN-CORP-001 | Completed |
| Phase 10 | Create Windows basic compliance policy | Planned |
| Phase 11 | Create Conditional Access policy in Report-only mode | Planned |
| Phase 12 | Test compliant corporate Windows sign-in | Planned |
| Phase 13 | Test unmanaged/BYOD sign-in behavior | Planned |
| Phase 14 | Create basic Windows configuration profile | Completed |
| Phase 14A | Create corporate wallpaper ADMX configuration profile | Completed |
| Phase 14B | Create USB storage block device restrictions profile | Completed |
| Phase 15 | Deploy Microsoft Store apps | Completed |
| Phase 16 | Deploy Win32 app using Intune | Completed |
| Phase 17 | Deploy Microsoft 365 Apps | Completed |
| Phase 18 | Configure Defender Antivirus policy | Completed |
| Phase 19 | Configure Windows Firewall policy | Completed |
| Phase 20 | Configure BitLocker encryption policy | Completed |
| Phase 21 | Configure Windows Autopilot | Completed |
| Phase 22 | Test Windows BYOD enrollment | Completed |
| Phase 23 | Test Android BYOD enrollment | Completed |
| Phase 23A | Deploy Android Managed Google Play apps | Completed |
| Phase 24 | Prepare iOS/iPadOS BYOD enrollment | In Progress / Admin prerequisites completed |
| Phase 24A | Complete physical iOS/iPadOS BYOD enrollment | Pending |
| Phase 25 | Configure Attack Surface Reduction policy | Next / Planned |
| Phase 26 | Configure Windows Security Baseline | Planned |
| Phase 27 | Test remote actions and monitoring | Planned |
| Phase 28 | Create troubleshooting documentation | Planned |

---

## Section roadmap

### 00 - Project Overview

| File | Status |
|---|---|
| README.md | Completed / Updated |
| 00-project-overview/company-scenario.md | Completed / Updated |
| 00-project-overview/device-inventory.md | Completed / Updated |
| 00-project-overview/lab-implementation-roadmap.md | Completed / Updated |

---

### 01 - Identity and Groups

| File | Status |
|---|---|
| 01-identity-and-groups/users-and-groups.md | Completed / Standardized |

---

### 02 - Device Enrollment

| File | Status |
|---|---|
| 02-device-enrollment/windows-oobe-enrollment.md | Completed |
| 02-device-enrollment/windows-autopilot-user-driven-enrollment.md | Completed / Standardized |
| 02-device-enrollment/windows-byod-enrollment.md | Completed / Standardized |
| 02-device-enrollment/android-byod-enrollment.md | Completed / Standardized |
| 02-device-enrollment/ios-byod-enrollment.md | In Progress / Admin prerequisites completed |

Completed enrollment results:

```text
WIN-CORP-001 = Enrolled and visible in Intune
WINAUTO452 = Autopilot enrolled, corporate-owned, and compliant
WIN-BYOD-001 = Enrolled as personal Windows BYOD device
ANDROID-BYOD-001 = Enrolled as Android Enterprise personally owned work profile device
IOS-BYOD-001 = Admin prerequisites completed, physical enrollment pending
```

---

### 03 - Configuration Profiles

| File | Status |
|---|---|
| 03-configuration-profiles/windows-basic-configuration-profile.md | Completed |
| 03-configuration-profiles/windows-corporate-wallpaper-policy.md | Completed / Standardized |
| 03-configuration-profiles/windows-device-restrictions-profile.md | Completed |

Observed configuration profile results:

```text
The Windows basic configuration profile was created and validated.
The corporate wallpaper was staged locally and applied successfully using an ADMX-backed user policy.
The USB storage block policy applied successfully and blocked removable drive access with an Access is denied message.
```

---

### 04 - Compliance and Conditional Access

| File | Status |
|---|---|
| 04-compliance-and-conditional-access/windows-basic-compliance-policy.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-compliant-device.md | Planned |
| 04-compliance-and-conditional-access/managed-noncompliant-device-test.md | Planned |
| 04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md | Planned |

Recommended sequence:

```text
Create basic Windows compliance policy
-> Validate compliant Windows device
-> Create Conditional Access policy in report-only mode
-> Test compliant device sign-in
-> Test noncompliant or unmanaged device behavior
-> Move from report-only to enforced mode after validation
```

---

### 05 - Application Deployment

| File | Status |
|---|---|
| 05-application-deployment/microsoft-store-app-deployment.md | Completed / Standardized |
| 05-application-deployment/win32-app-deployment-7zip.md | Completed / Standardized |
| 05-application-deployment/microsoft-365-apps-autopilot-deployment.md | Completed / Standardized |
| 05-application-deployment/android-managed-google-play-app-deployment.md | Completed / Standardized |
| 05-application-deployment/company-portal-self-service-apps.md | Optional / Planned |

Completed application deployment work:

```text
Microsoft Store apps
-> Win32 7-Zip app
-> Microsoft 365 Apps
-> Android Managed Google Play apps
```

Observed app deployment results:

```text
Required Microsoft Store apps installed automatically.
Available Microsoft Store apps appeared in Company Portal.
7-Zip was packaged as .intunewin and deployed through Intune.
Microsoft 365 Apps installed successfully and were validated after Autopilot.
Outlook and Teams installed inside the Android Work profile.
```

---

### 06 - Endpoint Security

| File | Status |
|---|---|
| 06-endpoint-security/windows-defender-antivirus-policy.md | Completed / Standardized |
| 06-endpoint-security/windows-firewall-policy.md | Completed / Standardized |
| 06-endpoint-security/bitlocker-encryption-policy.md | Completed / Standardized |
| 06-endpoint-security/attack-surface-reduction-policy.md | Next / Planned |
| 06-endpoint-security/windows-security-baseline.md | Planned |

Completed endpoint security work:

```text
Defender Antivirus
-> Windows Firewall
-> BitLocker encryption
```

Recommended next endpoint security sequence:

```text
Attack Surface Reduction
-> Windows Security Baseline
```

---

### 07 - Remote Actions and Monitoring

| File | Status |
|---|---|
| 07-remote-actions-and-monitoring/device-sync-remote-actions.md | Planned |
| 07-remote-actions-and-monitoring/restart-retire-wipe-actions.md | Planned |
| 07-remote-actions-and-monitoring/collect-diagnostics.md | Planned |
| 07-remote-actions-and-monitoring/device-monitoring-and-reports.md | Planned |

---

### 08 - Troubleshooting

| File | Status |
|---|---|
| 08-troubleshooting/intune-enrollment-troubleshooting.md | Planned |
| 08-troubleshooting/conditional-access-troubleshooting.md | Planned |
| 08-troubleshooting/office-app-signin-troubleshooting.md | Planned |
| 08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md | Planned |

---

## Completed hands-on lab sequence

| Step | Lab task | Status |
|---|---|---|
| 1 | Create Microsoft Entra ID lab users | Completed |
| 2 | Create Microsoft Entra ID security groups | Completed |
| 3 | Assign Intune licenses to test users | Completed |
| 4 | Configure/review automatic MDM enrollment | Completed / reviewed |
| 5 | Enroll WIN-CORP-001 through Windows OOBE | Completed |
| 6 | Deploy Microsoft Store apps | Completed |
| 7 | Package and deploy Win32 7-Zip | Completed |
| 8 | Deploy Microsoft 365 Apps | Completed |
| 9 | Configure Windows Autopilot | Completed |
| 10 | Complete Autopilot enrollment on WINAUTO452 | Completed |
| 11 | Create Microsoft Defender Antivirus policy | Completed |
| 12 | Create Windows Firewall policy | Completed |
| 13 | Create BitLocker encryption policy | Completed |
| 14 | Validate BitLocker with `manage-bde -status` | Completed |
| 15 | Enroll WIN-BYOD-001 as Windows BYOD device | Completed |
| 16 | Create Windows basic configuration profile | Completed |
| 17 | Create corporate wallpaper ADMX policy | Completed |
| 18 | Create USB storage block policy | Completed |
| 19 | Validate USB block endpoint result | Completed |
| 20 | Validate corporate wallpaper endpoint result | Completed |
| 21 | Connect Managed Google Play to Intune | Completed |
| 22 | Enroll ANDROID-BYOD-001 as Android work profile device | Completed |
| 23 | Deploy Microsoft Authenticator to Android Work profile | Completed |
| 24 | Deploy Outlook and Teams with Managed Google Play | Completed |
| 25 | Create Apple MDM Push Certificate for iOS/iPadOS enrollment | Completed |
| 26 | Upload and activate Apple MDM Push Certificate in Intune | Completed |
| 27 | Complete physical iOS/iPadOS enrollment | Pending |
| 28 | Configure Attack Surface Reduction policy in Audit mode | Next |

---

## Upcoming hands-on lab sequence

| Step | Lab task | Status |
|---|---|---|
| 1 | Configure Attack Surface Reduction policy in Audit mode | Next |
| 2 | Assign ASR policy to a pilot device group | Planned |
| 3 | Verify ASR policy reporting | Planned |
| 4 | Document ASR validation and screenshots | Planned |
| 5 | Continue to Windows Security Baseline lab | Planned |
| 6 | Complete physical iOS/iPadOS BYOD enrollment when device is available | Pending |
| 7 | Create Windows basic compliance policy | Planned |
| 8 | Create Conditional Access policy in report-only mode | Planned |
| 9 | Validate compliant and noncompliant access behavior | Planned |
| 10 | Start remote actions and monitoring labs | Planned |

---

## Documentation rules

Each completed lab file should follow a consistent structure:

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

## Screenshot rules

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
- Android IMEI numbers
- iOS serial numbers
- Phone numbers
- Internal IP addresses
- Production company data

Screenshots should be stored in:

```text
screenshots/sanitized/
```

Use subfolders for each lab area.

---

## Current status summary

| Area | Status |
|---|---|
| Repository created | Completed |
| README created | Completed / Updated |
| Company scenario created | Completed / Updated |
| Device inventory created | Completed / Updated |
| Lab roadmap created | Completed / Updated |
| Identity and groups lab | Completed / Standardized |
| Windows OOBE enrollment lab | Completed |
| Windows Autopilot enrollment lab | Completed / Standardized |
| Windows BYOD enrollment lab | Completed / Standardized |
| Android BYOD enrollment lab | Completed / Standardized |
| iOS/iPadOS BYOD enrollment lab | In Progress / Admin prerequisites completed |
| Configuration profile labs | Completed |
| Microsoft Store app deployment lab | Completed / Standardized |
| Win32 app deployment lab | Completed / Standardized |
| Microsoft 365 Apps deployment lab | Completed / Standardized |
| Android Managed Google Play app deployment lab | Completed / Standardized |
| Defender Antivirus endpoint security lab | Completed / Standardized |
| Windows Firewall endpoint security lab | Completed / Standardized |
| BitLocker encryption endpoint security lab | Completed / Standardized |
| Attack Surface Reduction policy lab | Next / Planned |
| Windows Security Baseline lab | Planned |
| Compliance and Conditional Access labs | Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting labs | Planned |

---

## Next step

Recommended next lab option 1:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Recommended next lab option 2:

```text
02-device-enrollment/ios-byod-enrollment.md
```

The iOS/iPadOS lab already has admin prerequisites completed. Physical device enrollment should be finished when a test iPhone/iPad is available.
