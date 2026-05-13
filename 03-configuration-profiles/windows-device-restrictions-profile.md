# Windows Device Restrictions Profile

This file documents a Microsoft Intune device configuration profile used to block removable USB storage access on a corporate Windows test device.

---

## Objective

Create a Windows device restrictions configuration profile in Microsoft Intune to block access to removable USB storage devices on a pilot corporate Windows device.

This lab validates that:

- A Windows Settings catalog profile can be created in Microsoft Intune.
- A removable storage restriction can be configured through Intune.
- The policy can be assigned to a pilot device group.
- The target Windows device can receive the policy after Intune sync.
- USB/removable storage access can be blocked on the endpoint.
- Policy status can be reviewed from the Intune admin center.

---

## Why This Lab Matters

In real organizations, administrators may need to prevent users from copying company data to USB flash drives or external removable storage.

Blocking removable storage helps reduce the risk of:

- Data leakage
- Unauthorized file copying
- Malware transfer through USB devices
- Loss of sensitive company data

This lab demonstrates a common endpoint security and device restriction scenario using Microsoft Intune.

Simple flow:

```text
Create Intune configuration profile
-> Configure removable storage restriction
-> Assign policy to pilot device group
-> Sync target Windows device
-> Test USB storage access
-> Verify policy status in Intune
```

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Profile type | Settings catalog |
| Platform | Windows 10 and later |
| Policy name | CFG-WIN-Block-USB-Storage |
| Target group | GRP-Autopilot-Devices |
| Test device | WINAUTO452 |
| Device ownership | Corporate |
| Device enrollment type | Windows Autopilot |
| Primary user | user01 |
| Current lab status | Completed |

---

## Policy Summary

| Setting | Value |
|---|---|
| Category | Administrative Templates |
| Subcategory | System > Removable Storage Access |
| Setting name | All Removable Storage classes: Deny all access |
| Configured value | Enabled |
| Purpose | Block access to removable storage devices |

When enabled, this setting denies access to removable storage classes on the target Windows device.

Examples of removable storage that may be affected:

```text
USB flash drives
External USB storage drives
SD cards
Removable media presented as storage
```

This policy is not intended to block normal USB input devices such as:

```text
USB keyboard
USB mouse
USB headset
USB webcam
```

---

## Prerequisites

Before starting this lab, the following were completed:

- Microsoft Entra ID users created.
- Microsoft Entra ID groups created.
- Windows Autopilot device enrolled.
- Test device `WINAUTO452` available in Microsoft Intune.
- `GRP-Autopilot-Devices` group available.
- `WINAUTO452` included in the target assignment group.
- Device able to sync with Microsoft Intune.
- A USB flash drive or removable storage device available for testing.

---

## Steps Performed

### Step 1: Opened Microsoft Intune Admin Center

Opened:

```text
https://intune.microsoft.com
```

Navigation used:

```text
Devices
-> Configuration
-> Create
-> New policy
```

Selected:

```text
Platform: Windows 10 and later
Profile type: Settings catalog
```

---

### Step 2: Configured Basics

Policy name configured as:

```text
CFG-WIN-Block-USB-Storage
```

Description:

```text
Blocks access to removable USB storage devices on corporate Windows pilot devices.
```

---

### Step 3: Added Removable Storage Restriction Setting

Navigation used inside the Settings catalog:

```text
Administrative Templates
-> System
-> Removable Storage Access
```

Search term used:

```text
All Removable Storage classes: Deny all access
```

Configured setting:

```text
All Removable Storage classes: Deny all access
```

Configured value:

```text
Enabled
```

This setting was selected to block removable storage access on the target Windows device.

---

### Step 4: Assigned Policy to Pilot Device Group

The policy was assigned to:

```text
GRP-Autopilot-Devices
```

Target test device:

```text
WINAUTO452
```

This kept the restriction limited to a controlled pilot corporate device instead of applying it broadly to all users or all devices.

---

### Step 5: Created the Configuration Profile

The profile was reviewed and created in Microsoft Intune.

Created policy:

```text
CFG-WIN-Block-USB-Storage
```

---

### Step 6: Verified Initial Policy Assignment Status

Initial Intune assignment status showed the target device as pending.

This was expected because the device had not yet fully checked in and reported the final policy result at the time of first review.

---

### Step 7: Verified Policy Success in Intune

After device check-in and report refresh, the Intune policy report showed:

```text
Device: WINAUTO452
Check-in status: Success
Succeeded: 1
Error: 0
Conflict: 0
Not applicable: 0
In progress: 0
```

This confirmed that the USB storage block policy was successfully delivered to the target Windows device.

---

### Step 8: Tested USB Storage Access on Endpoint

A removable USB storage device was connected to `WINAUTO452`.

When attempting to open the removable drive, Windows displayed:

```text
D:\ is not accessible.
Access is denied.
```

This confirmed that removable USB storage access was blocked successfully.

---

## Test Result

| Test Item | Result |
|---|---|
| Settings catalog profile created | Completed |
| USB/removable storage restriction setting found | Completed |
| All Removable Storage classes: Deny all access configured | Completed |
| Policy assigned to pilot group | Completed |
| Target device listed in assignment report | Completed |
| Policy status changed from pending to success | Completed |
| USB storage blocked on endpoint | Completed |
| Final Intune policy status verified | Completed |
| Final lab result | Completed |

---

## Expected Result

After this lab:

- `WINAUTO452` received the Intune configuration profile.
- The profile status changed to `Success`.
- Removable USB storage access was blocked on the endpoint.
- A user could not open the removable USB drive.
- The result was documented with sanitized screenshots.

Observed endpoint behavior:

```text
D:\ is not accessible.
Access is denied.
```

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/configuration-profiles/
```

### Create Windows Settings Catalog Profile

![Create Windows Settings Catalog Profile](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-create-profile-sanitized.png)

### Settings Picker - Removable Storage Access

![Settings Picker - Removable Storage Access](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-settings-picker-sanitized.png)

### USB Storage Block Setting Enabled

![USB Storage Block Setting Enabled](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-setting-enabled-sanitized.png)

### Assignment to Autopilot Device Group

![Assignment to Autopilot Device Group](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-assignment-sanitized.png)

### Intune Device Status Success

![Intune Device Status Success](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-device-status-success-sanitized.png)

### Endpoint USB Access Denied Test

![Endpoint USB Access Denied Test](../screenshots/sanitized/configuration-profiles/windows-usb-storage-block-endpoint-after-test-sanitized.png)

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, top-right signed-in account details, and sensitive identifiers were hidden.

---

## Uploaded Screenshot Files

The following screenshots were uploaded and linked:

```text
windows-usb-storage-block-create-profile-sanitized.png
windows-usb-storage-block-settings-picker-sanitized.png
windows-usb-storage-block-setting-enabled-sanitized.png
windows-usb-storage-block-assignment-sanitized.png
windows-usb-storage-block-device-status-success-sanitized.png
windows-usb-storage-block-endpoint-after-test-sanitized.png
```

---

## Troubleshooting Notes

### Policy initially showed Pending

The policy initially showed:

```text
Assignment status: Pending
```

This was expected because the target device had not yet checked in and reported the final policy result.

Recommended actions used:

1. Confirmed `WINAUTO452` was included in `GRP-Autopilot-Devices`.
2. Waited for device check-in/report refresh.
3. Checked the Intune device configuration profile status again.

Final result:

```text
Check-in status: Success
```

### Endpoint USB access test

The endpoint validation confirmed that a removable USB drive was visible in File Explorer, but access was denied when the user attempted to open it.

Observed message:

```text
D:\ is not accessible.
Access is denied.
```

This confirmed the policy worked as expected.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload screenshots that show:

- Full user email addresses
- Tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Internal IP addresses
- MAC addresses
- Recovery keys
- Passwords
- MFA prompts
- Unsanitized device details

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device identifiers
- Serial numbers
- Any private endpoint details

---

## Current Status

| Task | Status |
|---|---|
| windows-device-restrictions-profile.md created | Completed |
| Device restriction profile created | Completed |
| USB storage block setting configured | Completed |
| Policy assigned to pilot device group | Completed |
| Initial screenshots added | Completed |
| Target device appears in assignment report | Completed |
| Final Intune success status | Completed |
| Endpoint USB access denied test | Completed |
| Final validation screenshots added | Completed |
| Lab completed | Completed |

---

## Next Step

This lab is completed.

Recommended next configuration/profile lab:

```text
03-configuration-profiles/windows-corporate-wallpaper-policy.md
```

Recommended next new lab option:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

or:

```text
02-device-enrollment/android-byod-enrollment.md
```
