# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap is updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration, application deployment, endpoint security, BYOD enrollment, monitoring, and troubleshooting labs.

---

## Current project status

The project has completed the foundation documentation, identity and group setup, Windows enrollment labs, Windows Autopilot user-driven enrollment, Windows BYOD enrollment, Android BYOD work profile enrollment, application deployment labs, Windows configuration profile labs, and the first endpoint security policy labs.

Completed work:

- README created
- Company scenario documented
- Device inventory documented
- Lab implementation roadmap documented
- Microsoft Entra ID users and groups created
- user01 license assignment completed
- user03 license assignment verified for BYOD testing
- Automatic MDM enrollment reviewed for Windows enrollment and Autopilot
- Automatic MDM enrollment scoped for BYOD users using `GRP-BYOD-Users`
- Microsoft Entra device join settings reviewed
- Windows OOBE enrollment for `WIN-CORP-001` completed
- Intune enrollment issue documented and resolved with manual MDM enrollment
- Windows Autopilot device group prepared
- Windows Autopilot deployment profile created and assigned
- Autopilot hardware hash imported into Intune
- Autopilot profile status verified as Assigned
- Autopilot OOBE sign-in completed by user01
- Autopilot device enrolled into Intune as a corporate device
- Autopilot device compliance verified as Compliant
- Required apps verified after Autopilot enrollment
- Windows BYOD enrollment for `WIN-BYOD-001` completed
- Windows BYOD device verified as Intune managed, Personal, and Compliant
- Android BYOD enrollment for `ANDROID-BYOD-001` completed
- Android Enterprise personally owned work profile created
- Android BYOD device verified as Intune managed, Personal, and Compliant
- Microsoft Authenticator deployed to the Android Work profile
- Windows basic configuration profile completed
- Corporate wallpaper ADMX configuration profile completed
- Corporate wallpaper staged locally with a PowerShell platform script
- Corporate wallpaper validated successfully on `WINAUTO452`
- USB storage block device restrictions profile completed
- USB/removable storage access denied result validated on `WINAUTO452`
- Microsoft Store app deployment completed
- Required Microsoft Store apps verified in Company Portal
- Available Microsoft Store apps verified in Company Portal
- Win32 7-Zip app deployment completed
- 7-Zip packaged as `.intunewin`
- 7-Zip uploaded to Intune as a Windows app (Win32)
- 7-Zip assigned as Required to `GRP-Pilot-Users`
- 7-Zip install status verified in Intune
- Microsoft 365 Apps deployment completed
- Microsoft 365 Apps assigned as Required to `GRP-Pilot-Users`
- Microsoft 365 Apps install status verified as Installed
- Microsoft Defender Antivirus endpoint security policy completed
- Windows Firewall endpoint security policy completed
- BitLocker encryption endpoint security policy completed
- BitLocker encryption validated locally using `manage-bde -status`

Current focus:

- Continue remaining endpoint security labs:
  - Attack Surface Reduction
  - Windows Security Baseline
- Continue remaining BYOD enrollment lab:
  - iOS BYOD enrollment
- Begin Compliance and Conditional Access labs after endpoint security/BYOD cleanup
- Continue updating GitHub documentation as screenshots and validation are completed
- Keep roadmap, README, device inventory, and related lab files aligned after each completed lab

> [!NOTE]
> The project is not being completed strictly in folder order. Microsoft Store app deployment, Win32 app deployment, Microsoft 365 Apps deployment, Windows Autopilot, endpoint security, configuration profiles, Windows BYOD, and Android BYOD were completed before some compliance, Conditional Access, iOS BYOD, and remote action labs. This roadmap reflects the actual hands-on progress.

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
| Phase 24 | Test iOS BYOD enrollment | Planned |
| Phase 25 | Configure Attack Surface Reduction policy | Next / Planned |
| Phase 26 | Configure Windows Security Baseline | Planned |
| Phase 27 | Test remote actions and monitoring | Planned |
| Phase 28 | Create troubleshooting documentation | Planned |

> [!NOTE]
> Phase 8 is marked as completed/reviewed because automatic MDM enrollment was reviewed during Windows OOBE enrollment, Windows Autopilot preparation, Windows BYOD enrollment, and Android BYOD preparation. The earlier Windows OOBE enrollment issue remains documented in the Windows OOBE enrollment lab as a troubleshooting scenario.

---

## Section roadmap

### 00 - Project Overview

