# Device Inventory

This file tracks the lab devices used in the MD-102 Intune virtual company environment.

---

## Purpose

The purpose of this device inventory is to document all planned and active lab devices used for Microsoft Intune, Microsoft Entra ID, Windows Autopilot, BYOD enrollment, compliance, Conditional Access, application deployment, endpoint security, monitoring, and troubleshooting labs.

This file will be updated as devices are enrolled, tested, reset, retired, wiped, or reused for future labs.

---

## Device Ownership Types

This lab includes both corporate-owned and personally owned/BYOD devices.

### Corporate-Owned Devices

Corporate-owned devices are managed more strictly because they represent company assets.

These devices can be used for:

- Microsoft Entra join
- Microsoft Intune enrollment
- Windows Autopilot
- Compliance policies
- Configuration profiles
- Required app deployment
- Endpoint security policies
- BitLocker encryption
- Remote actions

### BYOD Devices

BYOD devices are personally owned test devices used to simulate employee-owned devices.

These devices should receive lighter, privacy-aware management.

BYOD testing helps compare:

```text
Unmanaged personal device
vs
Enrolled personal/BYOD device
vs
Corporate-managed device
```

### Autopilot Devices

Autopilot devices are corporate Windows devices registered with Windows Autopilot for cloud-based provisioning.

These devices are used to test:

- Hardware hash import
- Autopilot device import
- Deployment profile assignment
- Windows OOBE provisioning
- Microsoft Entra join
- Automatic Intune enrollment
- App and policy deployment after enrollment
- Corporate ownership after provisioning

---

## Device Inventory

| Device Name | Device Type | Ownership | OS | Enrollment Type | User | Status |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate lab | Windows 11 | OOBE + Entra joined + Intune | user01 | Enrolled / Compliant / Microsoft Store apps tested / Win32 7-Zip tested |
| WIN-AUTOPILOT-001 / WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven Entra join | user01 | Autopilot enrolled / Intune managed / Corporate / Compliant / Apps installed |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Browser sign-in test | user01 | Planned |
| WIN-BYOD-002 | Laptop | Personal/BYOD | Windows 11 | BYOD enrollment | user01 | Planned |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android | Work profile | user01 | Planned |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS | iOS enrollment | user01 | Planned |

> [!NOTE]
> During the Windows OOBE lab, Intune displayed `WIN-CORP-001` ownership as `Personal` after manual MDM enrollment. This is documented in the Windows OOBE enrollment lab and was later compared with Windows Autopilot corporate ownership behavior.

---

## Corporate Windows Device Plan

### WIN-CORP-001

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Laptop |
| Lab ownership | Corporate lab device |
| Intune ownership | Personal |
| Operating system | Windows 11 |
| Enrollment method | OOBE + manual MDM trigger |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Compliance | Compliant |
| Purpose | Main Windows Intune test device |
| Current status | Enrolled / Compliant / Microsoft Store apps tested / Win32 7-Zip tested |

This device was used first because it is the main Windows device for the lab.

It validated:

- Windows OOBE setup
- Device naming during OOBE
- Microsoft Entra join
- Intune enrollment troubleshooting
- Manual MDM enrollment trigger
- Intune device visibility
- Compliance status visibility
- Microsoft Store app deployment
- Required app installation through Intune
- Available app visibility in Company Portal
- Win32 7-Zip app deployment
- `.intunewin` package deployment through Intune
- Win32 app install status verification
- Microsoft 365 Apps deployment preparation

The detailed Windows enrollment lab is documented here:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

The detailed Microsoft Store app deployment lab is documented here:

```text
05-application-deployment/microsoft-store-app-deployment.md
```

The detailed Win32 7-Zip app deployment lab is documented here:

```text
05-application-deployment/win32-app-deployment-7zip.md
```

The detailed Microsoft 365 Apps deployment lab is documented here:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

---

## Application Deployment Tested on WIN-CORP-001

`WIN-CORP-001` was used to validate Microsoft Store app deployment with Microsoft Intune.

| App deployment item | Result |
|---|---|
| Application deployment tested | Microsoft Store apps |
| Assignment group used | GRP-Pilot-Users |
| Required apps installed | Company Portal, VLC UWP, Slack |
| Available apps visible in Company Portal | ChatGPT, WhatsApp |
| Device sync performed | Completed |
| Company Portal verification | Completed |
| Final app deployment result | Successful |

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

This proves that the device can receive both automatic app installs and self-service Company Portal app assignments.

Simple flow validated:

```text
Apps created in Intune
-> Apps assigned to GRP-Pilot-Users
-> WIN-CORP-001 synced with Intune
-> Required apps installed automatically
-> Available apps appeared in Company Portal
```

---

## Win32 App Deployment Tested on WIN-CORP-001

`WIN-CORP-001` was used to validate Win32 application deployment with Microsoft Intune.

