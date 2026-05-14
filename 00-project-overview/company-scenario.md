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
- Endpoint security policies for device protection

This lab environment is designed to simulate common endpoint administration tasks such as:

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
- Planned iOS BYOD devices

---

## Business scenario

Contoso Startup Lab wants to manage corporate and personal devices securely while allowing users to access Microsoft 365 resources.

The company wants to support:

- Corporate Windows laptops for employees
- Windows Autopilot for new corporate device provisioning
- Personal Windows BYOD enrollment
- Android Enterprise personally owned work profile enrollment
- Planned iOS BYOD enrollment
- Required business app deployment
- Optional self-service app deployment through Company Portal
- Endpoint security baselines for corporate Windows devices
- Future compliance and Conditional Access enforcement

---

## Device environment

The company uses a mixed device environment.

| Device type | Ownership | Platform | Purpose |
|---|---|---|---|
| Corporate laptops | Company-owned | Windows 11 | Managed endpoint testing |
| Autopilot laptops | Company-owned | Windows 11 | Autopilot provisioning and corporate endpoint security |
| BYOD laptops | Personally owned | Windows 11 | Windows BYOD enrollment testing |
| BYOD mobile devices | Personally owned | Android Enterprise | Android work profile testing |
| BYOD mobile devices | Personally owned | iOS | Planned iOS BYOD testing |

---

## Lab devices

| Device name | Device type | Ownership | Operating system | Current use / result |
|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Personal after manual enrollment | Windows 11 | OOBE enrollment, Intune management, compliance visibility, and app deployment testing |
| WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot enrollment, configuration profiles, app deployment, and endpoint security validation |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows BYOD enrollment validation |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android 15 | Android Enterprise personally owned work profile enrollment validation |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS | Planned iOS BYOD enrollment test |

> [!NOTE]
> `WIN-CORP-001` completed the Windows OOBE enrollment lab and appeared in Microsoft Intune. Intune showed the ownership value as `Personal` after manual MDM enrollment. This was later compared with the corporate ownership behavior of the Windows Autopilot-enrolled device `WINAUTO452`.

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
| Mobile test user | user04 | Planned mobile testing |
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

## Management tools

| Tool | Purpose |
|---|---|
| Microsoft Intune admin center | Device, app, configuration, and endpoint security management |
| Microsoft Entra ID | Identity, groups, and access management |
| Windows Autopilot | Corporate Windows device provisioning |
| Company Portal | User-facing app and device experience |
| Microsoft 365 Apps | Productivity app suite |
| Managed Google Play | Android Enterprise app deployment |
| PowerShell | Local validation and automation support |
| GitHub | Public project documentation and portfolio evidence |

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
- Microsoft Store app deployment
- Win32 7-Zip app deployment
- Microsoft 365 Apps deployment
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
```

---

## Application deployment progress

Application deployment has been validated using three approaches.

| App deployment type | Lab file | Result |
|---|---|---|
| Microsoft Store app deployment | `05-application-deployment/microsoft-store-app-deployment.md` | Completed |
| Win32 app deployment | `05-application-deployment/win32-app-deployment-7zip.md` | Completed |
| Microsoft 365 Apps deployment | `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Completed |

### Microsoft Store apps tested

Required apps:

```text
Company Portal
VLC UWP
Slack
```

Available apps:

```text
ChatGPT
WhatsApp
```

Observed result:

```text
Required apps installed automatically.
Available apps appeared in Company Portal for user self-service installation.
```

### Win32 app tested

```text
7-Zip
```

Observed result:

```text
7-Zip was packaged as a .intunewin file, deployed through Intune, and verified on the endpoint.
```

### Microsoft 365 Apps tested

Observed result:

```text
Microsoft 365 Apps installed successfully through Intune and were validated after Windows Autopilot enrollment.
```

---

## Configuration profile progress

Configuration profiles have been validated on the Autopilot-managed Windows device.

