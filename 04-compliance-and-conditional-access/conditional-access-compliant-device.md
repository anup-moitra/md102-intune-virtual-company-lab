# Conditional Access Compliant Device

## Lab status

| Item | Status |
|---|---|
| Lab | Conditional Access Compliant Device |
| Section | 04 - Compliance and Conditional Access |
| Platform | Microsoft Entra ID / Microsoft Intune |
| Policy type | Conditional Access policy |
| Policy name | `CA-WIN-Require-Compliant-Device-ReportOnly` |
| Policy state | Report-only |
| Target group | `GRP-Pilot-Users` |
| Test user | `User 01` |
| Target resource | Office 365 |
| Device platform | Windows |
| Grant control | Require device to be marked as compliant |
| Final result | Completed successfully |
| Validation result | Report-only: Success |

---

## Lab objective

The objective of this lab was to create a Microsoft Entra Conditional Access policy that evaluates whether a user is accessing Microsoft 365 from a compliant Windows device.

The policy was configured in **Report-only** mode so that it could safely evaluate the access decision without blocking the user.

This lab builds directly on the previous compliance lab, where the Windows device `WINAUTO452` was successfully marked compliant in Microsoft Intune.

The Conditional Access policy validates this flow:

```text
User signs in to Microsoft 365
        ↓
Microsoft Entra ID checks Conditional Access policy scope
        ↓
Policy checks user, target resource, and device platform
        ↓
Policy checks whether the device is compliant
        ↓
Report-only result is recorded in sign-in logs
```

---

## Why this lab matters

Conditional Access is one of the most important security controls in Microsoft Entra ID.

In a traditional environment, access was often controlled mainly by username, password, network location, or VPN access. In a modern cloud-managed environment, access decisions can also include device health, compliance state, user risk, sign-in risk, location, client app, and authentication strength.

For this lab, the main signal was:

```text
Device compliance
```

This means Microsoft Entra ID can use the compliance result reported by Microsoft Intune when deciding whether access should be allowed.

This is important in real environments because a user might know the correct password, but the organization may still want to block or restrict access if the device is not healthy, not encrypted, not protected by Defender, or not managed correctly.

---

## Lab environment

| Component | Value |
|---|---|
| Microsoft Entra tenant | HomeLAB |
| Intune tenant | Home lab Intune environment |
| Conditional Access policy | `CA-WIN-Require-Compliant-Device-ReportOnly` |
| Policy mode | Report-only |
| Target user group | `GRP-Pilot-Users` |
| Test user | `User 01` |
| Test device | `WINAUTO452` |
| Device compliance state | Compliant |
| Target resource | Office 365 |
| Device platform condition | Windows |
| Browser/app tested | Microsoft 365 web apps |

---

## Prerequisites

Before starting this lab, the following items were already completed:

- `WINAUTO452` was enrolled into Microsoft Intune.
- `WINAUTO452` was marked compliant by the Windows compliance policy.
- `User 01` was available as the test user.
- `User 01` was included in the pilot user group.
- `GRP-Pilot-Users` was available for policy targeting.
- Office 365 / Microsoft 365 web access was available for testing.
- Microsoft Entra sign-in logs were available for validation.

---

## Configuration summary

The Conditional Access policy was configured with the following settings:

| Area | Configuration |
|---|---|
| Policy name | `CA-WIN-Require-Compliant-Device-ReportOnly` |
| Users | Specific users included |
| Included group | `GRP-Pilot-Users` |
| Target resources | Office 365 |
| Network | Not configured |
| Conditions | Device platform |
| Device platform | Windows |
| Grant control | Require device to be marked as compliant |
| Session control | Not configured |
| Policy state | Report-only |

---

## Step 1 - Open Conditional Access

The lab started from the Microsoft Entra admin center.

The Conditional Access area was opened from:

```text
Microsoft Entra admin center
-> Conditional Access
```

The Conditional Access overview page was used as the starting point for creating the new policy.

![Conditional Access overview](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-01-conditional-access-overview-sanitized.png)

---

## Step 2 - Configure users