| File | Status |
|---|---|
| README.md | Completed / Updated |
| 00-project-overview/company-scenario.md | Completed / Updated |
| 00-project-overview/device-inventory.md | Completed / Updated |
| 00-project-overview/lab-implementation-roadmap.md | Completed / Updated |

This section documents:

- Overall project purpose
- Virtual company scenario
- Device inventory
- Lab implementation roadmap
- Current progress
- Planned next labs

---

### 01 - Identity and Groups

| File | Status |
|---|---|
| 01-identity-and-groups/users-and-groups.md | Completed / Standardized |

This section documents:

- Lab admin account
- Standard test users
- Pilot users
- BYOD users
- Microsoft Entra ID security groups
- Group assignment strategy
- License assignment plan
- Screenshots for identity setup
- Pilot group usage for app deployment and policy targeting
- BYOD group usage for Windows and Android BYOD enrollment
- Autopilot device group usage for device-based policy targeting

---

### 02 - Device Enrollment

| File | Status |
|---|---|
| 02-device-enrollment/windows-oobe-enrollment.md | Completed |
| 02-device-enrollment/windows-autopilot-user-driven-enrollment.md | Completed / Standardized |
| 02-device-enrollment/windows-byod-enrollment.md | Completed / Standardized |
| 02-device-enrollment/android-byod-enrollment.md | Completed / Standardized |
| 02-device-enrollment/ios-byod-enrollment.md | Planned |

This section documents Windows corporate enrollment, Windows Autopilot, and BYOD enrollment scenarios.

#### Windows OOBE enrollment

Completed for:

```text
WIN-CORP-001
```

The lab documents the troubleshooting path where the device initially showed `MDM: None` in Microsoft Entra ID and was later enrolled into Intune using manual MDM enrollment.

#### Windows Autopilot user-driven enrollment

Completed for:

```text
WINAUTO452
```

Observed Autopilot result:

```text
Autopilot device enrolled successfully, appeared in Intune as corporate-owned, and reported compliant.
```

Autopilot validation included:

- Automatic MDM enrollment review
- Microsoft Entra join settings review
- Autopilot device group preparation
- Hardware hash collection and import
- Deployment profile creation
- OOBE settings configuration
- Deployment profile assignment
- Profile status verified as Assigned
- OOBE sign-in with user01
- Microsoft Entra join
- Intune enrollment
- Corporate ownership validation
- Compliance validation
- App deployment validation after enrollment

#### Windows BYOD enrollment

Completed for:

```text
WIN-BYOD-001
```

Observed Windows BYOD result:

```text
WIN-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Windows BYOD device.
The device appeared as managed by Intune, ownership Personal, compliance Compliant, and primary user user03.
```

Windows BYOD validation included:

- user03 license assignment check
- user03 BYOD group membership check
- Automatic MDM enrollment scope review
- Windows personally owned device enrollment restriction check
- `WIN-BYOD-001` device preparation
- Windows work or school account connection
- MDM enrollment from Windows Settings
- Manual device sync
- Intune Windows device list verification
- Intune device overview verification

#### Android BYOD enrollment

Completed for:

```text
ANDROID-BYOD-001
```

Observed Android BYOD result:

```text
ANDROID-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Android Enterprise work profile device.
The device appeared as Personal, Intune managed, and Compliant.
Microsoft Authenticator installed successfully inside the Android Work profile.
```

Android BYOD validation included:

- Managed Google Play connected to Intune
- Android Enterprise personally owned work profile enrollment allowed
- Android device enrolled through Company Portal
- Work profile created
- Android device visible in Intune
- Ownership verified as Personal
- Compliance verified as Compliant
- Microsoft Authenticator assigned as Required
- Microsoft Authenticator installed inside the Work profile

---

### 03 - Configuration Profiles

| File | Status |
|---|---|
| 03-configuration-profiles/windows-basic-configuration-profile.md | Completed |
| 03-configuration-profiles/windows-corporate-wallpaper-policy.md | Completed / Standardized |
| 03-configuration-profiles/windows-device-restrictions-profile.md | Completed |

This section documents Windows configuration settings pushed by Microsoft Intune.

Completed configuration profile work:

```text
Windows basic configuration profile
-> Corporate wallpaper ADMX policy
-> USB storage block device restrictions policy
```

Configuration profile validation included:

- Settings Catalog profile creation
- Assignment to pilot groups
- Device sync and policy reporting
- ADMX-backed Desktop Wallpaper user policy
- PowerShell platform script for wallpaper staging
- USB/removable storage access restriction
- Endpoint validation screenshots

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

This section will document device compliance and access control testing.

