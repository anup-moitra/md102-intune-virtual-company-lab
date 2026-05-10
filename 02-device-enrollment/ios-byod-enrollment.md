# iOS BYOD Enrollment

This file documents the planned iOS BYOD enrollment lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Enroll a personally owned iPhone/iOS device into Microsoft Intune using a BYOD-friendly enrollment method.

This lab will validate that:

- iOS/iPadOS enrollment prerequisites are configured.
- A personal iOS device can enroll through Company Portal or user enrollment.
- The device appears in Intune.
- Corporate access can be protected while respecting personal privacy.

## Important Concept

iOS BYOD management should avoid treating personal devices like corporate devices.

```text
Corporate iOS device = stronger management, often supervised
Personal iOS BYOD = lighter management, privacy-aware controls
```

For a learning lab, the goal is to understand the enrollment flow and privacy boundary.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `IOS-BYOD-001` |
| Ownership | Personal/BYOD |
| User | `user01` |
| Enrollment type | User enrollment / Company Portal enrollment |
| Management | Microsoft Intune |
| User group | `GRP-Mobile-Users` or `GRP-BYOD-Users` |

## Prerequisites

Before starting:

- User has an Intune license.
- Apple MDM push certificate is configured in Intune if required.
- iOS/iPadOS enrollment is allowed.
- Company Portal is available from the App Store.
- A test iPhone/iPad is available.

## Steps to Perform

### Step 1: Check iOS/iPadOS Enrollment Prerequisites

Go to:

```text
Intune admin center
→ Devices
→ iOS/iPadOS
→ iOS/iPadOS enrollment
```

Confirm the required Apple MDM push certificate/enrollment settings are configured.

### Step 2: Confirm User Group

Confirm `user01` is in:

```text
GRP-Mobile-Users
```

or:

```text
GRP-BYOD-Users
```

### Step 3: Install Company Portal

On the iOS device:

```text
App Store
→ Install Company Portal
```

### Step 4: Start Enrollment

Open Company Portal and sign in as:

```text
user01
```

Follow the prompts to enroll the device.

Depending on the tenant configuration, this may include:

- Download management profile
- Open Settings
- Install management profile
- Trust remote management profile
- Return to Company Portal

### Step 5: Verify Device in Intune

Go to:

```text
Intune admin center
→ Devices
→ iOS/iPadOS devices
```

Check:

- Device name
- User
- Ownership
- Compliance
- Last check-in
- Management type

### Step 6: Verify User Experience

On the iOS device, confirm:

- Work account is connected
- Company Portal shows setup complete
- Required apps or available apps appear if assigned

## Test Result

| Test item | Result |
|---|---|
| iOS enrollment prerequisites checked | Pending |
| Company Portal installed | Pending |
| iOS enrollment started | Pending |
| Management profile installed | Pending |
| Device appeared in Intune | Pending |
| Compliance/ownership reviewed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/device-enrollment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `ios-byod-company-portal-signin-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ios-byod-management-profile-install-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ios-byod-company-portal-complete-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ios-byod-intune-device-overview-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ios-byod-compliance-status-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If iOS enrollment fails:

1. Confirm Apple MDM push certificate is active.
2. Confirm the user has an Intune license.
3. Confirm iOS personal enrollment is allowed.
4. Check Company Portal prompts.
5. Remove old management profiles and retry if needed.
6. Check Intune enrollment failure reports.

## Current Status

Planned.

## Next Step

Perform when an iOS test device is available.


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