The policy was configured to apply only to a pilot user group.

The selected group was:

```text
GRP-Pilot-Users
```

This controlled the scope of the policy and avoided applying the policy to all users.

![Conditional Access users group selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-02-users-group-selected-sanitized.png)

### Why a pilot group was used

A pilot group is safer than applying a policy broadly.

In a real enterprise, Conditional Access policies should be tested with a small group first. This helps avoid accidental user lockouts and gives administrators a chance to review the impact before enforcement.

For this lab, the pilot user group allowed the policy to evaluate only the intended test user.

---

## Step 3 - Configure target resource

The target resource was configured as:

```text
Office 365
```

This means the policy evaluates sign-ins to Microsoft 365 services such as Office web apps and related Microsoft 365 cloud resources.

![Office 365 target resource selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-03-target-resource-office365-sanitized.png)

### Why Office 365 was selected

Office 365 was selected because it represents a realistic enterprise resource.

In a production environment, organizations often protect Microsoft 365 apps with Conditional Access policies because they contain business email, files, Teams collaboration, SharePoint content, and other sensitive cloud data.

---

## Step 4 - Configure device platform condition

The policy condition was configured for Windows devices.

The selected device platform was:

```text
Windows
```

![Windows device platform selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-04-device-platform-windows-sanitized.png)

### Why the platform was limited to Windows

This lab focused only on a Windows device compliance scenario.

The test device was:

```text
WINAUTO452
```

Because the compliance policy from the previous lab was created for Windows, the Conditional Access policy was also scoped to Windows. This keeps the lab clean and avoids unexpected results from Android, iOS, macOS, or Linux sign-ins.

---

## Step 5 - Configure grant control

The access control was configured under **Grant**.

The selected grant requirement was:

```text
Require device to be marked as compliant
```

This means the policy checks whether the device is reported as compliant by Microsoft Intune.

The session control was not configured for this lab.

| Access control | Configuration |
|---|---|
| Grant | Require device to be marked as compliant |
| Session | Not configured |

---

## Step 6 - Set policy to Report-only

The policy was intentionally created in:

```text
Report-only
```

Report-only mode allows the policy to evaluate sign-ins and show what the result would have been, without enforcing access control.

![Policy summary with Report-only selected](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-05-policy-summary-report-only-sanitized.png)

### Why Report-only mode was used

Report-only mode is a safe rollout method for Conditional Access.

It allows administrators to answer these questions before enforcement:

- Did the correct users match the policy?
- Did the correct cloud app or resource match the policy?
- Did the device platform condition match correctly?
- Did the compliant-device grant control succeed?
- Would the user have been allowed or blocked if the policy was enabled?

This is important because Conditional Access controls sign-in. A mistake in policy scope can block users from Microsoft 365 or even admin portals.

---

## Step 7 - Confirm policy creation

After creation, the policy appeared in the Conditional Access policy list.

The policy state was:

```text
Report-only
```

![Conditional Access policy created in Report-only mode](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-06-policy-created-report-only-sanitized.png)

---

## Step 8 - Test Microsoft 365 access

The test user accessed Microsoft 365 successfully from the Windows device.

The test confirmed that the user could open Microsoft 365 apps while the Conditional Access policy was evaluating in Report-only mode.

![Microsoft 365 app access success](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-07-microsoft365-app-access-success-sanitized.png)

### Expected behavior

Because the policy was in Report-only mode, it did not block access.

The expected behavior was:

```text
User 01 signs in
        ↓
Microsoft 365 access succeeds
        ↓
Conditional Access evaluation is recorded in sign-in logs
```

---

## Step 9 - Validate Report-only result in sign-in logs

The Microsoft Entra sign-in logs were used to validate the Conditional Access result.

The Report-only tab showed the policy result:

```text
Report-only: Success
```

The grant control shown was:

```text
Require compliant device
```

![Report-only Conditional Access success](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-08-report-only-success-sanitized.png)

This confirmed that the Conditional Access policy evaluated successfully.

---

## Step 10 - Validate policy details

