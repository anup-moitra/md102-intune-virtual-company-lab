# Conditional Access Enforced Mode Test

## Lab status

| Item | Status |
|---|---|
| Lab | Conditional Access Enforced Mode Test |
| Section | 04 - Compliance and Conditional Access |
| Platform | Microsoft Entra ID / Microsoft Intune |
| Policy type | Conditional Access policy |
| Enforced policy name | `CA-WIN-Require-Compliant-Device-Enforced` |
| Previous report-only policy | `CA-WIN-Require-Compliant-Device-ReportOnly` |
| Policy state during test | On |
| Target user group | `GRP-BYOD-Users` |
| Test user | `user03` |
| Test device | `WIN-BYOD-001` |
| Device compliance state | Noncompliant |
| Target resource | Office 365 / Microsoft Teams Services |
| Device platform | Windows |
| Grant control | Require device to be marked as compliant |
| Final result | Completed successfully |
| Validation result | Access blocked for noncompliant device |

---

## Lab objective

The objective of this lab was to test a Microsoft Entra Conditional Access policy in **enforced mode**.

In the previous Conditional Access lab, the policy was tested in **Report-only** mode. Report-only mode is useful because it shows what would happen without actually blocking the user.

In this lab, the policy was enabled so that Microsoft Entra ID could actively block access when the Windows device was not compliant.

This lab validates the real enforcement flow:

```text
User signs in to Microsoft 365 from Windows BYOD device
        ↓
Microsoft Entra ID evaluates Conditional Access policy
        ↓
Policy checks user, target resource, and Windows platform
        ↓
Policy requires a compliant device
        ↓
Device is noncompliant in Intune
        ↓
Access is blocked
```

---

## Why this lab matters

Conditional Access in Report-only mode is only a simulation. It helps administrators confirm the policy result before enforcement.

Conditional Access in **On** mode is different because it actively controls access. If the device does not satisfy the configured grant control, the sign-in can be blocked.

This is important in real environments because organizations often want to protect Microsoft 365 apps from unhealthy, unmanaged, or noncompliant devices.

A user may know the correct password, but access should still be denied if the device does not meet security requirements.

---

## Lab environment

| Component | Value |
|---|---|
| Microsoft Entra tenant | HomeLAB |
| Intune tenant | Home lab Intune environment |
| Test user | `user03` |
| User group | `GRP-BYOD-Users` |
| Test device | `WIN-BYOD-001` |
| Device ownership | Personal / BYOD |
| Device management | Microsoft Intune |
| Device compliance state | Noncompliant |
| Protected resource | Office 365 / Microsoft Teams Services |
| Conditional Access policy | `CA-WIN-Require-Compliant-Device-Enforced` |
| Policy mode during validation | On |
| Grant control | Require device to be marked as compliant |
| Result | Blocked because device was not compliant |

---

## Prerequisites

Before starting this enforced mode test, the following items were already completed:

- `WIN-BYOD-001` was enrolled into Microsoft Intune.
- `user03` was available as the BYOD test user.
- `user03` was a member of `GRP-BYOD-Users`.
- `WIN-BYOD-001` was intentionally marked noncompliant in Intune.
- The previous Report-only Conditional Access lab was completed.
- Microsoft Entra sign-in logs were available for validation.
- The policy was scoped to a test group, not all users.
- The administrator account used for recovery was not the blocked test user.

---

## Important safety note

Enforced Conditional Access policies can block real access.

In this lab, the policy was scoped to a controlled test group:

```text
GRP-BYOD-Users
```

The policy was not applied to all users. This reduces the risk of accidentally locking out administrators or other accounts.

In a real environment, always exclude or protect emergency admin access before enabling Conditional Access policies.

---

## Configuration summary

| Area | Configuration |
|---|---|
| Policy name | `CA-WIN-Require-Compliant-Device-Enforced` |
| Users | Specific users included |
| Included group | `GRP-BYOD-Users` |
| Target resources | Office 365 |
| Network | Not configured |
| Conditions | Device platform |
| Device platform | Windows |
| Grant control | Require device to be marked as compliant |
| Session control | Not configured |
| Policy state during creation | Report-only |
| Policy state during enforcement test | On |

---

## Step 1 - Confirm the BYOD device is noncompliant

Before enforcing the Conditional Access policy, the BYOD Windows device was checked in Microsoft Intune.

The test device was:

```text
WIN-BYOD-001
```

The device showed as:

```text
Noncompliant
```

This confirmed that the device should fail the `Require compliant device` grant control.

![BYOD device noncompliant](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-01-byod-device-noncompliant.png)

---

## Step 2 - Configure users and group assignment

A new Conditional Access policy was created for enforced testing.

The policy was scoped to the BYOD test group:

```text
GRP-BYOD-Users
```

