# Windows BYOD Enrollment

This file documents the planned Windows BYOD enrollment lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Enroll a personally owned Windows device into Microsoft Intune and compare it with an unmanaged BYOD browser sign-in test.

This lab will validate that:

- A personal Windows device can be connected to work or school.
- The device can enroll into Intune as a BYOD device.
- The device can appear in Intune with personal ownership.
- Compliance and Conditional Access behavior can be compared against the earlier unmanaged BYOD test.

## Important Concept

Windows BYOD enrollment is different from corporate enrollment.

```text
Corporate OOBE enrollment = company-owned device, stronger management
Windows BYOD enrollment = personal device, lighter management and careful privacy boundaries
```

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-BYOD-002` |
| Ownership | Personal/BYOD |
| User | `user01` |
| Enrollment method | Access work or school / Company Portal |
| Join/registration type | Microsoft Entra registered or workplace joined |
| Management | Microsoft Intune |
| Assignment group | `GRP-BYOD-Users` |

## Prerequisites

Before starting:

- `user01` should have an Intune license.
- Automatic MDM enrollment should be configured.
- BYOD enrollment restrictions should allow Windows personal device enrollment.
- The test device should not contain production data.
- Screenshots must be sanitized before upload.

## Steps to Perform

### Step 1: Confirm BYOD User Group

Confirm `user01` is a member of:

```text
GRP-BYOD-Users
```

### Step 2: Confirm Enrollment Restrictions

Go to:

```text
Intune admin center
→ Devices
→ Enrollment
→ Enrollment device platform restrictions
```

Confirm Windows personal device enrollment is allowed for the test user/group.

### Step 3: Start Enrollment on Windows BYOD Device

On `WIN-BYOD-002`, go to:

```text
Settings
→ Accounts
→ Access work or school
→ Connect
```

Sign in as:

```text
user01
```

Choose the work/school connection flow.

### Step 4: Complete Company Portal Setup if Required

If Windows prompts for Company Portal:

1. Install/open Company Portal.
2. Sign in with `user01`.
3. Complete device setup.
4. Allow the device to register/enroll.

### Step 5: Verify Device in Intune

Go to:

```text
Intune admin center
→ Devices
→ Windows devices
```

Look for:

```text
WIN-BYOD-002
```

Check:

- Management state
- Ownership
- Compliance
- Primary user
- Last check-in

Expected ownership:

```text
Personal
```

### Step 6: Verify Local Work/School Connection

On the BYOD device:

```text
Settings
→ Accounts
→ Access work or school
```

Confirm the work account is connected.

### Step 7: Compare Against Unmanaged BYOD Test

Compare with earlier:

```text
WIN-BYOD-001 = unmanaged browser sign-in test
```

Expected learning outcome:

```text
Unmanaged BYOD = fails compliant device requirement
Enrolled BYOD = can be evaluated by Intune compliance policy
```

## Test Result

| Test item | Result |
|---|---|
| BYOD user group confirmed | Pending |
| Enrollment restrictions checked | Pending |
| Windows BYOD enrollment started | Pending |
| Device appeared in Intune | Pending |
| Ownership reviewed | Pending |
| Compliance reviewed | Pending |
| Conditional Access behavior compared | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/device-enrollment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `windows-byod-enrollment-start-sanitized.png` | Pending | Add after lab execution and sanitization |
| `windows-byod-access-work-school-connected-sanitized.png` | Pending | Add after lab execution and sanitization |
| `windows-byod-company-portal-setup-sanitized.png` | Pending | Add after lab execution and sanitization |
| `windows-byod-intune-device-overview-sanitized.png` | Pending | Add after lab execution and sanitization |
| `windows-byod-ownership-compliance-sanitized.png` | Pending | Add after lab execution and sanitization |
| `windows-byod-ca-comparison-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If enrollment fails:

1. Confirm the user has an Intune license.
2. Confirm MDM user scope includes the user.
3. Confirm Windows personal enrollment is allowed.
4. Check Company Portal status.
5. Check `Settings → Accounts → Access work or school`.
6. Check Intune enrollment failures under troubleshooting.

## Current Status

Planned.

## Next Step

Perform Windows BYOD enrollment after endpoint security pilot labs or when a safe personal test device is available.


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
