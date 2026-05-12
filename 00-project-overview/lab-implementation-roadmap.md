# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

---

## Purpose

The purpose of this roadmap is to keep the lab project organized as each section is created, tested, documented, and updated in GitHub.

This roadmap will be updated as the project progresses from initial documentation to hands-on Microsoft Intune configuration, application deployment, endpoint security, monitoring, and troubleshooting labs.

---

## Current Project Status

The project has completed the foundation documentation, the first identity lab, the first Windows device enrollment lab, Microsoft Store app deployment, Win32 7-Zip app deployment, Microsoft 365 Apps deployment, and Windows Autopilot user-driven enrollment.

Completed work:

- README created
- Company scenario documented
- Device inventory documented
- Lab implementation roadmap documented
- Microsoft Entra ID users and groups created
- user01 license assignment completed
- Automatic MDM enrollment reviewed for Windows enrollment and Autopilot
- Microsoft Entra device join settings reviewed
- Windows OOBE enrollment for WIN-CORP-001 completed
- Intune enrollment issue documented and resolved with manual MDM enrollment
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
- Windows Autopilot device group prepared
- Windows Autopilot deployment profile created and assigned
- Autopilot hardware hash imported into Intune
- Autopilot profile status verified as Assigned
- Autopilot OOBE sign-in completed by user01
- Autopilot device enrolled into Intune as a corporate device
- Autopilot device compliance verified as Compliant
- Required apps verified after Autopilot enrollment

Current focus:

- Continue to endpoint security labs:
  - Defender Antivirus
  - Windows Firewall
  - BitLocker
  - Attack Surface Reduction
  - Windows Security Baseline
- Continue updating GitHub documentation as screenshots and validation are completed
- Keep roadmap, README, device inventory, and related lab files aligned after each completed lab

> [!NOTE]
> The project is not being completed strictly in folder order. Microsoft Store app deployment, Win32 app deployment, Microsoft 365 Apps deployment, and Windows Autopilot were completed before some compliance, Conditional Access, configuration profile, and endpoint security labs. This roadmap reflects the actual hands-on progress.

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
| Phase 8 | Configure automatic MDM enrollment | Completed / reviewed during Autopilot |
| Phase 9 | Enroll corporate Windows device WIN-CORP-001 | Completed |
| Phase 10 | Create Windows basic compliance policy | Planned |
| Phase 11 | Create Conditional Access policy in Report-only mode | Planned |
| Phase 12 | Test compliant corporate Windows sign-in | Planned |
| Phase 13 | Test unmanaged BYOD sign-in | Planned |
| Phase 14 | Create basic Windows configuration profile | Planned |
| Phase 15 | Deploy Microsoft Store apps | Completed |
| Phase 16 | Deploy Win32 app using Intune | Completed |
| Phase 17 | Deploy Microsoft 365 Apps | Completed |
| Phase 18 | Configure Defender Antivirus policy | Next |
| Phase 19 | Configure Windows Firewall policy | Planned |
| Phase 20 | Configure BitLocker encryption policy | Planned |
| Phase 21 | Configure Windows Autopilot | Completed |
| Phase 22 | Test Windows BYOD enrollment | Planned |
| Phase 23 | Test Android BYOD enrollment | Planned |
| Phase 24 | Test iOS BYOD enrollment | Planned |
| Phase 25 | Configure Attack Surface Reduction policy | Planned |
| Phase 26 | Configure Windows Security Baseline | Planned |
| Phase 27 | Test remote actions and monitoring | Planned |
| Phase 28 | Create troubleshooting documentation | Planned |

> [!NOTE]
> Phase 8 is marked as completed/reviewed because automatic MDM enrollment was reviewed again during Windows Autopilot preparation. The earlier Windows OOBE enrollment issue remains documented in the Windows OOBE enrollment lab as a troubleshooting scenario.

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
- Pilot group usage for app deployment and Autopilot targeting

### 02 - Device Enrollment

| File | Status |
|---|---|
| 02-device-enrollment/windows-oobe-enrollment.md | Completed |
| 02-device-enrollment/windows-autopilot-user-driven-enrollment.md | Completed |
| 02-device-enrollment/windows-byod-enrollment.md | Planned |
| 02-device-enrollment/android-byod-enrollment.md | Planned |
| 02-device-enrollment/ios-byod-enrollment.md | Planned |

This section documents Windows corporate enrollment, Windows Autopilot, and BYOD enrollment scenarios.

The Windows OOBE enrollment lab is completed for:

```text
WIN-CORP-001
```

The lab also documents the troubleshooting path where the device initially showed `MDM: None` in Microsoft Entra ID and was later enrolled into Intune using manual MDM enrollment.

The Windows Autopilot user-driven enrollment lab is completed for:

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
| 05-application-deployment/win32-app-deployment-7zip.md | Completed |
| 05-application-deployment/microsoft-365-apps-autopilot-deployment.md | Completed |
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

#### Next application deployment work

The next optional application deployment lab is:

```text
05-application-deployment/company-portal-self-service-apps.md
```

This lab can further document the Company Portal user self-service app experience.

### 06 - Endpoint Security

| File | Status |
|---|---|
| 06-endpoint-security/windows-defender-antivirus-policy.md | Next |
| 06-endpoint-security/windows-firewall-policy.md | Planned |
| 06-endpoint-security/bitlocker-encryption-policy.md | Planned |
| 06-endpoint-security/attack-surface-reduction-policy.md | Planned |
| 06-endpoint-security/windows-security-baseline.md | Planned |

This section will document Microsoft Defender, Firewall, BitLocker, Attack Surface Reduction, and Security Baseline labs.

Recommended endpoint security sequence:

```text
Defender Antivirus
-> Windows Firewall
-> BitLocker encryption
-> Attack Surface Reduction
-> Windows Security Baseline
```

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
| 31 | Verify Autopilot device in Intune as corporate/compliant | Completed |
| 32 | Verify required apps installed after Autopilot | Completed |
| 33 | Update Autopilot documentation with screenshots | Completed |

---

## Upcoming Hands-On Lab Sequence

| Step | Lab Task | Status |
|---|---|---|
| 1 | Prepare Defender Antivirus policy lab | Next |
| 2 | Create Defender Antivirus policy in Intune | Planned |
| 3 | Assign Defender Antivirus policy to pilot users/devices | Planned |
| 4 | Verify policy status from Intune | Planned |
| 5 | Verify policy effect on Windows endpoint | Planned |
| 6 | Capture sanitized screenshots | Planned |
| 7 | Update GitHub documentation | Planned |
| 8 | Continue to Windows Firewall policy lab | Planned |
| 9 | Continue to BitLocker encryption policy lab | Planned |
| 10 | Continue to Attack Surface Reduction policy lab | Planned |
| 11 | Continue to Windows Security Baseline lab | Planned |

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
screenshots/sanitized/endpoint-security/
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
| Win32 app deployment lab | Completed |
| Microsoft 365 Apps deployment lab | Completed |
| Autopilot enrollment lab | Completed |
| Compliance and Conditional Access labs | Planned |
| Configuration profile labs | Planned |
| Endpoint security labs | Next |
| Remote actions and monitoring labs | Planned |
| Troubleshooting labs | Planned |

---

## Next Step

Continue to endpoint security policy labs.

Recommended next lab:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Recommended endpoint security sequence:

```text
Defender Antivirus
-> Windows Firewall
-> BitLocker
-> Attack Surface Reduction
-> Windows Security Baseline
```

Alternative planning focus:

```text
Attack Surface Reduction / Security Baseline planning
```
