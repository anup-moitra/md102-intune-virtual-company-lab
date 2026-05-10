# Autopilot Motherboard Replacement Troubleshooting

This file documents a planned troubleshooting scenario for Windows Autopilot after motherboard replacement or hardware identity change.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Understand how Autopilot registration can be affected when a device motherboard is replaced or the hardware hash changes.

This scenario will document:

- Why Autopilot identity may change
- How to remove or update stale Autopilot records
- How to collect a new hardware hash
- How to reimport and reassign an Autopilot profile

## Important Concept

Windows Autopilot identifies devices using hardware identity.

If the motherboard is replaced, the hardware identity can change.

Simple flow:

```text
Old motherboard
→ Old hardware hash registered
→ Motherboard replaced
→ New hardware identity
→ Old Autopilot registration may no longer match
→ New hash may need to be collected and imported
```

## Lab Scenario

| Item | Planned value |
|---|---|
| Scenario type | Simulated troubleshooting |
| Device | Autopilot test device |
| Issue | Device no longer receives expected Autopilot profile |
| Cause | Hardware identity changed or stale Autopilot record |
| Resolution | Remove stale record, collect/import new hash, reassign profile |

## Steps to Troubleshoot

### Step 1: Identify the Autopilot Device Record

Go to:

```text
Intune admin center
→ Devices
→ Windows
→ Windows enrollment
→ Devices
```

Search for the device.

Review:

- Serial number
- Group tag
- Profile status
- Assigned profile
- Associated Microsoft Entra device

Do not upload serial numbers or hardware hashes.

### Step 2: Check Profile Assignment

Confirm whether the device has:

```text
Profile status: Assigned
```

If not assigned, check group membership and dynamic/static group rules.

### Step 3: Remove Stale Record if Needed

If the old hardware identity is no longer valid, remove the stale Autopilot record only after confirming it is safe.

Document:

```text
Old Autopilot record reviewed
Stale record removed if required
```

### Step 4: Collect New Hardware Hash

On the device at OOBE or Windows, collect a new hardware hash using the approved lab method.

Do not upload the hardware hash CSV to GitHub.

### Step 5: Import New Hardware Hash

Go to:

```text
Intune admin center
→ Devices
→ Windows
→ Windows enrollment
→ Devices
→ Import
```

Import the new CSV.

### Step 6: Add Device to Autopilot Group

Add the device to:

```text
GRP-Autopilot-Devices
```

### Step 7: Wait for Profile Assignment

Wait until:

```text
Profile status: Assigned
```

### Step 8: Test Autopilot OOBE Again

Restart/reset the device to OOBE and confirm:

- Autopilot profile downloads
- User sign-in appears
- Device joins Microsoft Entra ID
- Device enrolls into Intune

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/troubleshooting/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `autopilot-troubleshooting-old-record-sanitized.png` | Pending | Hide serial number and IDs |
| `autopilot-troubleshooting-profile-not-assigned-sanitized.png` | Pending | Hide device identifiers |
| `autopilot-troubleshooting-new-import-sanitized.png` | Pending | Hide serial/hash details |
| `autopilot-troubleshooting-profile-assigned-sanitized.png` | Pending | Hide device identifiers |
| `autopilot-troubleshooting-oobe-success-sanitized.png` | Pending | Hide tenant/user details |

## Troubleshooting Result Template

| Item | Result |
|---|---|
| Old Autopilot record reviewed | Pending |
| New hardware hash collected | Pending |
| New hardware hash imported | Pending |
| Device added to Autopilot group | Pending |
| Profile assigned | Pending |
| OOBE retest completed | Pending |

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
