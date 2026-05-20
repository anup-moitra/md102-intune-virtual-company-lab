# Company Scenario

This file describes the virtual company used throughout this MD-102 hands-on lab project.

---

## Company name

```text
Contoso Startup Lab
```

---

## Company overview

Contoso Startup Lab is a fictional small business used for Microsoft Intune and MD-102 hands-on practice.

The company represents a modern cloud-managed workplace that uses:

- Microsoft Entra ID for identity and access management
- Microsoft Intune for endpoint and app management
- Windows Autopilot for corporate Windows provisioning
- Company Portal for user app experience
- Managed Google Play for Android Enterprise BYOD app deployment
- Apple MDM Push Certificate for iOS/iPadOS enrollment preparation
- Endpoint security policies for device protection
- Compliance policies for device health validation
- Conditional Access for identity and device-based access control
- Remote actions and monitoring for operational device management
- Troubleshooting documentation for real-world issue resolution

This lab environment simulates common endpoint administration tasks such as:

- User and group management
- Device enrollment
- Windows Autopilot provisioning
- BYOD enrollment
- Configuration profiles
- Application deployment
- Endpoint security
- Attack Surface Reduction policy deployment
- Windows Security Baseline deployment and troubleshooting
- Compliance policy deployment
- Conditional Access report-only validation
- Conditional Access enforced mode testing
- Remote actions and monitoring
- Troubleshooting documentation

---

## Company size

Contoso Startup Lab has approximately 15 users.

The lab includes:

- A lab administrator account
- Standard test users
- Pilot users
- Corporate Windows devices
- Personally owned Windows BYOD devices
- Personally owned Android BYOD devices
- iOS/iPadOS BYOD enrollment preparation

---

## Business scenario

Contoso Startup Lab wants to manage corporate and personal devices securely while allowing users to access Microsoft 365 resources.

The company wants to support:

- Corporate Windows laptops
- Windows Autopilot for new corporate device provisioning
- Personal Windows BYOD enrollment
- Android Enterprise personally owned work profile enrollment
- iOS/iPadOS BYOD enrollment
- Required business app deployment
- Optional self-service app deployment through Company Portal
- Managed Google Play app deployment to Android Work profiles
- Endpoint security policies for corporate Windows devices
- Attack Surface Reduction Rules in Audit mode for safe pilot testing
- Windows Security Baseline for Microsoft-recommended endpoint hardening
- Device compliance validation using Microsoft Intune
- Conditional Access report-only testing before enforcement
- Conditional Access enforced blocking for noncompliant devices
- Remote actions including sync, restart, retire, wipe, and collect diagnostics
- Device monitoring and reporting
- Troubleshooting documentation

---

## Device environment

| Device type | Ownership | Platform | Purpose |
|---|---|---|---|
| Corporate laptops | Company-owned | Windows 11 | Managed endpoint testing |
| Autopilot laptops | Company-owned | Windows 11 | Autopilot provisioning, compliance, app deployment, and endpoint security validation |
| BYOD laptops | Personally owned | Windows 11 | Windows BYOD enrollment, compliance, and Conditional Access testing |
| BYOD mobile devices | Personally owned | Android Enterprise | Android work profile testing |
| BYOD mobile devices | Personally owned | iOS/iPadOS | iOS BYOD enrollment testing |

---

## Lab devices

| Device name | Device type | Ownership | Operating system | Current use / result |
|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Personal in Intune after manual MDM enrollment | Windows 11 | OOBE enrollment, Intune management, compliance visibility, app deployment testing, and Wipe remote action |
| WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot enrollment, configuration profiles, app deployment, endpoint security validation, compliance, Conditional Access testing, and remote actions |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows BYOD enrollment; initially compliant, intentionally marked noncompliant for Conditional Access enforced blocking test |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android 15 | Android Enterprise personally owned work profile enrollment and Managed Google Play app deployment |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS/iPadOS | Admin prerequisites completed; physical enrollment pending |

---

## Identity environment

Contoso Startup Lab uses Microsoft Entra ID for cloud identity and access management.

The lab identity setup includes:

- Lab administrator account
- Standard test users
- Pilot user group
- Windows user group
- BYOD user group
- Mobile user group
- IT admin group
- Autopilot device group

---

## Lab users

