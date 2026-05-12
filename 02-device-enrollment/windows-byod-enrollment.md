# Windows BYOD Enrollment

This lab documents Windows bring-your-own-device (BYOD) enrollment into Microsoft Intune.

---

## Objective

Enroll a personally owned Windows device into Microsoft Intune using a standard BYOD user account.

This lab validates that:

- A BYOD user can be targeted for Windows MDM enrollment.
- Windows personal device enrollment is allowed in Intune enrollment restrictions.
- A Windows device can be enrolled into Intune as a personal device.
- The enrolled device appears in Intune as managed by Intune.
- The device ownership is shown as Personal.
- The device can sync with Intune from Windows Settings.
- The device can be used for future BYOD compliance, app, and policy testing.

---

## Why This Lab Matters

In a real organization, not every Windows device is corporate-owned.

Some users may use a personal laptop to access work resources. This is called BYOD.

With Intune, administrators can allow controlled access from personal devices while still applying management, compliance, and security requirements.

Simple flow:

```text
User signs in with work account
-> Windows enrolls into Intune MDM
-> Intune marks the device as Personal
-> Admin can apply BYOD policies and compliance rules
```

This is different from a corporate Autopilot device, which is normally treated as organization-owned.

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Lab company | HomeLAB / Contoso Startup Lab |
| BYOD test user | user03 |
| BYOD user group | GRP-BYOD-Users |
| Device name | WIN-BYOD-001 |
| Device ownership | Personal |
| Operating system | Windows |
| Enrollment method | Windows MDM enrollment from Settings |
| Current status | Completed |

---

## Test User and Group

The BYOD enrollment test used:

```text
user03
```

The user was added to:

```text
GRP-BYOD-Users
```

This group was used to scope Windows MDM enrollment for BYOD testing.

---

## Prerequisites

Before enrolling the device, the following items were confirmed:

- `user03` existed as a Microsoft Entra ID user.
- `user03` had an Intune-capable license assigned.
- `user03` was a member of `GRP-BYOD-Users`.
- Automatic MDM enrollment included `GRP-BYOD-Users`.
- Windows personal device enrollment was allowed in Intune enrollment restrictions.
- The test device was renamed to `WIN-BYOD-001`.

---

## Admin Configuration Review

### Step 1: Confirmed User 03 License Assignment

Opened:

```text
Microsoft 365 admin center
-> Users
-> Active users
-> User 03
-> Licenses and apps
```

Confirmed that `user03` had the required Intune-capable license assigned.

### Step 2: Confirmed User 03 BYOD Group Membership

Opened:

```text
Microsoft 365 admin center
-> Users
-> Active users
-> User 03
-> Manage groups
```

Confirmed that `user03` was a member of:

```text
GRP-BYOD-Users
```

### Step 3: Configured Automatic MDM Enrollment Scope

Opened:

```text
Intune admin center
-> Devices
-> Windows
-> Windows enrollment
-> Automatic Enrollment
```

Configured:

| Setting | Value |
|---|---|
| MDM user scope | Some |
| Selected group | GRP-BYOD-Users |
| Disable MDM enrollment when adding work or school account on Windows | No |

This ensured that users in `GRP-BYOD-Users` could enroll Windows devices into Intune MDM.

### Step 4: Confirmed Windows Personal Enrollment Was Allowed

Opened:

```text
Intune admin center
-> Devices
-> Enrollment
-> Device platform restrictions
-> Windows restrictions
-> All Users
```

Confirmed the Windows platform restriction settings:

| Setting | Value |
|---|---|
| Windows (MDM) platform | Allow |
| Windows personally owned | Allow |

This allowed personally owned Windows devices to enroll into Intune.

---

## Device Preparation

### Step 5: Verified Device Name

On the Windows test device, the device name was confirmed as:

```text
WIN-BYOD-001
```

The hostname was also verified from Command Prompt using:

```cmd
hostname
```

### Step 6: Checked Access Work or School Before Enrollment

Opened:

```text
Settings
-> Accounts
-> Access work or school
```

Before enrollment, no work or school account was connected.

---

## Enrollment Steps Performed

