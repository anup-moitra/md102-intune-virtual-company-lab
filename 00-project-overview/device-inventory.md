# Device Inventory

This file tracks the lab devices used in the MD-102 Intune virtual company environment.

## Device Ownership Types

This lab includes both corporate-owned and personally owned/BYOD devices.

- **Corporate-owned devices** are owned by the virtual company and can receive stronger Intune management.
- **BYOD devices** are personally owned devices used for work access and should receive more limited management focused on protecting company data.
- **Autopilot devices** are corporate devices registered with Windows Autopilot for user-driven provisioning.

## Inventory

| Device Name | Device Type | Ownership | Operating System | Enrollment Type | Assigned / Primary User | Status |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Physical laptop | Corporate | Windows 11 | Windows OOBE + Microsoft Entra joined + Intune enrolled | user01 | Enrolled and compliant |
| WIN-AUTOPILOT-001 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven Microsoft Entra join | user01 | Autopilot enrolled, Intune managed, and compliant |
| WIN-CORP-002 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-003 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-004 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-005 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-006 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-007 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-CORP-008 | Laptop | Corporate | Windows 11 | Planned: Entra joined + Intune enrolled | TBD | Planned |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Not enrolled / unmanaged browser sign-in test | user01 | Tested as unmanaged BYOD for Conditional Access |
| WIN-BYOD-002 | Laptop | Personal/BYOD | Windows 11 | Planned: BYOD user enrollment | TBD | Planned |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android | Planned: Personally owned work profile | TBD | Planned |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS | Planned: User enrollment / Company Portal | TBD | Planned |

## Completed Device Enrollment

### WIN-CORP-001

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Physical laptop |
| Manufacturer | Lenovo |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Out-of-Box Experience work or school setup |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Enrolled by | user01 |
| Compliance status | Compliant |
| Compliance policy | Windows 11 Basic Compliance |
| Configuration profile tested | WIN-CORP-Basic-Configuration-Profile |
| Lab result | Successful |

## Completed Autopilot Device Enrollment

### WIN-AUTOPILOT-001

| Item | Value |
|---|---|
| Device name | WIN-AUTOPILOT-001 / Windows-generated name |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Autopilot registration | Hardware hash imported |
| Autopilot profile | AP WIN User Driven Entra Join |
| Autopilot group | GRP-Autopilot-Devices |
| Profile status | Assigned |
| Enrollment method | Windows Autopilot user-driven Microsoft Entra join |
| Test user | user01 |
| Management | Microsoft Intune |
| Join type | Microsoft Entra joined |
| Ownership status in Intune | Corporate |
| Compliance status | Compliant |
| Microsoft 365 Apps deployment | Installed and verified |
| Office app validation | Word sign-in verified with User 01 |
| Lab result | Successful |

This device was used to validate the Windows Autopilot provisioning flow and Microsoft 365 Apps deployment after enrollment.

## Completed BYOD Testing

### WIN-BYOD-001

| Item | Value |
|---|---|
| Device name | WIN-BYOD-001 |
| Device type | Laptop |
| Ownership | Personal/BYOD |
| Operating system | Windows 11 |
| Enrollment status | Not enrolled |
| Management status | Unmanaged |
| Test user | user01 |
| Test purpose | Conditional Access Report-only unmanaged BYOD test |
| Conditional Access result | Report-only: Failure |
| Lab result | Successful unmanaged BYOD test |

WIN-BYOD-001 was intentionally left unenrolled to confirm that an unmanaged BYOD device does not satisfy the compliant device requirement in Conditional Access.

## Planned BYOD Devices

BYOD enrollment has not been completed yet.

Planned BYOD enrollment testing will include:

- Windows BYOD enrollment using **Settings > Accounts > Access work or school > Connect**
- Android personally owned work profile enrollment
- iOS user enrollment / Company Portal enrollment

## Screenshot Placeholders

Screenshots should be added after sanitizing sensitive information.

Suggested folder path:

```text
screenshots/sanitized/device-inventory/
```

Suggested screenshot filenames:

```text
win-corp-001-overview-sanitized.jpg
win-corp-001-compliance-sanitized.jpg
win-autopilot-001-intune-overview-sanitized.jpg
win-autopilot-001-compliance-status-sanitized.jpg
win-byod-001-report-only-test-sanitized.jpg
```

## Security and Privacy Notes

This is a public learning repository. The following information must not be published:

- Real user email addresses
- Real tenant names or tenant IDs
- Device serial numbers
- Autopilot hardware hashes
- BitLocker recovery keys
- QR codes or enrollment tokens
- Internal IP addresses
- Production company data
- Unsanitized screenshots

> [!IMPORTANT]
> All lab data in this repository is fictional or sanitized for privacy and security.

## Current Status

Completed:

- WIN-CORP-001 enrolled as a corporate Windows device
- WIN-CORP-001 joined to Microsoft Entra ID
- WIN-CORP-001 enrolled into Microsoft Intune
- WIN-CORP-001 reported compliant
- WIN-BYOD-001 tested as unmanaged BYOD for Conditional Access
- Autopilot test device imported into Windows Autopilot
- Autopilot profile assigned successfully
- Autopilot OOBE sign-in completed with User 01
- Autopilot device appeared in Intune Windows devices
- Autopilot device showed corporate ownership and compliant status
- Microsoft 365 Apps deployment verified on the Autopilot device
- Word sign-in verified with User 01

Pending:

- Windows BYOD enrollment
- Android BYOD enrollment
- iOS BYOD enrollment
- Additional Windows corporate devices
- Managed but noncompliant corporate Windows test