| User type | Example account | Purpose |
|---|---|---|
| Lab administrator | admin01 | Tenant and Intune administration |
| Main pilot user | user01 | Primary Windows, Autopilot, app, compliance, and policy test user |
| Windows test user | user02 | Additional Windows policy testing |
| BYOD test user | user03 | Windows BYOD, Android BYOD, compliance, and Conditional Access testing |
| iOS BYOD test user | user04 | iOS/iPadOS BYOD enrollment preparation |
| Policy test user | user05 | Additional policy testing |

---

## Lab groups

| Group name | Purpose |
|---|---|
| GRP-All-Lab-Users | General lab targeting |
| GRP-Pilot-Users | Pilot testing and user-based assignments |
| GRP-Windows-Users | Windows user targeting |
| GRP-BYOD-Users | BYOD enrollment, BYOD app targeting, and Conditional Access testing |
| GRP-Mobile-Users | Mobile device/user targeting |
| GRP-IT-Admins | Lab admin targeting |
| GRP-Autopilot-Devices | Autopilot device and device-based policy targeting |

---

## Management goals

This lab project demonstrates how an endpoint administrator manages a small cloud-first company environment from zero.

The main goals are to:

- Create Microsoft Entra ID users and groups
- Assign Intune and Microsoft 365 licenses
- Configure automatic MDM enrollment
- Enroll corporate Windows devices into Intune
- Configure Windows Autopilot for corporate device provisioning
- Enroll and compare BYOD devices
- Deploy Microsoft Store apps
- Deploy Win32 apps
- Deploy Microsoft 365 Apps
- Deploy Android Managed Google Play apps
- Create Windows configuration profiles
- Deploy corporate wallpaper with an ADMX-backed policy
- Block USB removable storage through Intune policy
- Configure Microsoft Defender Antivirus policy
- Configure Windows Firewall policy
- Configure BitLocker disk encryption policy
- Configure Attack Surface Reduction policy in Audit mode
- Deploy and troubleshoot a Windows Security Baseline
- Create Windows compliance policies
- Remediate compliance failures such as Secure Boot
- Test Conditional Access in report-only mode
- Test managed noncompliant BYOD access behavior
- Test Conditional Access enforced blocking for noncompliant devices
- Use remote actions including sync, restart, retire, wipe, and collect diagnostics
- Review Intune monitoring and reporting
- Document real troubleshooting case studies

---

## Completed lab progress

All major labs are completed:

- Project README
- Company scenario
- Device inventory
- Lab implementation roadmap
- Microsoft Entra ID users and groups
- user01 license assignment
- Windows OOBE enrollment for WIN-CORP-001
- Windows Autopilot user-driven enrollment for WINAUTO452
- Windows BYOD enrollment for WIN-BYOD-001
- Android BYOD work profile enrollment for ANDROID-BYOD-001
- iOS/iPadOS BYOD admin prerequisites
- Microsoft Store app deployment
- Win32 7-Zip app deployment
- Microsoft 365 Apps deployment
- Android Managed Google Play app deployment
- Windows basic configuration profile
- Corporate wallpaper ADMX configuration profile
- USB storage block device restrictions profile
- Microsoft Defender Antivirus endpoint security policy
- Windows Firewall endpoint security policy
- BitLocker encryption endpoint security policy
- Attack Surface Reduction policy in Audit mode
- Windows Security Baseline deployment and troubleshooting
- Windows basic compliance policy
- Conditional Access compliant-device report-only test
- Managed noncompliant BYOD test
- Conditional Access enforced mode test
- Device sync remote action
- Restart, Retire, and Wipe remote actions
- Collect diagnostics remote action
- Device monitoring and reports
- Intune enrollment troubleshooting case study
- Configuration policy conflict troubleshooting case study
- Remote actions diagnostics troubleshooting case study
- Troubleshooting summary

---

## Completed device outcomes

### WIN-CORP-001

```text
Windows OOBE enrollment completed
Device appeared in Intune
Device showed Intune management
Device used for early app deployment testing
Wipe remote action performed and confirmed
Device record no longer accessible after Wipe
```

### WINAUTO452

