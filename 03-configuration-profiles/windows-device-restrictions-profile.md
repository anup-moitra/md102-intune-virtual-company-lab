# Windows Device Restrictions Profile

## Lab status

**Status:** Completed  
**Lab category:** Configuration profiles  
**Platform:** Windows 10 and later  
**Management platform:** Microsoft Intune  
**Target endpoint:** WINAUTO452  
**Primary user:** user01  
**Target group:** GRP-Autopilot-Devices  
**Configuration profile name:** CFG-WIN-Block-USB-Storage  

---

## Lab objective

The objective of this lab is to create a Windows device restrictions configuration profile in Microsoft Intune to block access to removable USB storage devices on a corporate Windows test device.

This lab validates that:

- A Windows Settings catalog profile can be created in Microsoft Intune.
- A removable storage restriction can be configured through Intune.
- The policy can be assigned to a pilot device group.
- The target Windows device can receive the policy after Intune sync.
- USB/removable storage access can be blocked on the endpoint.
- Policy status can be reviewed from the Intune admin center.

Final result:

```text
USB/removable storage access was blocked successfully on WINAUTO452.
```

---

## Why this lab matters

In real organizations, administrators may need to prevent users from copying company data to USB flash drives or external removable storage.

Blocking removable storage helps reduce the risk of:

- Data leakage
- Unauthorized file copying
- Malware transfer through USB devices
- Loss of sensitive company data

This lab demonstrates a common endpoint security and device restriction scenario using Microsoft Intune.

In a real environment, this type of policy is usually deployed carefully to pilot groups first because removable storage restrictions can affect user workflows.

---

## Lab environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Profile type | Settings catalog |
| Platform | Windows 10 and later |
| Policy name | `CFG-WIN-Block-USB-Storage` |
| Target group | `GRP-Autopilot-Devices` |
| Test device | `WINAUTO452` |
| Device ownership | Corporate |
| Device enrollment type | Windows Autopilot |
| Primary user | `user01` |
| Current lab status | Completed |

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

## Deployment / Configuration flow

Simple deployment flow:

```text
Create Intune Settings catalog profile
-> Configure removable storage restriction
-> Assign policy to pilot device group
-> Sync target Windows device
-> Verify policy status in Intune
-> Test USB storage access on endpoint
```

Policy configuration summary:

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

## Steps performed

### Step 1: Opened Microsoft Intune admin center

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

### Step 2: Configured profile basics

Policy name configured as:

```text
CFG-WIN-Block-USB-Storage
```

Description:

```text
Blocks access to removable USB storage devices on corporate Windows pilot devices.
```

---

### Step 3: Added removable storage restriction setting

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

### Step 4: Assigned policy to pilot device group

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

### Step 5: Created the configuration profile

The profile was reviewed and created in Microsoft Intune.

Created policy:

```text
CFG-WIN-Block-USB-Storage
```

---

### Step 6: Verified initial policy assignment status

Initial Intune assignment status showed the target device as pending.

This was expected because the device had not yet fully checked in and reported the final policy result at the time of first review.

---

### Step 7: Verified policy success in Intune

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

### Step 8: Tested USB storage access on endpoint

A removable USB storage device was connected to `WINAUTO452`.

When attempting to open the removable drive, Windows displayed:

```text
D:\ is not accessible.
Access is denied.
```

This confirmed that removable USB storage access was blocked successfully.

---

## Validation

Validation was completed in two places:

1. Microsoft Intune policy reporting
2. Windows endpoint user experience

### Intune validation

The Intune device status report showed:

```text
Check-in status: Success
Succeeded: 1
Error: 0
Conflict: 0
Not applicable: 0
In progress: 0
```

### Endpoint validation

The removable USB drive was visible in File Explorer, but access was blocked when the user attempted to open the drive.

Observed message:

```text
D:\ is not accessible.
Access is denied.
```

---

## Final test result

| Validation item | Status |
|---|---|
| Settings catalog profile created | Completed |
| USB/removable storage restriction setting found | Completed |
| All Removable Storage classes: Deny all access configured | Completed |
| Policy assigned to pilot group | Completed |
| Target device listed in assignment report | Completed |
| Policy status changed from pending to success | Completed |
| USB storage blocked on endpoint | Completed |
| Final Intune policy status verified | Completed |
| Endpoint validation completed | Completed |
| Final lab result | Completed |

Observed endpoint behavior:

```text
D:\ is not accessible.
Access is denied.
```

---

## Screenshots captured

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

### Uploaded screenshot files

```text
windows-usb-storage-block-create-profile-sanitized.png
windows-usb-storage-block-settings-picker-sanitized.png
windows-usb-storage-block-setting-enabled-sanitized.png
windows-usb-storage-block-assignment-sanitized.png
windows-usb-storage-block-device-status-success-sanitized.png
windows-usb-storage-block-endpoint-after-test-sanitized.png
```

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, top-right signed-in account details, and sensitive identifiers were hidden.

---

## Troubleshooting notes

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

### Testing reminder

When testing removable storage restrictions, use a controlled pilot device first.

This type of restriction should not be broadly deployed without testing because it can affect users who rely on removable storage for business workflows.

---

## Enterprise reflection

In a real corporate environment, blocking USB storage can be part of a broader data protection strategy.

This type of control may be used alongside:

- Microsoft Defender for Endpoint
- Microsoft Purview Data Loss Prevention
- BitLocker encryption
- Endpoint security baselines
- Attack Surface Reduction rules
- Conditional Access
- Device compliance policies

A recommended enterprise rollout approach would be:

```text
Pilot group
-> IT validation
-> Business stakeholder review
-> Limited production ring
-> Broad production rollout
```

Important production considerations:

| Consideration | Why it matters |
|---|---|
| Pilot testing | Confirms the policy does not disrupt required workflows |
| Exception handling | Some users or departments may require removable storage |
| User communication | Users should understand why removable storage is blocked |
| Monitoring | Admins should track policy success, errors, and conflicts |
| Data protection alignment | USB blocking should support broader security and compliance goals |

For this lab, the policy was assigned only to the Autopilot test device group:

```text
GRP-Autopilot-Devices
```

This follows a safer pilot-based deployment approach.

---

## Security and privacy notes

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

## Key learning outcomes

This lab demonstrated:

- How to create a Windows Settings catalog configuration profile in Microsoft Intune.
- How to find removable storage settings under Administrative Templates.
- How to enable `All Removable Storage classes: Deny all access`.
- How to assign a configuration profile to a pilot device group.
- How to validate Intune policy success from the admin center.
- How to test policy behavior directly on a Windows endpoint.
- How to document endpoint validation with sanitized screenshots.
- Why USB storage blocking should be deployed carefully in production environments.

---

## Lab conclusion

The Windows device restrictions profile was completed successfully.

Final result:

```text
CFG-WIN-Block-USB-Storage applied successfully to WINAUTO452.
The device reported policy success in Microsoft Intune.
Removable USB storage access was blocked on the endpoint.
Windows displayed: D:\ is not accessible. Access is denied.
```