Recommended compliance and Conditional Access sequence:

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
| 05-application-deployment/company-portal-self-service-apps.md | Optional / Planned |

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

Win32 app deployment has also been completed and documented.

Win32 app tested:

```text
7-Zip
```

Observed result:

```text
7-Zip was packaged as .intunewin, uploaded to Intune, assigned as Required, and verified through Intune install status.
```

Microsoft 365 Apps deployment has also been completed and documented.

Microsoft 365 Apps result:

```text
Microsoft 365 Apps for Windows 10 and later was assigned as Required and verified as Installed.
```

Post-Autopilot app validation also confirmed that required apps were installed after the Autopilot-enrolled device completed provisioning.

---

### 06 - Endpoint Security

| File | Status |
|---|---|
| 06-endpoint-security/windows-defender-antivirus-policy.md | Completed / Standardized |
| 06-endpoint-security/windows-firewall-policy.md | Completed / Standardized |
| 06-endpoint-security/bitlocker-encryption-policy.md | Completed / Standardized |
| 06-endpoint-security/attack-surface-reduction-policy.md | Next / Planned |
| 06-endpoint-security/windows-security-baseline.md | Planned |

This section documents Microsoft Defender Antivirus, Windows Firewall, BitLocker, Attack Surface Reduction, and Security Baseline labs.

Completed endpoint security work:

```text
Defender Antivirus
-> Windows Firewall
-> BitLocker encryption
```

Observed endpoint security results:

```text
Defender Antivirus policy reported Success on WINAUTO452.
Windows Firewall policy reported Success on WINAUTO452.
BitLocker policy reported Success on WINAUTO452.
Local BitLocker status showed Fully Encrypted, 100.0% encrypted, and Protection On.
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

This section will document device sync, restart, retire, wipe, diagnostics collection, monitoring, and reports.

Recommended sequence:

```text
Device sync remote action
-> Restart remote action
-> Retire vs wipe comparison
-> Collect diagnostics
-> Device monitoring and reports
```

---

### 08 - Troubleshooting

| File | Status |
|---|---|
| 08-troubleshooting/intune-enrollment-troubleshooting.md | Planned |
| 08-troubleshooting/conditional-access-troubleshooting.md | Planned |
| 08-troubleshooting/office-app-signin-troubleshooting.md | Planned |
| 08-troubleshooting/autopilot-motherboard-replacement-troubleshooting.md | Planned |

This section will document repeatable troubleshooting checklists and realistic support scenarios.

Recommended troubleshooting topics:

```text
Windows enrollment troubleshooting
Autopilot profile assignment troubleshooting
App deployment troubleshooting
Compliance troubleshooting
Conditional Access troubleshooting
Office app sign-in troubleshooting
BitLocker recovery key troubleshooting
Autopilot motherboard replacement troubleshooting
```

---

## Completed hands-on lab sequence

| Step | Lab task | Status |
|---|---|---|
| 1 | Create Microsoft Entra ID lab users | Completed |
| 2 | Create Microsoft Entra ID security groups | Completed |
| 3 | Assign Intune licenses to test users | Completed |
| 4 | Configure/review automatic MDM enrollment | Completed / reviewed |
| 5 | Enroll WIN-CORP-001 through Windows OOBE | Completed |
| 6 | Confirm WIN-CORP-001 appears in Intune | Completed |
| 7 | Deploy Microsoft Store apps | Completed |
| 8 | Verify required apps installed | Completed |
| 9 | Verify available apps in Company Portal | Completed |
| 10 | Prepare 7-Zip installer source folder | Completed |
| 11 | Package 7-Zip as `.intunewin` | Completed |
| 12 | Upload Win32 app to Intune | Completed |
| 13 | Configure install and uninstall commands | Completed |
| 14 | Configure detection rule | Completed |
| 15 | Assign 7-Zip to `GRP-Pilot-Users` | Completed |
| 16 | Verify 7-Zip install status in Intune | Completed |
| 17 | Capture sanitized screenshots for Win32 app deployment | Completed |
| 18 | Update GitHub documentation for Win32 app deployment | Completed |
| 19 | Confirm Microsoft 365 Apps license availability for user01 | Completed |
| 20 | Create Microsoft 365 Apps deployment in Intune | Completed |
| 21 | Configure Microsoft 365 Apps with XML | Completed |
| 22 | Assign Microsoft 365 Apps as Required to `GRP-Pilot-Users` | Completed |
| 23 | Verify Microsoft 365 Apps install status | Completed |
| 24 | Prepare Autopilot device group | Completed |
| 25 | Collect Autopilot hardware hash | Completed |
| 26 | Import Autopilot hardware hash CSV into Intune | Completed |
| 27 | Create Autopilot user-driven deployment profile | Completed |
| 28 | Assign Autopilot deployment profile | Completed |
| 29 | Verify Autopilot profile status as Assigned | Completed |
| 30 | Complete Autopilot OOBE sign-in with user01 | Completed |
| 31 | Verify Autopilot device in Intune as Corporate and Compliant | Completed |
| 32 | Verify required apps installed after Autopilot | Completed |
| 33 | Update Autopilot documentation with screenshots | Completed |
| 34 | Create Microsoft Defender Antivirus endpoint security policy | Completed |
| 35 | Assign Defender Antivirus policy to `GRP-Autopilot-Devices` | Completed |
| 36 | Verify Defender Antivirus policy status on `WINAUTO452` | Completed |
| 37 | Create Windows Firewall endpoint security policy | Completed |
| 38 | Assign Windows Firewall policy to `GRP-Autopilot-Devices` | Completed |
| 39 | Verify Windows Firewall policy status on `WINAUTO452` | Completed |
| 40 | Create BitLocker encryption policy | Completed |
| 41 | Assign BitLocker policy to `GRP-Autopilot-Devices` | Completed |
| 42 | Verify BitLocker policy status on `WINAUTO452` | Completed |
| 43 | Verify local BitLocker encryption with `manage-bde -status` | Completed |
| 44 | Prepare Windows BYOD user and group targeting | Completed |
| 45 | Configure MDM user scope for `GRP-BYOD-Users` | Completed |
| 46 | Confirm Windows personally owned enrollment is allowed | Completed |
| 47 | Enroll `WIN-BYOD-001` using Windows MDM enrollment | Completed |
| 48 | Perform manual sync from Windows Settings | Completed |
| 49 | Verify `WIN-BYOD-001` in Intune as Personal, Compliant, and managed by Intune | Completed |
| 50 | Update Windows BYOD documentation with screenshots | Completed |
| 51 | Create Windows basic configuration profile | Completed |
| 52 | Create corporate wallpaper ADMX policy | Completed |
| 53 | Create USB storage block policy | Completed |
| 54 | Validate USB block endpoint result | Completed |
| 55 | Validate corporate wallpaper endpoint result | Completed |
| 56 | Update configuration profile documentation with screenshots | Completed |
| 57 | Connect Managed Google Play to Intune | Completed |
| 58 | Confirm Android Enterprise personally owned work profile enrollment is allowed | Completed |
| 59 | Enroll `ANDROID-BYOD-001` using Company Portal | Completed |
| 60 | Verify Android Work profile creation | Completed |
| 61 | Verify Android BYOD device in Intune | Completed |
| 62 | Assign Microsoft Authenticator as Required to `GRP-BYOD-Users` | Completed |
| 63 | Confirm Microsoft Authenticator installed in the Android Work profile | Completed |
| 64 | Update Android BYOD documentation with screenshots | Completed |

---

## Upcoming hands-on lab sequence

| Step | Lab task | Status |
|---|---|---|
| 1 | Configure Attack Surface Reduction policy in Audit mode | Next |
| 2 | Assign ASR policy to a pilot device group | Planned |
| 3 | Verify ASR policy reporting | Planned |
| 4 | Document ASR validation and screenshots | Planned |
| 5 | Continue to Windows Security Baseline lab | Planned |
| 6 | Prepare iOS BYOD enrollment lab | Planned |
| 7 | Complete iOS BYOD enrollment and validation | Planned |
| 8 | Create Windows basic compliance policy | Planned |
| 9 | Create Conditional Access policy in report-only mode | Planned |
| 10 | Validate compliant and noncompliant access behavior | Planned |
| 11 | Start remote actions and monitoring labs | Planned |

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

This makes the repository easier to read and easier to present as a portfolio project.

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
- Phone numbers
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
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/endpoint-security/
```

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
| iOS BYOD enrollment lab | Planned |
| Configuration profile labs | Completed |
| Microsoft Store app deployment lab | Completed / Standardized |
| Win32 app deployment lab | Completed / Standardized |
| Microsoft 365 Apps deployment lab | Completed / Standardized |
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

Recommended sequence if continuing endpoint security:

```text
Attack Surface Reduction policy
-> Windows Security Baseline
-> Remote actions and monitoring
```

Recommended sequence if continuing BYOD:

```text
iOS BYOD enrollment
-> BYOD compliance policy testing
-> Conditional Access BYOD testing
```
