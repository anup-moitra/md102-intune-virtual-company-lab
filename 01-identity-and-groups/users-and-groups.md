# Users and Groups

This file documents Microsoft Entra ID users and groups for the virtual company lab.

## Purpose

Microsoft Entra ID users and groups are used to organize lab identities and assign Intune policies, apps, compliance settings, Conditional Access rules, and device management configurations.

## User Naming Convention

| User Type | Naming Format | Example |
|---|---|---|
| Standard user | user-number | user01 |
| Department user | department-user-number | finance-user01 |
| IT admin | admin-number | admin01 |

## Lab Users

| Display Name | Username | Department | Role | Status |
|---|---|---|---|---|
| Admin User 01 | admin01 | IT | Lab administrator | Created |
| User 01 | user01 | Management | Standard user / pilot user | Created |
| User 02 | user02 | Finance | Standard user | Created |
| User 03 | user03 | HR | Standard user | Created |
| User 04 | user04 | Operations | Standard user | Created |
| User 05 | user05 | Operations | Standard user | Created |

## Lab Groups

| Group Name | Group Type | Purpose | Status |
|---|---|---|---|
| GRP-All-Lab-Users | Security group | General lab user targeting | Created |
| GRP-Pilot-Users | Security group | Pilot users for testing policies and apps | Created |
| GRP-Windows-Users | Security group | Windows user targeting | Created |
| GRP-BYOD-Users | Security group | BYOD user targeting | Created |
| GRP-Mobile-Users | Security group | Android/iOS user targeting | Created |
| GRP-IT-Admins | Security group | Lab admin users | Created |
| GRP-Autopilot-Devices | Security group | Autopilot registered Windows devices | Created |

## License Assignment

| User | Intune License | Microsoft 365 Business Premium | Notes |
|---|---|---|---|
| admin01 | Assigned | Optional / if available | Admin testing |
| user01 | Assigned | Assigned | Used for Windows enrollment, Autopilot, and Office app testing |
| user02 | Assigned | Optional / if available | Standard user testing |
| user03 | Assigned | Optional / if available | Standard user testing |
| user04 | Assigned | Optional / if available | Standard user testing |
| user05 | Assigned | Optional / if available | Standard user testing |

## Group Strategy

The lab uses separate groups for pilot testing, Windows users, BYOD users, mobile users, admins, and Autopilot devices.

This makes it easier to target policies safely before assigning them broadly.

## Assignment Examples

| Policy or App | Target Group | Reason |
|---|---|---|
| Basic Windows configuration profile | GRP-Pilot-Users | Test with a small user group first |
| Microsoft 365 Apps Autopilot deployment | GRP-Pilot-Users | User 01 signs in during Autopilot |
| Conditional Access requiring compliant device | GRP-Pilot-Users | Safe pilot testing |
| Windows Autopilot deployment profile | GRP-Autopilot-Devices | Target Autopilot registered devices |
| Future BYOD policies | GRP-BYOD-Users | Apply lighter BYOD management |
| Future mobile app protection | GRP-Mobile-Users | Protect work data on mobile devices |

## Screenshots

Suggested screenshot folder:

```text
screenshots/sanitized/identity-and-groups/
```

Suggested screenshots:

```text
lab-users-created-sanitized.jpg
lab-groups-created-sanitized.jpg
user01-license-assignment-sanitized.jpg
grp-pilot-users-membership-sanitized.jpg
grp-autopilot-devices-sanitized.jpg
```

## Security and Privacy Notes

Do not publish:

- Full real email addresses
- Real tenant names
- Tenant IDs
- Object IDs
- Passwords
- MFA QR codes
- Unsanitized screenshots

## Current Status

Completed:

- Lab users created
- Lab groups created
- Intune licenses assigned
- Microsoft 365 Business Premium assigned to user01
- Autopilot device group created

Pending:

- Add screenshots as available
- Add future device groups when additional devices are enrolled
