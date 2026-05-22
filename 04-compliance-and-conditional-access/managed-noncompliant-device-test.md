# Managed Noncompliant Device Test

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Compliance and Conditional Access |
| Test device | WIN-BYOD-001 |
| Device ownership | Personal / BYOD |
| Test user | user03 |
| BYOD group | GRP-BYOD-Users |
| Temporary compliance policy | COMP-WIN-BYOD-Noncompliant-Test |
| Conditional Access policy | CA-WIN-Require-Compliant-Device-ReportOnly |
| Conditional Access mode | Report-only |
| Validation result | Report-only: Failure |

---

## Lab Objective

Intentionally mark a managed Windows BYOD device as noncompliant using a temporary compliance policy, then validate that the Conditional Access Report-only result shows Failure for the compliant-device grant control.

This proves the critical distinction: a device can be enrolled and managed by Intune but still fail Conditional Access if it is not compliant.

---

## Why This Lab Matters

Device management and device compliance are not the same thing:

```text
Managed by Intune = Yes
Compliant = No
```

Organizations typically require devices to be both managed and compliant before granting access to Microsoft 365. This lab validates that Microsoft Entra Conditional Access correctly uses Intune compliance state as an access signal — and that a managed-but-noncompliant device fails the check.

---

## Prerequisites

- WIN-BYOD-001 enrolled in Intune and initially compliant
- user03 licensed and member of GRP-BYOD-Users
- CA-WIN-Require-Compliant-Device-ReportOnly already created in Report-only mode
- Microsoft Entra sign-in logs accessible for validation

---

## Configuration Flow

```text
Confirm WIN-BYOD-001 starts compliant
-> Create temporary compliance policy with impossible minimum OS version
-> Assign policy to GRP-BYOD-Users
-> Confirm WIN-BYOD-001 becomes noncompliant
-> Update CA policy scope to include GRP-BYOD-Users
-> Sign in as user03 from BYOD device
-> Validate Report-only: Failure in sign-in logs
```

---

## Steps Performed

### Step 1 — Confirmed initial BYOD device state

Verified WIN-BYOD-001 was managed by Intune and showing Compliant before the temporary policy was applied.

![Initial BYOD device compliant](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-01-initial-byod-device-compliant.png)

---

### Step 2 — Created the temporary compliance policy

Navigated to:

```text
Devices -> Compliance -> Policies -> Create policy
```

Selected Windows 10 and later. Named the policy `COMP-WIN-BYOD-Noncompliant-Test`.

Configured the key setting:

| Setting | Value |
|---|---|
| Minimum OS version | 10.0.30000.0 |
| Action for noncompliance | Mark device noncompliant — Immediately |

The minimum OS version was set intentionally higher than the current Windows version on WIN-BYOD-001. This is a safe, reversible method — no security controls are weakened, the device simply cannot satisfy an impossible version requirement.

![Create Windows compliance policy](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-02-create-windows-compliance-policy.png)

![Policy basics](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-03-policy-basics-name-description.png)

![Minimum OS version setting](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-04-minimum-os-version-noncompliant-setting.png)

![Noncompliance action immediate](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-05-actions-for-noncompliance-immediate.png)

---

### Step 3 — Assigned and created the policy

Assigned the policy to `GRP-BYOD-Users` and created it.

![Assignment to BYOD users group](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-06-assignment-byod-users-group.png)

![Review and create policy summary](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-07-review-create-policy-summary.png)

---

### Step 4 — Confirmed WIN-BYOD-001 became noncompliant

After policy evaluation and device check-in, WIN-BYOD-001 showed as Noncompliant in both the compliance policy device status and the Windows devices list.

![Policy device status noncompliant](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-08-policy-device-status-noncompliant.png)

![Windows device list BYOD noncompliant](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-09-windows-device-list-byod-noncompliant.png)

---

### Step 5 — Updated Conditional Access scope

Updated `CA-WIN-Require-Compliant-Device-ReportOnly` to include `GRP-BYOD-Users` alongside the existing `GRP-Pilot-Users`. Policy remained in Report-only mode.

![CA policy includes BYOD users](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-10-conditional-access-policy-includes-byod-users.png)

---

### Step 6 — Validated Report-only failure in sign-in logs

user03 signed in from WIN-BYOD-001. In Microsoft Entra sign-in logs, the Report-only tab showed:

| Item | Result |
|---|---|
| Policy | CA-WIN-Require-Compliant-Device-ReportOnly |
| Result | Report-only: Failure |
| Grant control | RequireCompliantDevice — Not satisfied |

![Report-only failure](../screenshots/sanitized/compliance-and-conditional-access/managed-noncompliant-device-test-11-report-only-failure-require-compliant-device.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| WIN-BYOD-001 confirmed compliant at start | Completed |
| Temporary compliance policy created | Completed |
| Minimum OS version set above device version | Completed |
| Policy assigned to GRP-BYOD-Users | Completed |
| WIN-BYOD-001 marked Noncompliant | Completed |
| CA policy updated to include GRP-BYOD-Users | Completed |
| Sign-in log captured Report-only: Failure | Completed |
| Grant control showed RequireCompliantDevice not satisfied | Completed |

---

## Troubleshooting Notes

**Device not becoming noncompliant** — confirm the policy is assigned to `GRP-BYOD-Users` and user03 is a member. Sync the device from Intune and from Windows Settings, then wait for compliance evaluation to refresh. Check the compliance policy device status view directly.

**Sign-in logs not showing Report-only failure** — confirm the CA policy includes `GRP-BYOD-Users` and is still in Report-only mode. Check the Report-only tab in sign-in log details specifically — the result does not appear on the main Conditional Access tab, which only shows enforced policy results.

---

## Cleanup Notes

The temporary compliance policy `COMP-WIN-BYOD-Noncompliant-Test` should be removed or disabled after testing to return WIN-BYOD-001 to a normal compliance state. The CA policy can remain in Report-only mode — do not switch it to On unless intentionally running an enforcement test with admin lockout protection in place.

---

## Key Learning Outcomes

- A device can be managed by Intune and still be noncompliant — management and compliance are separate states
- A temporary high minimum OS version is a safe, reversible way to force a device into noncompliance for testing
- Conditional Access Report-only mode shows Failure when a grant control is not satisfied, without blocking the user
- The Report-only tab in sign-in logs is separate from the main Conditional Access tab and must be checked specifically
- This lab is the prerequisite validation step before the enforced mode test
