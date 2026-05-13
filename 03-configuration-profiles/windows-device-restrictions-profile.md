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
- USB/removable storage access can be tested on the endpoint.
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
| Current lab status | In progress |

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

Before starting this lab, the following should already be completed:

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

This keeps the restriction limited to a controlled pilot corporate device instead of applying it broadly to all users or all devices.

---

### Step 5: Created the Configuration Profile

The profile was reviewed and created in Microsoft Intune.

Created policy:

```text
CFG-WIN-Block-USB-Storage
```

---

### Step 6: Checked Initial Policy Assignment Status

Initial Intune assignment status showed:

```text
Device: WINAUTO452
Assignment status: Pending
```

This means the device had not yet fully checked in and reported the final policy result at the time of review.

---

## Current Test Result

| Test Item | Result |
|---|---|
| Settings catalog profile created | Completed |
| USB/removable storage restriction setting found | Completed |
| All Removable Storage classes: Deny all access configured | Completed |
| Policy assigned to pilot group | Completed |
| Target device listed in assignment report | Completed |
| Initial device assignment status | Pending |
| Manual sync completed | Pending |
| USB storage blocked on endpoint | Pending |
| Final Intune policy status verified | Pending |
| Final lab result | In progress |

---

## Expected Result

After the device checks in and receives the policy:

- `WINAUTO452` should receive the Intune configuration profile.
- The profile status should eventually change from `Pending` to `Success`.
- Removable USB storage access should be blocked on the endpoint.
- A user should not be able to open or use removable storage normally.
- The result should be documented with sanitized screenshots.

Expected endpoint behavior:

```text
USB drive appears but access is denied
or
USB drive cannot be opened
or
Windows blocks removable storage access
```

---

## Validation Steps

### Step 1: Sync the Target Device

On `WINAUTO452`, sync the device from Windows Settings:

```text
Settings
-> Accounts
-> Access work or school
-> Connected work account
-> Info
-> Sync
```

Alternative Intune sync path:

```text
Intune admin center
-> Devices
-> Windows
-> WINAUTO452
-> Sync
```

---

### Step 2: Restart the Device

Restart:

```text
WINAUTO452
```

Then sign in again and wait several minutes for policy processing.

---

### Step 3: Refresh Intune Policy Report

In Intune, open:

```text
Devices
-> Configuration
-> CFG-WIN-Block-USB-Storage
-> Device assignment status
```

Click:

```text
Generate again
```

Expected final status:

```text
Success
```

---

### Step 4: Test USB Storage Access

On `WINAUTO452`:

1. Insert a USB flash drive.
2. Open File Explorer.
3. Try to open the removable drive.
4. Confirm whether access is blocked.

Expected result:

```text
USB/removable storage access is blocked.
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

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, top-right signed-in account details, and sensitive identifiers were hidden.

---

## Uploaded Screenshot Files

The following screenshots have been uploaded and linked:

```text
windows-usb-storage-block-create-profile-sanitized.png
windows-usb-storage-block-settings-picker-sanitized.png
windows-usb-storage-block-setting-enabled-sanitized.png
windows-usb-storage-block-assignment-sanitized.png
```

---

## Pending Screenshots

The following screenshots should be added after final policy validation:

```text
windows-usb-storage-block-device-status-success-sanitized.png
windows-usb-storage-block-manual-sync-sanitized.png
windows-usb-storage-block-endpoint-after-test-sanitized.png
```

Optional screenshot if captured before policy enforcement:

```text
windows-usb-storage-block-endpoint-before-test-sanitized.png
```

---

## Troubleshooting Notes

### Policy shows Pending

If the policy shows:

```text
Assignment status: Pending
```

Possible causes:

1. The target device has not checked in with Intune yet.
2. The Intune report has not refreshed yet.
3. The device was offline.
4. The policy was recently created and needs more time.
5. The target device is not correctly included in the assigned group.

Recommended actions:

1. Confirm `WINAUTO452` is in `GRP-Autopilot-Devices`.
2. Sync the device manually.
3. Restart the device.
4. Wait 5-15 minutes.
5. Click `Generate again` in the Intune report.
6. Recheck the policy assignment status.

### USB is still accessible after policy assignment

If USB storage remains accessible:

1. Confirm the setting is configured as `Enabled`.
2. Confirm the policy is assigned to the correct group.
3. Confirm the device is included in the assigned group.
4. Perform a manual sync.
5. Restart the device.
6. Test again after sign-in.
7. Check policy status in Intune.
8. Review local event logs if needed.

### Policy applies but testing is unclear

Some USB devices may present differently depending on hardware type.

Test with a simple USB flash drive if possible.

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
| Initial policy status | Pending |
| Manual sync validation | Pending |
| Endpoint USB test | Pending |
| Final Intune success status | Pending |
| Final validation screenshots added | Pending |

---

## Next Step

Complete validation on the target device:

```text
Sync WINAUTO452
Restart WINAUTO452
Generate Intune report again
Confirm policy status changes from Pending to Success
Test USB flash drive access
Capture sanitized screenshots
Update this file from In progress to Completed
```

After validation, update the final test result and screenshot links.
