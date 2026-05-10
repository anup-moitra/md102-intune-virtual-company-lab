# Conditional Access Troubleshooting

This file documents common Conditional Access troubleshooting steps for the MD-102 Intune lab.

## Status

Documentation template prepared / use during troubleshooting

## Objective

Create a repeatable checklist for troubleshooting Conditional Access policy behavior.

This guide helps troubleshoot:

- Unexpected access blocks
- Report-only failures
- Compliant device requirement failures
- User/group targeting issues
- Conditional Access policy conflicts

## Important Concept

Conditional Access decisions depend on many signals:

```text
User
Device
App
Location
Risk
Client app
Compliance state
Policy assignments
Grant controls
```

Always check the sign-in logs before guessing.

## Basic Troubleshooting Flow

```text
Find failed sign-in
→ Open Conditional Access tab
→ Check policy result
→ Check grant controls
→ Check device compliance
→ Check included/excluded users
→ Check report-only vs enforced state
```

## Step 1: Review Sign-in Logs

Go to:

```text
Microsoft Entra admin center
→ Monitoring
→ Sign-in logs
```

Filter by:

```text
User: user01
Application: Office 365 / tested app
Status: Failure or Success
```

Open the sign-in event.

## Step 2: Review Conditional Access Tab

In the sign-in event, open:

```text
Conditional Access
```

Review:

- Policies applied
- Policies not applied
- Result
- Grant controls
- Session controls

## Step 3: Check Device Details

In the sign-in log, review device details:

- Device ID
- Managed state
- Compliance state
- Join type
- Browser/client app

Do not upload device IDs to GitHub.

## Step 4: Check Policy Assignments

Open the policy:

```text
CA001 - Require compliant device for pilot users
```

Check:

- Included users/groups
- Excluded users/groups
- Target cloud apps
- Conditions
- Grant controls
- Policy state

## Step 5: Use What If Tool

Go to:

```text
Microsoft Entra admin center
→ Protection
→ Conditional Access
→ What If
```

Test:

- User
- Cloud app
- Device platform
- Client app
- Location if used

## Step 6: Compare Expected vs Actual

| Scenario | Expected result |
|---|---|
| Compliant `WIN-CORP-001` | Allowed |
| Unmanaged `WIN-BYOD-001` | Blocked or report-only failure |
| Managed noncompliant device | Blocked or report-only failure |
| Excluded admin account | Policy not applied |

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/troubleshooting/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `ca-troubleshooting-sign-in-log-sanitized.png` | Pending | Hide user details and IDs |
| `ca-troubleshooting-ca-tab-sanitized.png` | Pending | Hide IDs and full UPN |
| `ca-troubleshooting-device-details-sanitized.png` | Pending | Hide device ID |
| `ca-troubleshooting-policy-assignments-sanitized.png` | Pending | Hide tenant/account |
| `ca-troubleshooting-what-if-sanitized.png` | Pending | Hide user and tenant details |

## Troubleshooting Result Template

| Item | Result |
|---|---|
| Sign-in log reviewed | Pending |
| Conditional Access tab reviewed | Pending |
| Device compliance checked | Pending |
| Policy assignment checked | Pending |
| What If tool used | Pending |
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
