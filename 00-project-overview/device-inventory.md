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
- Autopilot deployment profile assignment
- Windows OOBE provisioning
- Microsoft Entra join
- Automatic Intune enrollment
- App and policy deployment after enrollment

---

## Planned Device Inventory

| Device Name | Device Type | Ownership | Operating System | Enrollment Type | Assigned User | Status |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate | Windows 11 | Windows OOBE + Microsoft Entra joined + Intune enrolled | user01 | Planned |
| WIN-AUTOPILOT-001 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven enrollment | user01 | Planned |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Unmanaged browser sign-in test | user01 | Planned |
| WIN-BYOD-002 | Laptop | Personal/BYOD | Windows 11 | Windows BYOD enrollment | user01 | Planned |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android | Android Enterprise personally owned work profile | user01 | Planned |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS | iOS/iPadOS user enrollment or Company Portal enrollment | user01 | Planned |

---

## Corporate Windows Device Plan

### WIN-CORP-001

| Item | Planned Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Out-of-Box Experience work or school setup |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Purpose | Main corporate Windows Intune test device |
| Current status | Planned |

This device will be used first because it is the main corporate Windows device for the lab.

It will be used to validate:

- Windows OOBE enrollment
- Microsoft Entra join
- Intune enrollment
- Compliance policy
- Conditional Access
- Configuration profiles
- App deployment
- Endpoint security policies
- Remote actions
- Monitoring and troubleshooting

---

## Windows Autopilot Device Plan

### WIN-AUTOPILOT-001

| Item | Planned Value |
|---|---|
| Device name | WIN-AUTOPILOT-001 |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Autopilot user-driven enrollment |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Autopilot group | GRP-Autopilot-Devices |
| Purpose | Windows Autopilot provisioning test |
| Current status | Planned |

This device will be used to test Windows Autopilot from registration to completed provisioning.

The lab will document:

- Hardware hash collection
- Autopilot device import
- Deployment profile assignment
- OOBE sign-in
- Microsoft Entra join
- Intune enrollment
- App and policy deployment after enrollment

> [!IMPORTANT]
> Autopilot hardware hashes, serial numbers, and device identifiers must not be uploaded to GitHub.

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
| Purpose | Test unmanaged BYOD access behavior |
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
| Enrollment method | Access work or school / Company Portal enrollment |
| Join or registration type | Microsoft Entra registered / workplace joined |
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
| Enrollment method | Android Enterprise personally owned work profile |
| Management | Microsoft Intune |
| Test user | user01 |
| Purpose | Android BYOD enrollment and work profile testing |
| Current status | Planned |

This device will be used to test separation between personal apps/data and work apps/data using Android Enterprise personally owned work profile.

### IOS-BYOD-001

| Item | Planned Value |
|---|---|
| Device name | IOS-BYOD-001 |
| Device type | Mobile |
| Ownership | Personal/BYOD |
| Operating system | iOS |
| Enrollment method | iOS/iPadOS user enrollment or Company Portal enrollment |
| Management | Microsoft Intune |
| Test user | user01 |
| Purpose | iOS BYOD enrollment testing |
| Current status | Planned |

This device will be used to test iOS/iPadOS BYOD enrollment and privacy-aware mobile device management.

---

## Device Naming Convention

The lab uses simple names to make screenshots and documentation easier to understand.

| Naming Pattern | Meaning |
|---|---|
| WIN-CORP-### | Corporate Windows device |
| WIN-AUTOPILOT-### | Windows Autopilot test device |
| WIN-BYOD-### | Personal Windows BYOD test device |
| ANDROID-BYOD-### | Personal Android BYOD test device |
| IOS-BYOD-### | Personal iOS BYOD test device |

Examples:

```text
WIN-CORP-001
WIN-AUTOPILOT-001
WIN-BYOD-001
ANDROID-BYOD-001
IOS-BYOD-001
```

---

## Device Lifecycle Tracking

Each device may move through several states during the lab.

| Status | Meaning |
|---|---|
| Planned | Device is documented but not yet tested |
| In progress | Lab work is currently being performed |
| Enrolled | Device successfully enrolled into Intune |
| Compliant | Device meets compliance policy requirements |
| Noncompliant | Device fails one or more compliance requirements |
| Retired | Device removed from Intune management |
| Wiped | Device reset using Intune or local reset |
| Discarded | Retired lab-only test device no longer used |

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
| Corporate Windows device documented | Planned |
| Autopilot device documented | Planned |
| Windows BYOD devices documented | Planned |
| Android BYOD device documented | Planned |
| iOS BYOD device documented | Planned |
| First device enrollment started | Planned |

---

## Next Step

Create the lab roadmap file:

```text
00-project-overview/lab-implementation-roadmap.md
```

After the roadmap is created, the next hands-on section will be:

```text
01-identity-and-groups/users-and-groups.md
```