This group contains the BYOD test user:

```text
user03
```

![Users group selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-02-users-group-selected.png)

### Why this group was used

The purpose of this lab was to test access from the noncompliant BYOD Windows device.

Using `GRP-BYOD-Users` kept the policy targeted and avoided affecting unrelated users.

---

## Step 3 - Configure target resource

The target resource was configured as:

```text
Office 365
```

This means the policy applies to Microsoft 365 services such as Teams, Office web apps, and related Microsoft 365 resources.

![Target resource Office 365](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-03-target-resource-office365.png)

---

## Step 4 - Configure device platform condition

The device platform condition was configured for:

```text
Windows
```

This kept the policy focused on Windows sign-ins.

![Device platform Windows](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-04-device-platform-windows.png)

### Why Windows was selected

The test device in this lab was a Windows BYOD device.

Scoping the policy to Windows made the test result easier to understand because Android, iOS, macOS, and Linux sign-ins were not part of this lab.

---

## Step 5 - Configure grant control

The grant control was configured as:

```text
Require device to be marked as compliant
```

This tells Microsoft Entra ID to allow access only when the device is reported as compliant by Microsoft Intune.

![Grant require compliant device](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-05-grant-require-compliant-device.png)

### What this setting means

The policy does not simply check whether the user knows the password.

It also checks whether the device meets compliance requirements from Intune.

For this lab:

```text
WIN-BYOD-001 = Noncompliant
```

So the expected enforced result was:

```text
Access blocked
```

---

## Step 6 - Review policy before creation

Before creation, the policy summary was reviewed.

The policy was initially kept in:

```text
Report-only
```

This is a safer way to confirm the policy settings before changing it to enforcement mode.

![Policy summary report-only before create](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-06-policy-summary-report-only-before-create.png)

---

## Step 7 - Confirm policy creation

After creation, the policy appeared in the Conditional Access policy list.

The new policy was:

```text
CA-WIN-Require-Compliant-Device-Enforced
```

At this stage, it was still shown as Report-only.

![Policy created report-only](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-07-policy-created-report-only.png)

---

## Step 8 - Identify Security Defaults blocking enforcement

When attempting to enable the Conditional Access policy, Microsoft Entra showed a warning that Security Defaults must be disabled before enabling a Conditional Access policy.

The policy could not be saved in **On** mode while Security Defaults were enabled.

![Security defaults error before enabling](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-08-security-defaults-error-before-enabling.png)

### Why this happened

Security Defaults provide basic tenant-wide identity protection.

Custom Conditional Access policies are a more controlled and flexible approach. In this lab tenant, Security Defaults had to be disabled before the custom Conditional Access policy could be enforced.

---

## Step 9 - Select reason for disabling Security Defaults

Security Defaults were disabled for this controlled lab scenario.

The selected reason was:

```text
My organization is planning to use Conditional Access
```

![Security defaults disable reason selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-09-security-defaults-disable-reason-selected.png)

---

## Step 10 - Confirm Security Defaults disabled

After saving the change, Security Defaults showed as:

```text
Disabled
```

This allowed the Conditional Access policy to be switched to enforcement mode.

![Security defaults disabled](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-10-security-defaults-disabled.png)

> Note: This was done only for the lab so that Conditional Access enforcement could be tested. In a real tenant, equivalent Conditional Access protections should be planned carefully before disabling Security Defaults.

---

## Step 11 - Enable the Conditional Access policy

The enforced Conditional Access policy was changed from:

```text
Report-only
```

to:

```text
On
```

The policy list confirmed the enforced policy state as:

```text
On
```

![Policy enabled On](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-11-policy-enabled-on.png)

---

## Step 12 - Test access from noncompliant BYOD device

The test user attempted to access Microsoft 365 / Teams from the noncompliant BYOD Windows device.

Test user:

```text
user03
```

Test device:

```text
WIN-BYOD-001
```

The sign-in was blocked with the message:

```text
Device must comply with your organization's compliance requirements
```

![User03 access blocked](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-12-user03-access-blocked.png)

### Expected result

This was the expected result.

Because the device was noncompliant, the device could not satisfy the grant control:

```text
Require device to be marked as compliant
```

---

## Step 13 - Review sign-in logs failure list

The Microsoft Entra sign-in logs were reviewed after the blocked access attempt.

The sign-in logs showed a failed sign-in for the BYOD test user.

The observed sign-in error code was:

```text
53000
```

![Sign-in logs enforced failure list](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-13-signin-logs-enforced-failure-list.png)

### What the sign-in log proves

The sign-in logs prove that the user was not simply blocked by the browser or by a local device issue.

The access decision was evaluated by Microsoft Entra Conditional Access.

---

## Step 14 - Validate Conditional Access policy details

The Conditional Access policy details confirmed the final enforced result.