| App deployment item | Result |
|---|---|
| Application deployment tested | Win32 app |
| App deployed | 7-Zip |
| Package format | `.intunewin` |
| Assignment group used | `GRP-Pilot-Users` |
| Assignment type | Required |
| Install status | Completed |
| Final app deployment result | Successful |

This proves that the device can receive Win32 app deployments through the Intune Management Extension.

Simple flow validated:

```text
7-Zip installer prepared
-> Installer packaged as .intunewin
-> Win32 app uploaded to Intune
-> App assigned as Required to GRP-Pilot-Users
-> WIN-CORP-001 received the app deployment
-> Intune install status was verified
```

---

## Windows Autopilot Device Result

### WIN-AUTOPILOT-001 / WINAUTO452

| Item | Value |
|---|---|
| Original lab device name | WIN-AUTOPILOT-001 |
| Final enrolled device name | WINAUTO452 |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Autopilot user-driven enrollment |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Autopilot group | GRP-Autopilot-Devices |
| Autopilot profile | APUserDrivenEntraJoinPilot |
| Compliance | Compliant |
| Apps verified | Store apps, Win32 7-Zip, Microsoft 365 Apps |
| Purpose | Windows Autopilot provisioning test |
| Current status | Autopilot enrolled / Intune managed / Corporate / Compliant / Apps installed |

This device was used to test Windows Autopilot from hardware hash import to completed provisioning.

The lab validated:

- Hardware hash collection
- Autopilot device CSV import
- Autopilot device group targeting
- Autopilot deployment profile creation
- Autopilot deployment profile assignment
- Windows OOBE sign-in with `user01`
- Microsoft Entra join
- Automatic Microsoft Intune enrollment
- Corporate device ownership
- Compliance status after enrollment
- Required app deployment after Autopilot enrollment
- Microsoft Store app deployment after Autopilot
- Win32 7-Zip deployment after Autopilot
- Microsoft 365 Apps deployment after Autopilot
- Company Portal installed apps validation

Final Autopilot result:

```text
WIN-AUTOPILOT-001 was provisioned with Windows Autopilot and appeared in Intune as WINAUTO452.
The device was managed by Microsoft Intune, marked as Corporate, showed Compliant, and received required app deployments.
```

The detailed Windows Autopilot lab is documented here:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

The detailed Microsoft 365 Apps Autopilot validation lab is documented here:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

> [!IMPORTANT]
> Autopilot hardware hashes, serial numbers, and device identifiers must not be uploaded to GitHub.

---

## Application Deployment Verified After Autopilot

`WINAUTO452` was used to validate app deployment after Windows Autopilot enrollment.

| App deployment item | Result |
|---|---|
| Microsoft Store apps | Installed / available as assigned |
| Win32 app | 7-Zip installed |
| Microsoft 365 Apps | Installed |
| Company Portal | Installed and used for validation |
| Required app deployment | Successful |
| Available app visibility | Successful |
| Final post-Autopilot app result | Successful |

Apps verified after Autopilot:

```text
Company Portal
VLC UWP
Slack
7-Zip
Microsoft 365 Apps for Windows 10 and later
ChatGPT
WhatsApp
```

Simple flow validated:

```text
Autopilot enrollment completed
-> Device joined Microsoft Entra ID
-> Device enrolled into Intune
-> Required apps applied
-> Microsoft Store apps installed
-> Win32 7-Zip installed
-> Microsoft 365 Apps installed
-> Company Portal confirmed app status
```

---

## Windows BYOD Device Plan

### WIN-BYOD-001

| Item | Planned Value |
|---|---|
| Device name | WIN-BYOD-001 |
| Device type | Laptop |
| Ownership | Personal/BYOD |
| Operating system | Windows 11 |
| Enrollment method | Unmanaged browser sign-in test |
| Management | Not enrolled |
| Test user | user01 |
| Purpose | Unmanaged BYOD access test |
| Current status | Planned |

This device will be intentionally left unmanaged for the first BYOD comparison test.

It will be used to show that an unmanaged device does not satisfy a Conditional Access requirement for a compliant device.

### WIN-BYOD-002

| Item | Planned Value |
|---|---|
| Device name | WIN-BYOD-002 |
| Device type | Laptop |
| Ownership | Personal/BYOD |
| Operating system | Windows 11 |
| Enrollment method | Access work or school / Company Portal |
| Join type | Microsoft Entra registered |
| Management | Microsoft Intune |
| Test user | user01 |
| Purpose | Windows BYOD enrollment test |
| Current status | Planned |

This device will be used to test personal Windows device enrollment.

The goal is to compare:

```text
WIN-BYOD-001 = unmanaged personal device
WIN-BYOD-002 = enrolled personal/BYOD device
```

---

## Mobile BYOD Device Plan

### ANDROID-BYOD-001

