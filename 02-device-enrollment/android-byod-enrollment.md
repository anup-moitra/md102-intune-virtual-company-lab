# Android BYOD Enrollment

This file documents the planned Android BYOD enrollment lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Enroll a personally owned Android device using Android Enterprise personally owned work profile.

This lab will validate that:

- Android BYOD enrollment is available in Intune.
- A work profile can be created on a personal Android device.
- Work apps and personal apps are separated.
- The device can appear in Intune.
- Corporate data can be managed without fully managing the personal side of the device.

## Important Concept

Android personally owned work profile separates work and personal data.

```text
Personal side = user owns and controls
Work profile = managed by organization
```

This is a common modern BYOD approach because it protects company data while respecting personal privacy.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `ANDROID-BYOD-001` |
| Ownership | Personal/BYOD |
| User | `user01` |
| Enrollment type | Android Enterprise personally owned work profile |
| Management | Microsoft Intune |
| User group | `GRP-Mobile-Users` or `GRP-BYOD-Users` |

## Prerequisites

Before starting:

- Android enrollment should be enabled in Intune.
- The user should have an Intune license.
- Company Portal should be installed from Google Play.
- Android Enterprise connector/settings should be available.
- A test Android device should be used.

## Steps to Perform

### Step 1: Confirm User Group

Confirm `user01` is in:

```text
GRP-Mobile-Users
```

or:

```text
GRP-BYOD-Users
```

### Step 2: Check Android Enrollment Availability

Go to:

```text
Intune admin center
→ Devices
→ Android
→ Android enrollment
```

Confirm Android Enterprise personally owned work profile enrollment is available.

### Step 3: Install Company Portal

On the Android device:

```text
Google Play Store
→ Install Company Portal
```

### Step 4: Start Enrollment

Open Company Portal and sign in as:

```text
user01
```

Follow prompts to:

- Create work profile
- Accept management permissions
- Install required work apps
- Complete registration

### Step 5: Verify Work Profile

On the Android device, confirm:

- Work profile exists
- Work apps have the work badge
- Company Portal appears in the work profile
- Personal apps remain separate

### Step 6: Verify Device in Intune

Go to:

```text
Intune admin center
→ Devices
→ Android devices
```

Check:

- Device name
- User
- Ownership
- Compliance
- Last check-in
- Management type

### Step 7: Test Work App Access

Open a work app or Company Portal from the work profile and confirm the user is signed in.

## Test Result

| Test item | Result |
|---|---|
| Android enrollment settings checked | Pending |
| Company Portal installed | Pending |
| Work profile created | Pending |
| Device appeared in Intune | Pending |
| Ownership/compliance reviewed | Pending |
| Work/personal separation verified | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/device-enrollment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `android-byod-company-portal-signin-sanitized.png` | Pending | Add after lab execution and sanitization |
| `android-byod-work-profile-created-sanitized.png` | Pending | Add after lab execution and sanitization |
| `android-byod-work-apps-sanitized.png` | Pending | Add after lab execution and sanitization |
| `android-byod-intune-device-overview-sanitized.png` | Pending | Add after lab execution and sanitization |
| `android-byod-compliance-status-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If Android enrollment fails:

1. Confirm the user has an Intune license.
2. Confirm Android enrollment is enabled.
3. Confirm Company Portal is updated.
4. Check internet connectivity.
5. Remove partial work profile and retry if setup gets stuck.
6. Review Intune device enrollment failures.

## Current Status

Planned.

## Next Step

Perform after Windows BYOD enrollment or when an Android test device is available.


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
