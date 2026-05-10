# Device Sync Remote Actions

This file documents the planned Intune device sync and basic remote actions lab.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Use Microsoft Intune remote actions to sync a Windows device and verify that policy/app status updates after check-in.

This lab will validate that:

- A remote sync can be triggered from Intune.
- A local sync can be triggered from Windows settings.
- Device check-in time updates.
- Policy status can be reviewed after sync.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Management | Microsoft Intune |
| Remote action | Sync |
| Local action | Access work or school sync |
| Test user | `user01` |

## Important Concept

Intune devices check in automatically, but admins can trigger a sync when testing policies.

```text
Policy created in Intune
→ Device checks in
→ Policy applies
→ Status reports back to Intune
```

Remote sync is useful during troubleshooting and lab validation.

## Steps to Perform

### Step 1: Check Current Device Status

Go to:

```text
Intune admin center
→ Devices
→ Windows
→ WIN-CORP-001
```

Record:

- Last check-in
- Compliance status
- Ownership
- Management state

### Step 2: Trigger Remote Sync from Intune

Select:

```text
Sync
```

Confirm the action.

### Step 3: Trigger Local Sync from Windows

On `WIN-CORP-001`:

```text
Settings
→ Accounts
→ Access work or school
→ Connected work/school account
→ Info
→ Sync
```

### Step 4: Verify Check-in Update

Return to Intune and refresh the device page.

Check:

- Last check-in time
- Device status
- Policy status if testing a policy

### Step 5: Review Device Action Status

If available, check:

```text
Devices
→ Monitor
→ Device actions
```

Confirm the sync action was sent or completed.

## Test Result

| Test item | Result |
|---|---|
| Current device status reviewed | Pending |
| Remote sync triggered from Intune | Pending |
| Local sync triggered from Windows | Pending |
| Last check-in updated | Pending |
| Device action status reviewed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `device-sync-before-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-sync-remote-action-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-sync-local-windows-settings-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-sync-after-check-in-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-sync-device-action-status-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If sync does not update:

1. Confirm device has internet access.
2. Confirm Intune Management Extension is running if app/script status is involved.
3. Restart the device.
4. Check Company Portal.
5. Review device check-in time after waiting several minutes.

## Current Status

Planned.

## Next Step

Perform after ASR or Security Baseline testing when a fresh policy check-in is needed.


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
