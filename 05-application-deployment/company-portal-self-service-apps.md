# Company Portal Self-Service Apps

This file documents the planned Company Portal self-service app deployment lab.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Publish selected apps as **Available** in Company Portal so users can install them on demand.

This lab will validate that:

- Apps can be assigned as Available.
- Users can see apps in Company Portal.
- Users can install self-service apps.
- Install status can be verified in Intune.

## Important Concept

Intune app assignments can be:

| Assignment type | Meaning |
|---|---|
| Required | App installs automatically |
| Available | User can install from Company Portal |
| Uninstall | App is removed |

Self-service apps reduce unnecessary automatic installs and give users controlled choice.

## Lab Environment

| Item | Planned value |
|---|---|
| Test user | `user01` |
| Test device | `WIN-CORP-001` or `WIN-AUTOPILOT-001` |
| Assignment group | `GRP-Pilot-Users` |
| App delivery | Company Portal |
| Assignment type | Available |

## Candidate Apps

Use safe test apps already deployed or available in the tenant.

Examples:

- ChatGPT
- VLC
- 7-Zip
- Other approved lab apps

## Steps to Perform

### Step 1: Choose App

Go to:

```text
Intune admin center
→ Apps
→ Windows
```

Select an app to publish as Available.

### Step 2: Configure Assignment

Open:

```text
Properties
→ Assignments
→ Edit
```

Add group:

```text
GRP-Pilot-Users
```

Assignment type:

```text
Available for enrolled devices
```

### Step 3: Sync Device

On the test device:

```text
Settings
→ Accounts
→ Access work or school
→ Info
→ Sync
```

### Step 4: Open Company Portal

On the test device, open:

```text
Company Portal
```

Confirm the app appears as available.

### Step 5: Install App from Company Portal

Select the app and install it.

### Step 6: Verify Install Status

Check:

```text
Intune admin center
→ Apps
→ App
→ Monitor
→ Device install status
```

Expected result:

```text
Installed
```

## Test Result

| Test item | Result |
|---|---|
| App selected | Pending |
| Available assignment configured | Pending |
| App visible in Company Portal | Pending |
| User-installed app from Company Portal | Pending |
| Intune install status verified | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/application-deployment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `company-portal-available-assignment-sanitized.png` | Pending | Add after lab execution and sanitization |
| `company-portal-app-visible-sanitized.png` | Pending | Add after lab execution and sanitization |
| `company-portal-app-install-started-sanitized.png` | Pending | Add after lab execution and sanitization |
| `company-portal-app-installed-sanitized.png` | Pending | Add after lab execution and sanitization |
| `company-portal-intune-install-status-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If app does not appear in Company Portal:

1. Confirm the app is assigned as Available.
2. Confirm user is in the assigned group.
3. Sync the device.
4. Restart Company Portal.
5. Check Company Portal account.
6. Wait for Intune app catalog refresh.

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
