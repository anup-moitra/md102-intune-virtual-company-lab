# Conditional Access Enforced Mode Test

This file documents the planned Conditional Access enforced mode test for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Move a tested Conditional Access policy from Report-only mode to enforced mode in a controlled pilot test.

This lab will validate that:

- The policy works as expected before enforcement.
- Compliant devices are allowed.
- Unmanaged or noncompliant devices are blocked.
- Admin lockout risk is controlled.

## Existing Policy

| Item | Value |
|---|---|
| Policy name | `CA001 - Require compliant device for pilot users` |
| Current state | Report-only |
| Target user group | `GRP-Pilot-Users` |
| Target cloud app | Office 365 |
| Grant control | Require device to be marked as compliant |

## Safety Requirements

Before enabling the policy:

- Keep at least one emergency/break-glass admin account excluded.
- Do not target all users.
- Confirm report-only results are correct.
- Confirm compliant corporate device sign-in succeeds.
- Confirm unmanaged BYOD sign-in would fail.
- Do not enforce until you are ready to troubleshoot access issues.

## Steps to Perform

### Step 1: Review Report-only Results

Go to:

```text
Microsoft Entra admin center
→ Protection
→ Conditional Access
→ Insights and reporting
```

or:

```text
Microsoft Entra admin center
→ Sign-in logs
```

Confirm:

| Scenario | Expected report-only result |
|---|---|
| `WIN-CORP-001` compliant device | Success |
| `WIN-BYOD-001` unmanaged browser test | Failure |
| Managed noncompliant test device | Failure, if lab completed |

### Step 2: Confirm Exclusions

Open:

```text
CA001 - Require compliant device for pilot users
```

Confirm exclusions include:

- Break-glass admin account
- Any service accounts
- Any admin account needed for recovery

### Step 3: Change Policy State

Change:

```text
Report-only
```

to:

```text
On
```

### Step 4: Test Compliant Device Access

From `WIN-CORP-001`, sign in as:

```text
user01
```

Test:

- Office portal
- Outlook web
- Word/Excel app sign-in if needed

Expected result:

```text
Access allowed
```

### Step 5: Test Unmanaged BYOD Access

From `WIN-BYOD-001` or another unmanaged browser session, sign in as:

```text
user01
```

Expected result:

```text
Access blocked because device is not marked as compliant
```

### Step 6: Review Sign-in Logs

Go to:

```text
Microsoft Entra admin center
→ Sign-in logs
```

Check the Conditional Access tab for each test.

Document:

- Policy applied
- Grant control result
- Device compliance state
- Final access result

### Step 7: Roll Back if Needed

If access impact is unexpected, change the policy state back to:

```text
Report-only
```

## Test Result

| Test item | Result |
|---|---|
| Report-only results reviewed | Pending |
| Break-glass/admin exclusions confirmed | Pending |
| Policy changed to On | Pending |
| Compliant device access allowed | Pending |
| Unmanaged BYOD access blocked | Pending |
| Sign-in logs reviewed | Pending |
| Rollback plan confirmed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/conditional-access/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `ca-enforced-policy-state-on-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ca-enforced-compliant-device-success-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ca-enforced-unmanaged-byod-blocked-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ca-enforced-sign-in-logs-compliant-sanitized.png` | Pending | Add after lab execution and sanitization |
| `ca-enforced-sign-in-logs-blocked-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If compliant devices are blocked:

1. Confirm device is Intune managed.
2. Confirm device is compliant.
3. Confirm primary user and sign-in user match where required.
4. Check sign-in logs Conditional Access details.
5. Confirm the user is in the included group.
6. Confirm no conflicting Conditional Access policy is applying.
7. Temporarily return policy to Report-only if needed.

## Current Status

Planned.

## Next Step

Perform only after report-only testing and noncompliant testing are documented.


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
