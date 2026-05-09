# Conditional Access Requiring Compliant Devices

This file documents the Conditional Access lab for requiring a compliant device before accessing Microsoft 365 resources.

## Objective

Test how Microsoft Entra Conditional Access works with Microsoft Intune device compliance.

This lab validates that:

- A managed and compliant corporate Windows device satisfies the Conditional Access requirement.
- An unmanaged or noncompliant BYOD device does not satisfy the Conditional Access requirement.
- Report-only mode can be used to safely test the policy without blocking users.

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company uses Microsoft Entra ID, Microsoft Intune, compliance policies, and Conditional Access to protect access to Microsoft 365 resources.

## Important Concept

Conditional Access does not decide by itself whether a device is healthy or secure.

Microsoft Intune checks the device using compliance policies. Microsoft Entra Conditional Access then uses that compliance result when a user tries to access company resources.

Simple flow:

```text
Device signs in to Microsoft 365
→ Microsoft Entra evaluates Conditional Access
→ Conditional Access checks whether a compliant device is required
→ Intune provides the device compliance result
→ Access decision is evaluated
```

In this lab, the Conditional Access policy is kept in Report-only mode. This means the policy result is recorded in sign-in logs, but the user is not actually blocked.

## Conditional Access Policy Details

| Setting | Value |
|---|---|
| Policy name | CA001 - Require compliant device for pilot users |
| Policy state | Report-only |
| Target resource | Office 365 |
| Grant control | Require device to be marked as compliant |
| Test user | User 01 |
| Compliant test device | WIN-CORP-001 |
| BYOD test device | WIN-BYOD-001 |

## Steps Performed

1. Verified WIN-CORP-001 was managed and compliant.
2. Created a Conditional Access policy in Microsoft Entra admin center.
3. Targeted pilot users.
4. Selected Office 365 as the target resource.
5. Configured the grant control to require compliant device.
6. Set the policy to Report-only.
7. Tested sign-in from WIN-CORP-001.
8. Reviewed sign-in logs and confirmed Report-only Success.
9. Tested sign-in from WIN-BYOD-001 while unmanaged/not enrolled.
10. Reviewed sign-in logs and confirmed Report-only Failure.

## Compliant Corporate Device Test Result

| Item | Result |
|---|---|
| User | User 01 |
| Device | WIN-CORP-001 |
| Managed | Yes |
| Compliant | Yes |
| Join type | Microsoft Entra joined / Azure AD joined |
| Browser | Edge |
| Operating system | Windows |
| Conditional Access result | Report-only: Success |

## Unmanaged BYOD Device Report-only Test

To validate the opposite scenario, the same Conditional Access policy was tested from a personal/BYOD Windows device.

The BYOD device was not enrolled in Intune and was used only to sign in to Microsoft 365 through the browser.

### Test Details

| Item | Value |
|---|---|
| Test user | User 01 |
| Test device | WIN-BYOD-001 |
| Device ownership | Personal/BYOD |
| Intune enrollment status | Not enrolled |
| Conditional Access policy | CA001 - Require compliant device for pilot users |
| Policy mode | Report-only |
| Target resource | Office 365 |
| Grant control | Require device to be marked as compliant |

### Expected Result

Because WIN-BYOD-001 was not enrolled in Intune, it did not have a valid compliant device status.

Expected Conditional Access result:

```text
Report-only: Failure
```

### Actual Result

The sign-in from WIN-BYOD-001 was successful because the policy was still in Report-only mode.

However, the Report-only tab showed that the compliant device requirement was not satisfied.

Result:

```text
CA001 - Require compliant device for pilot users
Grant control: Require compliant device
Result: Report-only: Failure
```

Device info showed:

```text
Compliant: No
Managed: No
```

This means the device would have been blocked if the policy was turned On.

## Result Summary

| Scenario | Device | Managed | Compliant | Conditional Access result |
|---|---|---|---|---|
| Corporate compliant device | WIN-CORP-001 | Yes | Yes | Report-only: Success |
| BYOD unmanaged device | WIN-BYOD-001 | No / Not enrolled | No / No valid compliance result | Report-only: Failure |

## Screenshots

### Conditional Access policy list

![Conditional Access policy list](../screenshots/sanitized/conditional-access/ca001-policy-list-report-only-sanitized.jpg)

### Conditional Access policy settings

![Conditional Access policy settings](../screenshots/sanitized/conditional-access/ca001-policy-settings-sanitized.jpg)

### User 01 sign-in log from compliant corporate device

![User 01 sign-in log](../screenshots/sanitized/conditional-access/user01-signin-log-sanitized.jpg)

### Device info showing compliant and managed corporate device

![Device info compliant managed](../screenshots/sanitized/conditional-access/device-info-compliant-managed-sanitized.jpg)

### Report-only success result for compliant corporate device

![Report-only success](../screenshots/sanitized/conditional-access/report-only-success-sanitized.jpg)

### BYOD device info showing unmanaged and not compliant device

![BYOD device info unmanaged](../screenshots/sanitized/conditional-access/byod-device-info-unmanaged-sanitized.jpg)

### BYOD report-only failure result

![Report-only failure BYOD](../screenshots/sanitized/conditional-access/report-only-failure-byod-sanitized.jpg)

## Screenshot Folder Path

All screenshots for this lab are stored in:

```text
screenshots/sanitized/conditional-access/
```

## Troubleshooting Notes

- If the Conditional Access policy does not appear in the sign-in log, confirm that the test user is included in the policy assignment.
- If the device does not show as compliant, confirm that the device is enrolled in Intune and has successfully synced.
- If no sign-in log appears immediately, wait a few minutes and refresh the sign-in logs.
- If a BYOD test device is allowed to sign in, remember that this is expected when the policy is in Report-only mode.
- For unmanaged BYOD testing, do not enroll the device before the test.

## Security Notes

This policy was kept in Report-only mode for safe testing.

Before turning this type of policy On in a real environment, an administrator should:

- Test with a pilot group first.
- Confirm at least one admin device is compliant.
- Exclude a break-glass emergency admin account.
- Confirm users have a clear path to enroll or fix noncompliant devices.
- Review sign-in logs and Conditional Access results.

## Current Lab Status

| Task | Status |
|---|---|
| Create Windows compliance policy | Completed |
| Confirm WIN-CORP-001 is managed | Completed |
| Confirm WIN-CORP-001 is compliant | Completed |
| Create Conditional Access policy requiring compliant device | Completed |
| Keep policy in Report-only mode | Completed |
| Test compliant corporate device sign-in | Completed |
| Confirm Report-only success result | Completed |
| Test unmanaged BYOD device sign-in | Completed |
| Confirm BYOD device shows Managed: No | Completed |
| Confirm BYOD device shows Compliant: No | Completed |
| Confirm Report-only failure result | Completed |
| Add sanitized screenshots | Completed / as available |

## Pending

- Decide whether to keep policy in Report-only or later move to On.
- Test a managed but noncompliant corporate device later.
- Document BYOD enrollment behavior later.

## Next Step

Continue with Autopilot verification, Microsoft 365 Apps validation, BYOD enrollment, or additional endpoint security labs.
