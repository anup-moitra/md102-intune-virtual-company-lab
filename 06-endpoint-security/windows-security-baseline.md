# Windows Security Baseline

This file documents the planned Windows Security Baseline lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Create and test a Windows Security Baseline policy using Microsoft Intune.

This lab will validate that:

- A Windows Security Baseline can be created from Intune.
- Baseline settings can be reviewed before assignment.
- The baseline can be safely assigned to a pilot device group.
- The test device can report baseline status.
- Conflicts with existing endpoint security policies can be identified.

## Important Concept

A security baseline is a Microsoft-recommended collection of security settings.

Simple comparison:

```text
Individual endpoint security policy = one focused area, such as Firewall or BitLocker
Security baseline = a larger recommended security configuration package
```

Security baselines are useful, but they can overlap with other policies. In real environments, admins test them carefully to avoid conflicts.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Management | Microsoft Intune |
| Policy area | Endpoint security / Security baselines |
| Baseline type | Windows Security Baseline |
| Assignment group | `GRP-EndpointSecurity-Pilot-Devices` |
| Policy name | `WIN-CORP-Windows-Security-Baseline` |

## Prerequisites

Before starting:

- `WIN-CORP-001` should be Intune managed and compliant.
- Defender Antivirus, Firewall, BitLocker, and ASR audit labs should be reviewed first.
- A device-only pilot group should be used.
- Avoid broad assignment until conflicts are understood.

## Configuration Plan

| Setting | Planned configuration |
|---|---|
| Baseline name | `WIN-CORP-Windows-Security-Baseline` |
| Assignment | Device-only pilot group |
| Initial setting approach | Review defaults, avoid unnecessary changes |
| Conflict review | Required after deployment |

## Steps to Perform

### Step 1: Open Security Baselines

Go to:

```text
Intune admin center
→ Endpoint security
→ Security baselines
```

Select the available Windows security baseline, for example:

```text
Security Baseline for Windows 10 and later
```

or the currently available Windows security baseline profile in your tenant.

### Step 2: Create Profile

Select:

```text
Create profile
```

Name:

```text
WIN-CORP-Windows-Security-Baseline
```

Description:

```text
Applies Microsoft recommended Windows security baseline settings to the pilot Windows device group in the MD-102 Intune lab.
```

### Step 3: Review Baseline Settings

Review each section before creating the profile.

Common sections may include:

- Microsoft Defender settings
- Firewall settings
- Local security options
- Account protection
- Browser/security settings
- User rights/security options

For the first lab, keep defaults unless a setting clearly conflicts with an already-created lab policy.

### Step 4: Assign the Baseline

Assign only to:

```text
GRP-EndpointSecurity-Pilot-Devices
```

or another device-only pilot group containing only:

```text
WIN-CORP-001
```

Do not assign to:

```text
All users
All devices
Production users
```

### Step 5: Review and Create

Confirm:

- Baseline name
- Assignment group
- Scope tags
- Settings

Then select:

```text
Create
```

### Step 6: Sync the Device

Sync `WIN-CORP-001` from:

```text
Settings
→ Accounts
→ Access work or school
→ Info
→ Sync
```

or from Intune:

```text
Devices
→ Windows
→ WIN-CORP-001
→ Sync
```

### Step 7: Verify Status

Go to:

```text
Endpoint security
→ Security baselines
→ WIN-CORP-Windows-Security-Baseline
→ Monitor
→ Device status
```

Expected result:

```text
WIN-CORP-001 = Success / Succeeded
```

If conflicts appear, document them instead of ignoring them.

### Step 8: Review Conflicts

Check:

```text
Devices
→ Windows
→ WIN-CORP-001
→ Device configuration
```

Look for:

- Success
- Conflict
- Error
- Not applicable

Document any conflicts with earlier Defender, Firewall, BitLocker, or ASR policies.

## Test Result

| Test item | Result |
|---|---|
| Security baseline profile created | Pending |
| Baseline settings reviewed | Pending |
| Assigned to pilot device group | Pending |
| Device sync completed | Pending |
| Device status verified | Pending |
| Conflict review completed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/endpoint-security/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `security-baseline-profile-created-sanitized.png` | Pending | Add after lab execution and sanitization |
| `security-baseline-settings-review-sanitized.png` | Pending | Add after lab execution and sanitization |
| `security-baseline-assignment-sanitized.png` | Pending | Add after lab execution and sanitization |
| `security-baseline-review-create-sanitized.png` | Pending | Add after lab execution and sanitization |
| `security-baseline-device-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `security-baseline-conflict-review-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If the baseline shows errors or conflicts:

1. Review per-setting status.
2. Compare overlapping settings with existing endpoint security policies.
3. Check whether Firewall, Defender, BitLocker, or ASR settings are duplicated.
4. Decide which policy should own the setting.
5. Avoid assigning multiple policies that configure the same setting differently.

## Current Status

Planned.

## Next Step

Create the baseline only after the ASR audit policy lab has been documented.


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