Observed result:

```text
Policy: CA-WIN-Require-Compliant-Device-Enforced
Policy state: Enabled
Result: Failure
```

The policy matched the expected scope:

| Item | Result |
|---|---|
| User | Matched |
| Resource | Matched |
| Device platform | Windows10 matched |
| Grant controls | Not satisfied |
| Required control | Require compliant device |

![Sign-in log policy details failure](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-enforced-mode-test-14-signin-log-policy-details-failure.png)

---

## Validation summary

| Validation item | Expected result | Actual result |
|---|---|---|
| BYOD device visible in Intune | Yes | Passed |
| BYOD device noncompliant | Yes | Passed |
| Policy scoped to `GRP-BYOD-Users` | Yes | Passed |
| Target resource set to Office 365 | Yes | Passed |
| Device platform set to Windows | Yes | Passed |
| Grant control requires compliant device | Yes | Passed |
| Security Defaults issue identified | Yes | Passed |
| Security Defaults disabled for lab enforcement | Yes | Passed |
| Conditional Access policy enabled | Yes | Passed |
| Noncompliant BYOD access blocked | Yes | Passed |
| Sign-in logs captured failure | Yes | Passed |
| Conditional Access details showed grant control not satisfied | Yes | Passed |

---

## Final result

The lab was successful.

The enforced Conditional Access policy blocked the BYOD user from accessing Microsoft 365 because the Windows device was not compliant.

Final enforced result:

```text
Access blocked
```

Reason:

```text
Require compliant device = Not satisfied
```

This confirms that Microsoft Entra Conditional Access can enforce Intune compliance requirements and block access from noncompliant Windows devices.

---

## Key learning outcomes

- Report-only mode is useful for safe Conditional Access testing.
- Enforced mode actively allows or blocks access.
- Security Defaults must be disabled before custom Conditional Access policies can be enforced in this tenant.
- A managed device is not automatically trusted.
- A device must be compliant if the policy requires a compliant device.
- Microsoft Entra ID uses Intune compliance state as an access signal.
- Sign-in logs are the best place to validate Conditional Access decisions.
- The `Grant Controls` result shows whether the compliant-device requirement was satisfied.

---

## Troubleshooting notes

If the user is not blocked as expected:

1. Confirm the policy state is set to **On**.
2. Confirm the user is included in `GRP-BYOD-Users`.
3. Confirm the sign-in is targeting Office 365 / Microsoft 365 resources.
4. Confirm the device platform condition includes Windows.
5. Confirm the device is actually noncompliant in Intune.
6. Confirm the user is signing in from the expected device.
7. Check Microsoft Entra sign-in logs.
8. Open the Conditional Access policy details from the sign-in log.
9. Confirm the grant control shows `Require compliant device`.
10. Confirm the result shows `Failure` or `Not satisfied`.

If the policy cannot be enabled:

1. Check whether Security Defaults are enabled.
2. Review tenant-level Security Defaults settings.
3. Do not disable Security Defaults in production unless equivalent Conditional Access protections are planned.
4. Keep at least one emergency admin recovery path available.

---

## Cleanup notes

Because this was an enforced access test, the policy should not be left enabled unless continued blocking is intended.

Recommended cleanup after validation:

```text
Microsoft Entra admin center
-> Conditional Access
-> Policies
-> CA-WIN-Require-Compliant-Device-Enforced
-> Enable policy
-> Report-only or Off
-> Save
```

If this lab tenant will continue using Conditional Access, Security Defaults can remain disabled only if replacement Conditional Access protections are configured.

If Conditional Access testing is complete and no equivalent protections exist, consider re-enabling Security Defaults for basic tenant protection.

---

## Security and privacy notes

This lab is part of a public learning repository.

Before publishing screenshots, sanitize:

- Full user principal names.
- Tenant IDs.
- Device IDs.
- Object IDs.
- IP addresses.
- Top-right signed-in account details.
- Device serial numbers.
- Hardware identifiers.
- Any real personal or production data.

---

## Lab conclusion

This lab proves the enforced Conditional Access scenario for a noncompliant Windows BYOD device.

The user `user03` attempted to access Microsoft 365 from `WIN-BYOD-001`. The device was managed by Intune but marked noncompliant. The Conditional Access policy required a compliant device, so Microsoft Entra ID blocked the access attempt.

The final validation showed:

```text
Policy state: Enabled
Result: Failure
Grant Controls: Not satisfied
Require compliant device
```

This confirms that the Conditional Access policy worked correctly in enforced mode.

---

## Next lab

Recommended next lab:

```text
04-compliance-and-conditional-access/conditional-access-troubleshooting.md
```

This can document how to investigate blocked sign-ins, read Conditional Access policy details, and understand common error codes such as device compliance failures.