The policy details view confirmed that the policy matched the expected sign-in conditions.

| Item | Result |
|---|---|
| Policy | `CA-WIN-Require-Compliant-Device-ReportOnly` |
| Policy state | Report-only |
| Result | Report-only: Success |
| User | Matched |
| Resource | Matched |
| Device platform | Windows10 matched |
| Grant controls | Satisfied |
| Session controls | Not configured |

![Conditional Access policy details success](../screenshots/sanitized/compliance-and-conditional-access/conditional-access-compliant-device-09-policy-details-report-only-success-sanitized.png)

---

## Validation

The validation confirmed that the policy worked as expected.

| Validation item | Result |
|---|---|
| Policy created successfully | Passed |
| Policy state set to Report-only | Passed |
| Pilot user group selected | Passed |
| Office 365 selected as target resource | Passed |
| Windows selected as device platform | Passed |
| Compliant device grant control configured | Passed |
| Microsoft 365 access succeeded | Passed |
| Sign-in logs captured policy evaluation | Passed |
| Report-only result showed Success | Passed |
| Grant controls showed Satisfied | Passed |

---

## Final test result

Final result:

```text
Conditional Access policy evaluated successfully in Report-only mode.
```

The policy result showed:

```text
Report-only: Success
```

The grant control showed:

```text
Require compliant device = Satisfied
```

This confirms that the compliant Windows device met the Conditional Access requirement.

---

## Troubleshooting notes

During testing, the normal **Conditional Access** tab showed Security Defaults, while the Conditional Access policy created in this lab appeared under the **Report-only** tab.

This is expected because the policy was not enabled in enforcement mode. Report-only policies are reviewed from the Report-only view in sign-in log details.

The tenant also displayed a warning that Security Defaults must be disabled before enabling a Conditional Access policy. Since this lab used Report-only mode, enforcement was not enabled in this lab.

The enforced Conditional Access behavior will be tested later in a separate lab.

---

## Enterprise reflection

This lab demonstrates a safe and realistic enterprise approach to Conditional Access deployment.

In production environments, administrators should avoid immediately enabling broad Conditional Access policies without testing. A poorly scoped Conditional Access policy can block users from Microsoft 365 apps or even prevent administrators from accessing management portals.

Using Report-only mode first allows administrators to validate the policy impact before enforcement. This is especially important when combining Conditional Access with Intune device compliance, because the policy depends on accurate device state reporting.

This lab also shows the relationship between Microsoft Intune and Microsoft Entra ID:

```text
Intune reports device compliance
        ↓
Microsoft Entra ID uses compliance as an access signal
        ↓
Conditional Access evaluates whether access should be allowed
```

This is a core concept in modern identity and endpoint security.

---

## Key learning outcomes

- Created a Microsoft Entra Conditional Access policy.
- Scoped the policy to a pilot user group.
- Targeted Office 365 as the protected cloud resource.
- Configured Windows as the device platform condition.
- Required the device to be marked as compliant.
- Used Report-only mode to validate policy behavior safely.
- Tested Microsoft 365 access as the pilot user.
- Reviewed Microsoft Entra sign-in logs.
- Confirmed the Conditional Access policy result as Report-only: Success.
- Confirmed the compliant-device grant control was satisfied.
- Understood how Intune compliance integrates with Microsoft Entra Conditional Access.

---

## Lab conclusion

This lab was completed successfully.

The Conditional Access policy `CA-WIN-Require-Compliant-Device-ReportOnly` was created in Microsoft Entra ID and configured to require a compliant Windows device for Office 365 access.

The policy was scoped to the pilot user group `GRP-Pilot-Users` and configured in Report-only mode. Microsoft Entra sign-in logs confirmed that the policy matched the test sign-in, the Windows device platform condition matched, and the compliant-device grant control was satisfied.

The final result was:

```text
Report-only: Success
```

This confirms that Conditional Access successfully evaluated the compliant-device requirement without enforcing or blocking access.

---

## Next lab

Recommended next lab:

```text
04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md
```

The next lab should test real enforcement behavior after safely validating the policy in Report-only mode.