```text
Windows Autopilot user-driven enrollment completed
Device appeared as corporate-owned in Intune
Required apps installed after Autopilot enrollment
Corporate wallpaper applied
USB storage access blocked
Defender Antivirus policy applied
Windows Firewall policy applied
BitLocker encryption enabled
Attack Surface Reduction rules deployed in Audit mode
ASR rule configuration validated via PowerShell
Windows Security Baseline deployed
Security Baseline conflicts and VBS error identified and remediated
Windows Security Baseline final status showed Success
Windows compliance policy applied
Secure Boot remediation completed
Device reported compliant in Intune
Conditional Access report-only compliant-device test succeeded
Device sync remote action executed and verified
Restart remote action executed and confirmed
Retire remote action executed and confirmed
Collect diagnostics remote action executed and confirmed
Device used as primary monitoring and reporting reference device
```

### WIN-BYOD-001

```text
Windows BYOD enrollment completed
Device appeared in Intune
Ownership showed Personal
Primary user showed user03
Initial compliance showed Compliant
Temporary compliance policy intentionally marked the device Noncompliant
Conditional Access report-only test showed Failure for the noncompliant device
Conditional Access enforced mode blocked Microsoft 365 access because the device was noncompliant
```

### ANDROID-BYOD-001

```text
Android Enterprise personally owned work profile enrollment completed
Device appeared in Intune
Ownership showed Personal
Compliance showed Compliant
Microsoft Authenticator installed in the Work profile
Microsoft Outlook and Microsoft Teams installed in the Work profile
```

### IOS-BYOD-001

```text
iOS/iPadOS BYOD admin prerequisites completed
Apple MDM Push Certificate created and active
Physical iPhone/iPad enrollment pending
```

---

## Application deployment progress

| App deployment type | Lab file | Result |
|---|---|---|
| Microsoft Store app deployment | `05-application-deployment/microsoft-store-app-deployment.md` | Completed |
| Win32 app deployment | `05-application-deployment/win32-app-deployment-7zip.md` | Completed |
| Microsoft 365 Apps deployment | `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Completed |
| Android Managed Google Play app deployment | `05-application-deployment/android-managed-google-play-app-deployment.md` | Completed |

Observed results:

```text
Required Microsoft Store apps installed automatically.
Available Microsoft Store apps appeared in Company Portal.
7-Zip was packaged as .intunewin and deployed through Intune.
Microsoft 365 Apps installed successfully through Intune.
Outlook and Teams installed inside the Android Work profile through Managed Google Play.
```

---

## Configuration profile progress

| Configuration profile | Lab file | Result |
|---|---|---|
| Windows basic configuration profile | `03-configuration-profiles/windows-basic-configuration-profile.md` | Completed |
| Corporate wallpaper ADMX policy | `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Completed |
| USB storage block policy | `03-configuration-profiles/windows-device-restrictions-profile.md` | Completed |

---

## Endpoint security progress

| Endpoint security policy | Lab file | Result |
|---|---|---|
| Microsoft Defender Antivirus policy | `06-endpoint-security/windows-defender-antivirus-policy.md` | Completed |
| Windows Firewall policy | `06-endpoint-security/windows-firewall-policy.md` | Completed |
| BitLocker encryption policy | `06-endpoint-security/bitlocker-encryption-policy.md` | Completed |
| Attack Surface Reduction policy | `06-endpoint-security/attack-surface-reduction-policy.md` | Completed |
| Windows Security Baseline | `06-endpoint-security/windows-security-baseline.md` | Completed |

---

## Compliance and Conditional Access progress

| Lab | Result |
|---|---|
| Windows basic compliance policy | Completed |
| Conditional Access compliant device report-only test | Completed |
| Managed noncompliant BYOD test | Completed |
| Conditional Access enforced mode test | Completed |

Detailed lab files:

| Lab | File | Result |
|---|---|---|
| Windows basic compliance policy | `04-compliance-and-conditional-access/windows-basic-compliance-policy.md` | WINAUTO452 became compliant after Secure Boot remediation |
| Conditional Access compliant device | `04-compliance-and-conditional-access/conditional-access-compliant-device.md` | Report-only result showed Success for compliant device |
| Managed noncompliant device test | `04-compliance-and-conditional-access/managed-noncompliant-device-test.md` | Report-only result showed Failure for noncompliant BYOD device |
| Conditional Access enforced mode test | `04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md` | Access was blocked for noncompliant BYOD device |

---

## Remote actions and monitoring progress

| Lab | File | Result |
|---|---|---|
| Device sync remote action | `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Completed |
| Restart, Retire, and Wipe remote actions | `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` | Completed |
| Collect diagnostics remote action | `07-remote-actions-and-monitoring/collect-diagnostics.md` | Completed |
| Device monitoring and reports | `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Completed |

Remote actions tested:

| Action | Device | Result |
|---|---|---|
| Sync | WINAUTO452 | Completed |
| Restart | WINAUTO452 | Completed |
| Retire | WINAUTO452 | Completed |
| Wipe | WIN-CORP-001 | Completed |
| Collect diagnostics | WINAUTO452 | Completed |

---

## Troubleshooting progress

| Case study | File | Result |
|---|---|---|
| Intune enrollment troubleshooting | `08-troubleshooting/intune-enrollment-troubleshooting.md` | Completed |
| Configuration policy conflict troubleshooting | `08-troubleshooting/configuration-policy-conflict-troubleshooting.md` | Completed |
| Remote actions diagnostics troubleshooting | `08-troubleshooting/remote-actions-diagnostics-troubleshooting.md` | Completed |
| Troubleshooting summary | `08-troubleshooting/troubleshooting-summary.md` | Completed |

---

## BYOD progress

| BYOD scenario | Lab file | Result |
|---|---|---|
| Windows BYOD enrollment | `02-device-enrollment/windows-byod-enrollment.md` | Completed |
| Windows BYOD noncompliance testing | `04-compliance-and-conditional-access/managed-noncompliant-device-test.md` | Completed |
| Android BYOD work profile enrollment | `02-device-enrollment/android-byod-enrollment.md` | Completed |
| iOS/iPadOS BYOD enrollment | `02-device-enrollment/ios-byod-enrollment.md` | In Progress — admin prerequisites completed, physical enrollment pending |

---

## Completed modern endpoint management chain

The completed labs demonstrate this full practical chain:

```text
Microsoft Entra users and groups
-> Intune enrollment
-> Windows OOBE enrollment
-> Windows Autopilot registration and provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> iOS/iPadOS enrollment prerequisites
-> Microsoft Store app deployment
-> Win32 app deployment
-> Microsoft 365 Apps deployment
-> Android Managed Google Play app deployment
-> Windows configuration profiles
-> Corporate wallpaper deployment
-> USB storage restriction
-> Defender Antivirus policy
-> Windows Firewall policy
-> BitLocker encryption policy
-> Attack Surface Reduction policy in Audit mode
-> Windows Security Baseline deployed and troubleshot to Success
-> Windows compliance policy
-> Conditional Access report-only validation
-> Managed noncompliant BYOD test
-> Conditional Access enforced mode blocking test
-> Device sync remote action
-> Restart, Retire, and Wipe remote actions
-> Collect diagnostics remote action
-> Device monitoring and reports
-> Troubleshooting case studies documented
```

---

## Lab safety and privacy statement

This project is built for learning and portfolio purposes only.

The lab environment is fictional, isolated, and not connected to any production company environment.

Do not upload:

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
- Diagnostic ZIP package contents
- Unsanitized screenshots
- Production company data

---

## Current status

| Task | Status |
|---|---|
| Company scenario documented | Completed |
| Device inventory documented | Completed |
| Lab implementation roadmap documented | Completed |
| Identity and groups lab | Completed |
| Windows OOBE enrollment lab | Completed |
| Windows Autopilot enrollment lab | Completed |
| Windows BYOD enrollment lab | Completed |
| Android BYOD enrollment lab | Completed |
| iOS/iPadOS BYOD admin prerequisite lab | In Progress — admin prerequisites completed |
| Windows configuration profile labs | Completed |
| Application deployment labs | Completed |
| Android Managed Google Play app deployment lab | Completed |
| Defender Antivirus policy lab | Completed |
| Windows Firewall policy lab | Completed |
| BitLocker encryption policy lab | Completed |
| Attack Surface Reduction policy lab | Completed |
| Windows Security Baseline lab | Completed |
| Windows basic compliance policy lab | Completed |
| Conditional Access compliant-device report-only lab | Completed |
| Managed noncompliant BYOD Conditional Access lab | Completed |
| Conditional Access enforced mode lab | Completed |
| Device sync remote action lab | Completed |
| Restart, Retire, and Wipe remote actions lab | Completed |
| Collect diagnostics remote action lab | Completed |
| Device monitoring and reports lab | Completed |
| Intune enrollment troubleshooting case study | Completed |
| Configuration policy conflict troubleshooting case study | Completed |
| Remote actions diagnostics troubleshooting case study | Completed |
| Troubleshooting summary | Completed |
| iOS/iPadOS physical device enrollment | Pending — hardware required |
