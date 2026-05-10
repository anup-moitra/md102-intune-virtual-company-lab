# Restart, Retire, and Wipe Remote Actions

This file documents planned Intune remote action testing for Restart, Retire, and Wipe.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Understand and document Intune remote actions for Windows devices.

This lab will validate safe use of:

- Restart
- Retire
- Wipe

## Safety Warning

`Restart` is generally safe.

`Retire` and `Wipe` can remove management data or reset the device.

Do not perform Retire or Wipe on a device you still need unless you are intentionally testing cleanup or reset behavior.

Recommended first lab:

```text
Test Restart only
Document Retire and Wipe as planned/simulated until a disposable test device is available
```

## Important Concept

| Remote action | Meaning | Risk level |
|---|---|---|
| Restart | Restarts the device | Low |
| Retire | Removes company data and management from device | Medium |
| Wipe | Factory resets the device | High |

## Lab Environment

| Item | Planned value |
|---|---|
| Safe test device for Restart | `WIN-CORP-001` |
| Safe test device for Retire/Wipe | Disposable test device only |
| Management | Microsoft Intune |
| Documentation approach | Restart tested first, Retire/Wipe documented carefully |

## Steps to Perform: Restart

### Step 1: Open Device

Go to:

```text
Intune admin center
→ Devices
→ Windows
→ WIN-CORP-001
```

### Step 2: Select Restart

Select:

```text
Restart
```

Confirm the action.

### Step 3: Verify Device Restarted

On the device, confirm the device restarts.

After restart, sign in and check:

```text
Settings
→ Accounts
→ Access work or school
```

### Step 4: Review Device Action Status

Go to:

```text
Devices
→ Monitor
→ Device actions
```

Confirm restart action status.

## Steps to Perform: Retire

Only perform on a safe disposable BYOD test device.

Expected result:

```text
Intune management is removed
Company data is removed where applicable
Personal data remains
```

## Steps to Perform: Wipe

Only perform on a disposable test device.

Expected result:

```text
Device resets to factory/OOBE state
Data is removed
Device must be re-enrolled if needed
```

## Test Result

| Test item | Result |
|---|---|
| Restart action triggered | Pending |
| Device restarted successfully | Pending |
| Device action status reviewed | Pending |
| Retire action reviewed but not performed | Pending |
| Wipe action reviewed but not performed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `restart-remote-action-sanitized.png` | Pending | Add after lab execution and sanitization |
| `restart-device-action-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `retire-action-screen-review-only-sanitized.png` | Pending | Add after lab execution and sanitization |
| `wipe-action-screen-review-only-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If restart does not occur:

1. Confirm the device is online.
2. Confirm last check-in time.
3. Trigger sync.
4. Wait several minutes.
5. Check device action status.

## Current Status

Planned.

## Next Step

Perform Restart first. Save Retire/Wipe for a disposable test device.


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

Before uploading screenshots, blur or hide:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs / object IDs / serial numbers
- Any recovery keys, tokens, or QR codes
