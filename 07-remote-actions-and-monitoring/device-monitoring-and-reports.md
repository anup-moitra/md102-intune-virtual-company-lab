# Device Monitoring and Reports

This file documents the planned device monitoring and reporting lab for Microsoft Intune.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Review Intune device monitoring views and reports for enrolled Windows devices.

This lab will validate that:

- Device inventory can be reviewed.
- Compliance status can be checked.
- Configuration policy status can be reviewed.
- App install status can be reviewed.
- Endpoint security status can be reviewed.
- Reports can be used for troubleshooting.

## Lab Environment

| Item | Planned value |
|---|---|
| Devices | `WIN-CORP-001`, `WIN-AUTOPILOT-001` |
| Management | Microsoft Intune |
| Report areas | Devices, Compliance, Configuration, Apps, Endpoint security |

## Important Concept

Monitoring is how an Intune admin proves whether a policy actually worked.

```text
Configuration created
→ Assignment completed
→ Device checks in
→ Report shows success, error, conflict, or pending
```

## Steps to Perform

### Step 1: Review Windows Device List

Go to:

```text
Intune admin center
→ Devices
→ Windows devices
```

Review:

- Device name
- Compliance
- Ownership
- Last check-in
- Primary user

### Step 2: Review Device Overview

Open:

```text
WIN-CORP-001
```

Review:

- Overview
- Hardware
- Discovered apps
- Device compliance
- Device configuration
- Managed apps

### Step 3: Review Compliance Reports

Go to:

```text
Devices
→ Monitor
→ Device compliance
```

Check compliance status for:

```text
WIN-CORP-001
WIN-AUTOPILOT-001
```

### Step 4: Review Configuration Profile Status

Go to:

```text
Devices
→ Configuration
```

Open a completed policy and review:

- Device status
- User status
- Per-setting status if available

### Step 5: Review App Install Status

Go to:

```text
Apps
→ Monitor
→ App install status
```

Review status for:

- Company Portal
- 7-Zip
- Microsoft 365 Apps
- Other deployed apps

### Step 6: Review Endpoint Security Status

Go to:

```text
Endpoint security
```

Review completed policies:

- Defender Antivirus
- Windows Firewall
- BitLocker
- ASR after future testing
- Security Baseline after future testing

## Test Result

| Test item | Result |
|---|---|
| Windows device list reviewed | Pending |
| Device overview reviewed | Pending |
| Compliance report reviewed | Pending |
| Configuration profile status reviewed | Pending |
| App install status reviewed | Pending |
| Endpoint security status reviewed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `monitoring-windows-device-list-sanitized.png` | Pending | Add after lab execution and sanitization |
| `monitoring-win-corp-001-overview-sanitized.png` | Pending | Add after lab execution and sanitization |
| `monitoring-device-compliance-report-sanitized.png` | Pending | Add after lab execution and sanitization |
| `monitoring-configuration-profile-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `monitoring-app-install-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `monitoring-endpoint-security-status-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If report data looks stale:

1. Sync the device.
2. Wait for Intune reporting delay.
3. Check last check-in time.
4. Confirm the device is online.
5. Review per-setting status instead of only summary status.

## Current Status

Planned.

## Next Step

Perform after more endpoint security policies are created.


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