| Item | Planned Value |
|---|---|
| Device name | ANDROID-BYOD-001 |
| Device type | Mobile |
| Ownership | Personal/BYOD |
| Operating system | Android |
| Enrollment method | Android Enterprise work profile |
| Management | Microsoft Intune |
| Test user | user01 |
| Purpose | Android BYOD work profile test |
| Current status | Planned |

This device will be used to test separation between personal apps/data and work apps/data using Android Enterprise personally owned work profile.

### IOS-BYOD-001

| Item | Planned Value |
|---|---|
| Device name | IOS-BYOD-001 |
| Device type | Mobile |
| Ownership | Personal/BYOD |
| Operating system | iOS |
| Enrollment method | iOS/iPadOS enrollment |
| Management | Microsoft Intune |
| Test user | user01 |
| Purpose | iOS BYOD enrollment test |
| Current status | Planned |

This device will be used to test iOS/iPadOS BYOD enrollment and privacy-aware mobile device management.

---

## Device Naming Convention

The lab uses simple names to make screenshots and documentation easier to understand.

| Naming Pattern | Meaning |
|---|---|
| WIN-CORP-### | Corporate Windows device |
| WIN-AUTOPILOT-### | Windows Autopilot test device |
| WINAUTO### | Final Autopilot-generated Windows device name |
| WIN-BYOD-### | Personal Windows BYOD test device |
| ANDROID-BYOD-### | Personal Android BYOD test device |
| IOS-BYOD-### | Personal iOS BYOD test device |

Examples:

```text
WIN-CORP-001
WIN-AUTOPILOT-001
WINAUTO452
WIN-BYOD-001
ANDROID-BYOD-001
IOS-BYOD-001
```

---

## Device Lifecycle Tracking

Each device may move through several states during the lab.

| Status | Meaning |
|---|---|
| Planned | Device is documented but not tested |
| In progress | Lab work is active |
| Enrolled | Device enrolled into Intune |
| Compliant | Device meets compliance rules |
| Corporate | Device is treated as a corporate-owned device in Intune |
| App deployment tested | Device has been used for Intune app deployment validation |
| Autopilot enrolled | Device completed Windows Autopilot provisioning |
| Noncompliant | Device fails compliance rules |
| Retired | Device removed from Intune |
| Wiped | Device reset |
| Discarded | Device no longer used |

---

## Screenshot Folder Mapping

Screenshots for device-related labs should be stored in the matching sanitized screenshot folders.

| Lab Area | Screenshot Folder |
|---|---|
| Windows enrollment | screenshots/sanitized/device-enrollment/ |
| Autopilot enrollment | screenshots/sanitized/device-enrollment/ |
| BYOD enrollment | screenshots/sanitized/device-enrollment/ |
| Compliance testing | screenshots/sanitized/compliance/ |
| Conditional Access testing | screenshots/sanitized/conditional-access/ |
| Application deployment | screenshots/sanitized/application-deployment/ |
| Endpoint security | screenshots/sanitized/endpoint-security/ |
| Remote actions | screenshots/sanitized/remote-actions-and-monitoring/ |
| Troubleshooting | screenshots/sanitized/troubleshooting/ |

---

## Security and Privacy Notes

This is a public learning repository.

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
- Internal IP addresses
- Unsanitized screenshots
- Production company data

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Device IDs
- Object IDs
- Serial numbers
- Hardware hashes
- Recovery keys
- Tokens or QR codes

---

## Current Status

| Task | Status |
|---|---|
| Device inventory file created | Completed |
| Corporate Windows device documented | Completed |
| WIN-CORP-001 enrolled in Intune | Completed |
| WIN-CORP-001 compliance visible | Completed |
| WIN-CORP-001 Microsoft Store app deployment tested | Completed |
| Required apps installed on WIN-CORP-001 | Completed |
| Available apps visible in Company Portal on WIN-CORP-001 | Completed |
| WIN-CORP-001 Win32 7-Zip deployment tested | Completed |
| Win32 app install status verified on WIN-CORP-001 | Completed |
| Microsoft 365 Apps deployment tested | Completed |
| Autopilot device documented | Completed |
| WIN-AUTOPILOT-001 registered with Autopilot | Completed |
| WIN-AUTOPILOT-001 provisioned as WINAUTO452 | Completed |
| WINAUTO452 enrolled in Intune | Completed |
| WINAUTO452 ownership verified as Corporate | Completed |
| WINAUTO452 compliance verified | Completed |
| WINAUTO452 app deployment verified | Completed |
| Windows BYOD devices documented | Planned |
| Android BYOD device documented | Planned |
| iOS BYOD device documented | Planned |
| First device enrollment started | Completed |

---

## Next Step

Continue to endpoint security policy labs.

Recommended next lab:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Follow-on endpoint security labs:

```text
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```
