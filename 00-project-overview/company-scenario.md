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

This lab environment simulates common endpoint administration tasks such as:

- User and group management
- Device enrollment
- Windows Autopilot provisioning
- BYOD enrollment
- Configuration profiles
- Application deployment
- Endpoint security
- Compliance and Conditional Access planning
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
- Endpoint security baselines for corporate Windows devices
- Future compliance and Conditional Access enforcement

---

## Device environment

| Device type | Ownership | Platform | Purpose |
|---|---|---|---|
| Corporate laptops | Company-owned | Windows 11 | Managed endpoint testing |
| Autopilot laptops | Company-owned | Windows 11 | Autopilot provisioning and corporate endpoint security |
| BYOD laptops | Personally owned | Windows 11 | Windows BYOD enrollment testing |
| BYOD mobile devices | Personally owned | Android Enterprise | Android work profile testing |
| BYOD mobile devices | Personally owned | iOS/iPadOS | iOS BYOD enrollment testing |

---

## Lab devices

| Device name | Device type | Ownership | Operating system | Current use / result |
|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Personal in Intune after manual MDM enrollment | Windows 11 | OOBE enrollment, Intune management, compliance visibility, and app deployment testing |
| WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot enrollment, configuration profiles, app deployment, and endpoint security validation |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows BYOD enrollment validation |
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
| Main pilot user | user01 | Primary Windows, Autopilot, app, and policy test user |
| Windows test user | user02 | Additional Windows policy testing |
| BYOD test user | user03 | Windows BYOD and Android BYOD testing |
| iOS BYOD test user | user04 | iOS/iPadOS BYOD enrollment preparation |
| Policy test user | user05 | Future policy testing |

---

## Lab groups

| Group name | Purpose |
|---|---|
| GRP-All-Lab-Users | General lab targeting |
| GRP-Pilot-Users | Pilot testing and user-based assignments |
| GRP-Windows-Users | Windows user targeting |
| GRP-BYOD-Users | BYOD enrollment and BYOD app targeting |
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
- Test Attack Surface Reduction policy
- Test Windows Security Baseline policy
- Create compliance policies
- Test Conditional Access in report-only mode before enforcement
- Use remote actions such as sync, restart, retire, wipe, and collect diagnostics
- Review Intune monitoring and reporting
- Document troubleshooting scenarios

---

## Completed lab progress

Completed so far:

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

---

## Completed device outcomes

### WIN-CORP-001

```text
Windows OOBE enrollment completed
Device appeared in Intune
Device showed Intune management
Device was used for early app deployment testing
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
```

### WIN-BYOD-001

```text
Windows BYOD enrollment completed
Device appeared in Intune
Ownership showed Personal
Compliance showed Compliant
Primary user showed user03
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

Application deployment has been validated using four approaches.

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
| Attack Surface Reduction policy | `06-endpoint-security/attack-surface-reduction-policy.md` | Next / Planned |
| Windows Security Baseline | `06-endpoint-security/windows-security-baseline.md` | Planned |

---

## BYOD progress

| BYOD scenario | Lab file | Result |
|---|---|---|
| Windows BYOD enrollment | `02-device-enrollment/windows-byod-enrollment.md` | Completed |
| Android BYOD work profile enrollment | `02-device-enrollment/android-byod-enrollment.md` | Completed |
| iOS/iPadOS BYOD enrollment | `02-device-enrollment/ios-byod-enrollment.md` | In Progress / Admin prerequisites completed |

---

## Completed modern endpoint management chain

The completed labs now demonstrate this practical chain:

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
```

---

## Planned next labs

| Area | Lab file | Status |
|---|---|---|
| Endpoint Security | `06-endpoint-security/attack-surface-reduction-policy.md` | Next / Planned |
| Device Enrollment | `02-device-enrollment/ios-byod-enrollment.md` | In Progress / Device enrollment pending |
| Endpoint Security | `06-endpoint-security/windows-security-baseline.md` | Planned |
| Compliance and Conditional Access | `04-compliance-and-conditional-access/windows-basic-compliance-policy.md` | Planned |
| Remote Actions and Monitoring | `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Planned |

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
| iOS/iPadOS BYOD admin prerequisite lab | In Progress / Admin prerequisites completed |
| Windows configuration profile labs | Completed |
| Application deployment labs | Completed |
| Android Managed Google Play app deployment lab | Completed |
| Defender Antivirus policy lab | Completed |
| Windows Firewall policy lab | Completed |
| BitLocker encryption policy lab | Completed |
| Attack Surface Reduction policy lab | Next / Planned |
| Windows Security Baseline lab | Planned |
| Compliance and Conditional Access labs | Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting documentation | Planned |

---

## Next step

Recommended next endpoint security lab:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Alternative BYOD continuation:

```text
02-device-enrollment/ios-byod-enrollment.md
```

The iOS/iPadOS lab already has admin prerequisites completed. It should be finished when a physical iPhone/iPad test device is available.