| Configuration profile | Lab file | Result |
|---|---|---|
| Windows basic configuration profile | `03-configuration-profiles/windows-basic-configuration-profile.md` | Completed |
| Corporate wallpaper ADMX policy | `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Completed |
| USB storage block policy | `03-configuration-profiles/windows-device-restrictions-profile.md` | Completed |

Observed results:

```text
Basic Windows configuration profile was created and assigned.
Corporate wallpaper was applied successfully using an ADMX-backed policy.
USB removable storage access was blocked successfully on WINAUTO452.
```

---

## Endpoint security progress

Endpoint security has been validated on the Autopilot-managed Windows device.

| Endpoint security policy | Lab file | Result |
|---|---|---|
| Microsoft Defender Antivirus policy | `06-endpoint-security/windows-defender-antivirus-policy.md` | Completed |
| Windows Firewall policy | `06-endpoint-security/windows-firewall-policy.md` | Completed |
| BitLocker encryption policy | `06-endpoint-security/bitlocker-encryption-policy.md` | Completed |
| Attack Surface Reduction policy | `06-endpoint-security/attack-surface-reduction-policy.md` | Next / Planned |
| Windows Security Baseline | `06-endpoint-security/windows-security-baseline.md` | Planned |

Observed results:

```text
Defender Antivirus policy reported Success.
Windows Firewall policy reported Success.
BitLocker policy reported Success.
WINAUTO452 showed Fully Encrypted, 100.0% encrypted, and Protection On.
```

---

## BYOD progress

BYOD enrollment has been validated for Windows and Android.

| BYOD scenario | Lab file | Result |
|---|---|---|
| Windows BYOD enrollment | `02-device-enrollment/windows-byod-enrollment.md` | Completed |
| Android BYOD work profile enrollment | `02-device-enrollment/android-byod-enrollment.md` | Completed |
| iOS BYOD enrollment | `02-device-enrollment/ios-byod-enrollment.md` | Planned |

Observed results:

```text
WIN-BYOD-001 enrolled as a personally owned Windows BYOD device.
ANDROID-BYOD-001 enrolled as a personally owned Android Enterprise work profile device.
```

---

## Example real-world access scenario

A typical access flow in this lab will be:

```text
User signs in to Microsoft 365
-> Microsoft Entra ID evaluates the sign-in
-> Conditional Access checks policy requirements
-> Intune provides device compliance status
-> Access is allowed or blocked based on policy result
```

This helps demonstrate the relationship between identity, device compliance, and access control.

---

## Example real-world app deployment scenario

A typical app deployment flow in this lab is:

```text
Admin creates app in Intune
-> App is assigned to GRP-Pilot-Users
-> Managed device syncs with Intune
-> Required apps install automatically
-> Available apps appear in Company Portal
-> Admin verifies results in Intune and on the endpoint
```

This demonstrates the difference between automatic required app deployment and user-driven self-service app deployment.

---

## Example real-world endpoint security scenario

A typical endpoint security flow in this lab is:

```text
Device enrolls through Windows Autopilot
-> Device joins Microsoft Entra ID
-> Device enrolls into Microsoft Intune
-> Endpoint security policies are assigned to GRP-Autopilot-Devices
-> Device receives Defender, Firewall, and BitLocker policies
-> Intune reports policy status
-> Admin validates local endpoint result
```

This demonstrates how a corporate Windows device can receive security controls after provisioning.

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
-> Microsoft Store app deployment
-> Win32 app deployment
-> Microsoft 365 Apps deployment
-> Windows configuration profiles
-> Corporate wallpaper deployment
-> USB storage restriction
-> Defender Antivirus policy
-> Windows Firewall policy
-> BitLocker encryption policy
```

This creates a strong real-world portfolio scenario for MD-102 preparation.

---

## Planned next labs

The next recommended labs are:

| Area | Lab file | Status |
|---|---|---|
| Endpoint Security | `06-endpoint-security/attack-surface-reduction-policy.md` | Next / Planned |
| Device Enrollment | `02-device-enrollment/ios-byod-enrollment.md` | Planned |
| Endpoint Security | `06-endpoint-security/windows-security-baseline.md` | Planned |
| Compliance and Conditional Access | `04-compliance-and-conditional-access/windows-basic-compliance-policy.md` | Planned |
| Remote Actions and Monitoring | `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Planned |

Recommended next choice:

```text
Attack Surface Reduction policy or iOS BYOD enrollment
```

---

## Lab safety and privacy statement

This project is built for learning and portfolio purposes only.

The lab environment is fictional, isolated, and not connected to any production company environment.

The devices used in this lab are retired lab-only test devices. They do not contain production company data and may be reset, wiped, or discarded after lab completion.

Before uploading screenshots to GitHub, sensitive information must be hidden or removed.

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
| Windows configuration profile labs | Completed |
| Application deployment labs | Completed |
| Defender Antivirus policy lab | Completed |
| Windows Firewall policy lab | Completed |
| BitLocker encryption policy lab | Completed |
| Attack Surface Reduction policy lab | Next / Planned |
| iOS BYOD enrollment lab | Planned |
| Windows Security Baseline lab | Planned |
| Compliance and Conditional Access labs | Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting documentation | Planned |

---

## Next step

Continue with one of the following labs.

### Option 1 - Continue endpoint security

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

This path continues the endpoint security sequence after Defender Antivirus, Windows Firewall, and BitLocker.

### Option 2 - Continue BYOD enrollment

```text
02-device-enrollment/ios-byod-enrollment.md
```

This path completes the remaining planned BYOD enrollment scenario.

Recommended next choice:

```text
Attack Surface Reduction policy
```