### Step 7: Added Work or School Account

On the Windows device, opened:

```text
Settings
-> Accounts
-> Access work or school
-> Connect
```

Signed in using:

```text
user03
```

The initial connection added the work account to the device.

Observed message:

```text
Account added to this device
```

### Step 8: Observed Work Account Connected Only

After the first connection, the account appeared as a work or school account, but the device management options were limited.

The account showed:

```text
Disconnect this account
Manage your account
```

This indicated that the account connection existed, but the Intune MDM management view was not yet visible.

### Step 9: Completed MDM Enrollment

The Windows MDM enrollment flow was then completed from Settings using:

```text
Settings
-> Accounts
-> Access work or school
-> Enroll only in device management
```

After enrollment, the device showed:

```text
Connected by user03
Connected to HomeLAB MDM
Managed by HomeLAB
```

### Step 10: Performed Manual Device Sync

Opened:

```text
Settings
-> Accounts
-> Access work or school
-> Managed by HomeLAB
-> Info
```

A manual sync was started from the device.

This confirmed the Windows device could communicate with Intune MDM.

---

## Intune Validation

### Step 11: Verified Device in Windows Devices List

Opened:

```text
Intune admin center
-> Devices
-> Windows
-> Windows devices
```

The device appeared in the Windows devices list as:

| Field | Result |
|---|---|
| Device name | WIN-BYOD-001 |
| Managed by | Intune |
| Ownership | Personal |
| Compliance | Compliant |
| OS | Windows |
| Primary user | user03 |

### Step 12: Verified Device Overview

Opened the device record for:

```text
WIN-BYOD-001
```

The device overview confirmed:

| Field | Result |
|---|---|
| Device name | WIN-BYOD-001 |
| Compliance | Compliant |
| Ownership | Personal |
| Management | Intune |
| Primary user | User 03 |
| OS | Windows |
| Manufacturer | Lenovo |

---

## Test Result

| Test Item | Result |
|---|---|
| user03 license assigned | Completed |
| user03 added to GRP-BYOD-Users | Completed |
| GRP-BYOD-Users added to MDM user scope | Completed |
| Windows personal enrollment allowed | Completed |
| WIN-BYOD-001 prepared | Completed |
| Work account added | Completed |
| MDM enrollment completed | Completed |
| Device sync completed | Completed |
| Device appeared in Intune | Completed |
| Device managed by Intune | Completed |
| Device ownership shown as Personal | Completed |
| Device compliance shown as Compliant | Completed |

Observed final result:

```text
WIN-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Windows BYOD device.
```

---

## Microsoft Entra ID Observation

The main validation for this lab was completed in Microsoft Intune.

During testing, the device was successfully shown in Intune as:

```text
Managed by: Intune
Ownership: Personal
Compliance: Compliant
Primary user: user03
```

The Microsoft Entra device record was not used as the primary validation point for this lab because the final working enrollment path used Windows MDM enrollment from Settings.

This is documented as a real-world observation:

```text
A Windows device can be successfully enrolled and managed in Intune even when the clearest validation evidence is available from the Intune device record rather than the Microsoft Entra device details page.
```

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/device-enrollment/
```

### User 03 license assignment

![User 03 license assignment](../screenshots/sanitized/device-enrollment/windows-byod-user03-license-sanitized.png)

### User 03 BYOD group membership

![User 03 BYOD group membership](../screenshots/sanitized/device-enrollment/windows-byod-user03-byod-group-membership-sanitized.png)

### Automatic MDM enrollment scope

![Automatic MDM enrollment scope](../screenshots/sanitized/device-enrollment/windows-byod-automatic-mdm-scope-sanitized.png)

### Windows BYOD platform restriction

![Windows BYOD platform restriction](../screenshots/sanitized/device-enrollment/windows-byod-platform-restriction-sanitized.png)

### Windows BYOD device name

![Windows BYOD device name](../screenshots/sanitized/device-enrollment/win-byod-001-device-about-sanitized.png)

### Access work or school before enrollment

![Access work or school before enrollment](../screenshots/sanitized/device-enrollment/win-byod-001-access-work-school-before-sanitized.png)

### Account added to device

![Account added to device](../screenshots/sanitized/device-enrollment/win-byod-001-account-added-sanitized.png)

### Work account connected only

![Work account connected only](../screenshots/sanitized/device-enrollment/win-byod-001-work-account-connected-only-sanitized.png)

### Access work or school after MDM enrollment

![Access work or school after MDM enrollment](../screenshots/sanitized/device-enrollment/win-byod-001-access-work-school-after-sanitized.png)

### Manual device sync

![Manual device sync](../screenshots/sanitized/device-enrollment/win-byod-001-manual-sync-sanitized.png)

### Windows BYOD device in Intune Windows devices list

![Windows BYOD device in Intune Windows devices list](../screenshots/sanitized/device-enrollment/win-byod-001-intune-windows-devices-list-sanitized.png)

### Windows BYOD Intune device overview

![Windows BYOD Intune device overview](../screenshots/sanitized/device-enrollment/win-byod-001-intune-overview-sanitized.png)

---

## Screenshot Files

```text
windows-byod-user03-license-sanitized.png
windows-byod-user03-byod-group-membership-sanitized.png
windows-byod-automatic-mdm-scope-sanitized.png
windows-byod-platform-restriction-sanitized.png
win-byod-001-device-about-sanitized.png
win-byod-001-access-work-school-before-sanitized.png
win-byod-001-account-added-sanitized.png
win-byod-001-work-account-connected-only-sanitized.png
win-byod-001-access-work-school-after-sanitized.png
win-byod-001-manual-sync-sanitized.png
win-byod-001-intune-windows-devices-list-sanitized.png
win-byod-001-intune-overview-sanitized.png
```

---

## Troubleshooting Notes

### Issue: Work account connected but Intune sync was not visible

During the first attempt, the account was added successfully, but the Access work or school page showed only a connected work account view.

Expected Intune management options such as device management information and sync were not immediately visible.

Resolution:

```text
Settings
-> Accounts
-> Access work or school
-> Enroll only in device management
```

After completing the MDM enrollment flow, the device showed:

```text
Connected to HomeLAB MDM
Managed by HomeLAB
```

The device then appeared in Intune as managed by Intune.

### Issue: Entra device details were not the main validation source

The primary validation for this BYOD lab was the Intune device record.

The device was confirmed as:

```text
Managed by: Intune
Ownership: Personal
Compliance: Compliant
Primary user: user03
```

This was sufficient to confirm successful Windows BYOD Intune enrollment.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload screenshots that show:

- Full real email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- MAC addresses
- Internal IP addresses
- Passwords
- MFA prompts
- QR codes
- Verification codes
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- User principal names
- Device serial number
- Intune device ID
- Microsoft Entra device ID
- Wi-Fi MAC address
- Ethernet MAC address
- IP address
- Any sensitive account or authentication information

---

## Related Labs

| Lab file | Relationship |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Provides `user03` and `GRP-BYOD-Users` |
| `02-device-enrollment/windows-oobe-enrollment.md` | Documents corporate-style Windows enrollment troubleshooting |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Documents corporate Autopilot enrollment |
| `02-device-enrollment/android-byod-enrollment.md` | Planned mobile BYOD enrollment lab |
| `02-device-enrollment/ios-byod-enrollment.md` | Planned mobile BYOD enrollment lab |

---

## Current Status

| Task | Status |
|---|---|
| windows-byod-enrollment.md created | Completed |
| User and group prerequisites verified | Completed |
| MDM user scope configured | Completed |
| Windows personal enrollment allowed | Completed |
| WIN-BYOD-001 enrolled | Completed |
| Device sync verified | Completed |
| Intune device list validation completed | Completed |
| Intune device overview validation completed | Completed |
| Screenshots added | Completed |

---

## Next Step

Continue with the next BYOD enrollment lab:

```text
02-device-enrollment/android-byod-enrollment.md
```

Recommended follow-on sequence:

```text
Android BYOD enrollment
-> iOS BYOD enrollment
-> BYOD compliance policy testing
-> Conditional Access BYOD testing
```
