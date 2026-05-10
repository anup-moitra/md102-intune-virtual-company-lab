# Managed Noncompliant Device Test

This file documents the planned managed but noncompliant device test for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Test how Conditional Access behaves when a device is managed by Intune but does not meet compliance requirements.

This lab will validate the difference between:

```text
Unmanaged device = not enrolled
Managed noncompliant device = enrolled, but failing compliance
Managed compliant device = enrolled and passing compliance
```

## Lab Environment

| Item | Planned value |
|---|---|
| Test user | `user01` |
| Test device | Dedicated test device, not primary production/lab device |
| Compliance policy | Temporary noncompliance test policy |
| Conditional Access policy | `CA001 - Require compliant device for pilot users` |
| Policy mode | Report-only first |
| Expected result | Managed noncompliant device fails compliant device requirement |

## Safety Note

Do not intentionally break compliance on your main working device unless you are comfortable recovering it.

Recommended safer approach:

```text
Use a separate test device or temporary test policy assigned only to a test group.
```

## Important Concept

Conditional Access can require a device to be marked as compliant.

A device can be:

| Device state | Meaning |
|---|---|
| Unmanaged | Intune does not manage the device |
| Managed noncompliant | Intune manages it, but compliance policy fails |
| Managed compliant | Intune manages it and compliance policy passes |

This lab proves that **managed** and **compliant** are not the same thing.

## Steps to Perform

### Step 1: Prepare a Test Group

Create or confirm a test group:

```text
GRP-Noncompliant-Test-Devices
```

Add only the test device.

Do not add broad groups.

### Step 2: Create Temporary Compliance Test Policy

Go to:

```text
Intune admin center
→ Devices
→ Compliance policies
→ Create policy
```

Choose:

```text
Platform: Windows 10 and later
```

Create a temporary policy that the test device will fail.

Example safe options:

- Require a setting that is not currently met on the test device
- Use a temporary test-only rule
- Avoid destructive changes

Policy name:

```text
WIN-Test-Temporary-Noncompliance-Policy
```

### Step 3: Assign Only to Test Device Group

Assign only to:

```text
GRP-Noncompliant-Test-Devices
```

### Step 4: Sync the Device

Sync the test device from:

```text
Settings
→ Accounts
→ Access work or school
→ Info
→ Sync
```

### Step 5: Verify Noncompliance

Go to:

```text
Intune admin center
→ Devices
→ Windows devices
→ Test device
→ Compliance
```

Expected result:

```text
Noncompliant
```

### Step 6: Test Conditional Access in Report-only Mode

Attempt sign-in to the target cloud app as:

```text
user01
```

Then check:

```text
Microsoft Entra admin center
→ Sign-in logs
→ Report-only
```

Expected result:

```text
CA001 requires compliant device
Device is managed but noncompliant
Access would fail
```

### Step 7: Clean Up Test Policy

After documenting the result, remove or unassign the temporary compliance test policy.

## Test Result

| Test item | Result |
|---|---|
| Test device group created | Pending |
| Temporary compliance policy created | Pending |
| Test device became noncompliant | Pending |
| Conditional Access report-only result reviewed | Pending |
| Cleanup completed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/compliance/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `managed-noncompliant-test-policy-sanitized.png` | Pending | Add after lab execution and sanitization |
| `managed-noncompliant-device-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `managed-noncompliant-ca-report-only-result-sanitized.png` | Pending | Add after lab execution and sanitization |
| `managed-noncompliant-cleanup-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If the device does not become noncompliant:

1. Confirm policy assignment.
2. Sync the device.
3. Wait for compliance evaluation.
4. Check per-setting compliance details.
5. Confirm no grace period is delaying the result.

## Current Status

Planned.

## Next Step

Perform after BYOD or when a safe separate test device is available.


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
