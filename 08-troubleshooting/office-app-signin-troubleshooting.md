# Office App Sign-in Troubleshooting

This file documents Microsoft 365 Apps sign-in troubleshooting for the MD-102 Intune lab.

## Status

Documentation template prepared / use during troubleshooting

## Objective

Create a repeatable checklist for troubleshooting Word, Excel, PowerPoint, and other Microsoft 365 Apps sign-in issues after Intune deployment.

This guide helps troubleshoot:

- Office apps installed but user cannot sign in
- License activation issues
- Wrong account signed into Office
- Company Portal shows installed but Office activation fails
- Conditional Access blocks Office app access

## Lab Context

Earlier Microsoft 365 Apps deployment testing used:

```text
user01
WIN-AUTOPILOT-001
Microsoft 365 Apps deployment through Intune
Word sign-in verification
```

## Basic Troubleshooting Flow

```text
Check license
→ Check app install status
→ Check Office account
→ Check Conditional Access
→ Check device compliance
→ Sign out/in
→ Repair/reinstall if needed
```

## Step 1: Check License Assignment

Go to:

```text
Microsoft 365 admin center
→ Users
→ Active users
→ user01
→ Licenses and apps
```

Confirm Microsoft 365 Apps entitlement exists through the assigned license.

## Step 2: Check Intune App Install Status

Go to:

```text
Intune admin center
→ Apps
→ Windows
→ Microsoft 365 Apps policy
→ Device install status
```

Confirm the device shows:

```text
Installed
```

## Step 3: Check Company Portal

On the device, open:

```text
Company Portal
→ Downloads & updates
```

Confirm Microsoft 365 Apps status.

## Step 4: Check Office Account

Open Word.

Go to:

```text
File
→ Account
```

Confirm signed-in user:

```text
user01
```

Check whether Office says:

```text
Product Activated
```

or shows an activation/sign-in issue.

## Step 5: Check Conditional Access

If sign-in fails, check:

```text
Microsoft Entra admin center
→ Sign-in logs
```

Review the sign-in event for:

- Conditional Access result
- Device compliance
- Grant control result
- Error code

## Step 6: Sign Out and Sign In Again

In Office:

```text
File
→ Account
→ Sign out
→ Sign in again
```

Use:

```text
user01
```

## Step 7: Repair Office if Needed

If the app is installed but broken:

```text
Settings
→ Apps
→ Installed apps
→ Microsoft 365 Apps
→ Modify
→ Quick Repair
```

Use Online Repair only if needed.

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/troubleshooting/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `office-signin-license-check-sanitized.png` | Pending | Hide full email and tenant details |
| `office-signin-intune-install-status-sanitized.png` | Pending | Hide user/device IDs |
| `office-signin-company-portal-status-sanitized.png` | Pending | Hide full email |
| `office-signin-word-account-page-sanitized.png` | Pending | Hide full email |
| `office-signin-entra-signin-log-sanitized.png` | Pending | Hide IDs and full UPN |

## Troubleshooting Result Template

| Item | Result |
|---|---|
| License verified | Pending |
| App install status checked | Pending |
| Company Portal checked | Pending |
| Office account page checked | Pending |
| Conditional Access logs checked | Pending |
| Issue resolved | Pending |

## Current Status

Ready for future troubleshooting use.


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
