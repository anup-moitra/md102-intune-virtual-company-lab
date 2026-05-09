# Windows Basic Compliance Policy

This file documents a basic Windows compliance policy created in Microsoft Intune.

## Objective

Create and test a Windows compliance policy that checks basic security health settings on a managed Windows device.

## Lab Context

Compliance policies check whether a device meets security requirements.

Conditional Access can later use the compliance result to allow or block access to Microsoft 365 resources.

Simple flow:

```text
Compliance policy = checks the device
Conditional Access = uses the compliance result
```

## Policy Details

| Setting | Value |
|---|---|
| Policy name | Windows 11 Basic Compliance |
| Platform | Windows 10 and later |
| Assignment | All devices |
| Test device | WIN-CORP-001 |
| Compliance result | Compliant |

## Security Requirements Checked

The policy checks basic Windows security requirements such as:

- Firewall
- Antivirus
- Antispyware
- Microsoft Defender Antimalware
- Real-time protection

## Prerequisites

Before creating this policy, the following tasks were completed:

- Microsoft Intune tenant verified
- Microsoft Entra ID users created
- Intune license assigned to user01
- WIN-CORP-001 enrolled into Intune

## Steps Performed

1. Opened Microsoft Intune admin center.
2. Navigated to Devices > Compliance.
3. Created a Windows compliance policy.
4. Configured basic security requirements.
5. Assigned the policy.
6. Synced WIN-CORP-001.
7. Reviewed compliance status.
8. Confirmed WIN-CORP-001 reported compliant.

## Test Result

| Test Item | Result |
|---|---|
| Compliance policy created | Successful |
| Policy assigned | Successful |
| WIN-CORP-001 evaluated | Successful |
| WIN-CORP-001 reported compliant | Successful |
| Final result | Successful |

## What This Proves

This lab proves that Microsoft Intune can evaluate a managed Windows device against compliance rules.

```text
WIN-CORP-001 enrolls into Intune
→ Compliance policy evaluates device health
→ Device meets configured requirements
→ Device reports Compliant
```

## Screenshots

Suggested folder:

```text
screenshots/sanitized/compliance/
```

Suggested screenshots:

```text
windows-basic-compliance-policy-settings-sanitized.jpg
win-corp-001-compliance-status-sanitized.jpg
windows-compliance-device-status-sanitized.jpg
```

## Troubleshooting Notes

If a device does not become compliant:

1. Confirm the device is enrolled in Intune.
2. Confirm the policy assignment is correct.
3. Sync the device manually.
4. Confirm Defender and firewall are enabled.
5. Review per-setting compliance details.
6. Wait for device check-in.

## Current Lab Status

Completed:

- Windows compliance policy created
- WIN-CORP-001 evaluated
- WIN-CORP-001 reported compliant
- Conditional Access requiring compliant device completed later
- Basic Windows configuration profile completed later

Pending:

- Add screenshots as available
- Test managed but noncompliant corporate device later

## Next Step

Continue with Autopilot validation, Microsoft 365 Apps verification, BYOD enrollment, or additional endpoint security labs.
