# Collect Diagnostics

This file documents the planned Intune Collect diagnostics lab.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Use the Intune **Collect diagnostics** remote action to gather troubleshooting data from a managed Windows device.

This lab will validate that:

- Diagnostics collection can be triggered from Intune.
- The device receives the action.
- Diagnostic collection status can be monitored.
- Diagnostic packages can support troubleshooting.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Management | Microsoft Intune |
| Remote action | Collect diagnostics |
| Use case | Troubleshooting policy/app/enrollment issues |

## Important Concept

Collect diagnostics helps admins gather logs from a managed device without physically accessing it.

This is useful for:

- Enrollment issues
- Policy application failures
- App installation issues
- Intune Management Extension troubleshooting
- Windows update or security policy troubleshooting

## Steps to Perform

### Step 1: Open the Device

Go to:

```text
Intune admin center
→ Devices
→ Windows
→ WIN-CORP-001
```

### Step 2: Start Collect Diagnostics

Select:

```text
Collect diagnostics
```

Confirm the action.

### Step 3: Wait for Collection

The device must be online and able to check in.

Wait for the action to process.

### Step 4: Review Device Action Status

Go to:

```text
Devices
→ Monitor
→ Device actions
```

Check the status of the diagnostics action.

### Step 5: Download or Review Diagnostic Package

When available, download or review the diagnostic package.

Do not upload diagnostic packages to the public repository.

### Step 6: Document High-Level Result Only

For GitHub, document only:

- Action started
- Action completed
- Package available
- No sensitive logs uploaded

## Test Result

| Test item | Result |
|---|---|
| Device selected | Pending |
| Collect diagnostics triggered | Pending |
| Device action status reviewed | Pending |
| Diagnostic package availability confirmed | Pending |
| Sensitive package not uploaded | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `collect-diagnostics-action-started-sanitized.png` | Pending | Add after lab execution and sanitization |
| `collect-diagnostics-device-action-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `collect-diagnostics-package-available-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If diagnostics collection does not complete:

1. Confirm the device is online.
2. Trigger device sync.
3. Restart the device.
4. Wait for check-in.
5. Check device action status again.
6. Confirm the account has permission to collect diagnostics.

## Current Status

Planned.

## Next Step

Perform when troubleshooting logs are needed for a future failed or delayed lab result.


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
