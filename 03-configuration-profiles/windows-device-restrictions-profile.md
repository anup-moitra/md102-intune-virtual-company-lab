# Windows Device Restrictions Profile

This file documents the planned Windows device restrictions configuration profile lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Create a Windows device restrictions profile using Intune Settings catalog or Templates.

This lab will validate that:

- Device restriction settings can be configured in Intune.
- A safe pilot assignment can be used.
- Settings can be reviewed on the test device.
- User impact can be documented before broader rollout.

## Important Concept

Device restrictions are configuration settings that limit or control Windows features.

Examples:

- Control access to device settings
- Restrict consumer experiences
- Configure privacy or cloud content settings
- Limit certain user actions

For a lab, use non-destructive settings first.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Platform | Windows 10 and later |
| Profile type | Settings catalog |
| Assignment | `GRP-Pilot-Users` or pilot device group |
| Policy name | `WIN-CORP-Device-Restrictions-Profile` |

## Safe First Settings

Choose a small number of safe settings first.

Example setting areas:

| Area | Example lab purpose |
|---|---|
| Start menu / taskbar | Test user experience policy |
| Microsoft consumer experiences | Reduce consumer features |
| Cloud content | Reduce suggestions |
| Control Panel / Settings visibility | Test restrictions carefully |

Do not block critical admin tools on your only test device unless you have a recovery plan.

## Steps to Perform

### Step 1: Create Configuration Profile

Go to:

```text
Intune admin center
→ Devices
→ Configuration
→ Create
→ New policy
```

Select:

```text
Platform: Windows 10 and later
Profile type: Settings catalog
```

### Step 2: Name the Profile

Policy name:

```text
WIN-CORP-Device-Restrictions-Profile
```

Description:

```text
Configures selected Windows device restriction settings for pilot testing in the MD-102 Intune lab.
```

### Step 3: Add Settings

Select:

```text
Add settings
```

Choose safe settings for the first test.

Document each configured setting in a table.

### Step 4: Assign to Pilot

Assign to a small pilot group only.

Recommended:

```text
GRP-Pilot-Users
```

or a pilot device group.

### Step 5: Sync and Verify

Sync `WIN-CORP-001`.

Check the local Windows behavior for the configured restrictions.

## Configured Settings

| Setting | Planned value | Result |
|---|---|---|
| TBD | TBD | Pending |

## Test Result

| Test item | Result |
|---|---|
| Profile created | Pending |
| Settings configured | Pending |
| Assigned to pilot group | Pending |
| Device synced | Pending |
| Local behavior verified | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/configuration-profiles/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `device-restrictions-profile-created-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-restrictions-settings-configured-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-restrictions-assignment-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-restrictions-device-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `device-restrictions-local-verification-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If settings do not apply:

1. Confirm assignment.
2. Sync the device.
3. Check device configuration status.
4. Check per-setting status.
5. Restart the device if needed.

## Current Status

Planned.


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
