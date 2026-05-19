# Attack Surface Reduction Policy

This file documents the Microsoft Intune Attack Surface Reduction Rules policy configured for the MD-102 Intune virtual company lab.

---

## Objective

Create and validate an Attack Surface Reduction policy in Microsoft Intune using **Audit** mode for a pilot Windows device.

This lab validates that:

- Attack Surface Reduction Rules can be configured from the Intune admin center.
- ASR rules can be assigned to a pilot device group.
- The policy can deploy successfully to a managed Windows device.
- ASR rule configuration can be verified locally on the endpoint using PowerShell.
- Audit mode can be used first to evaluate rule impact before moving to enforcement.

---

## Why This Lab Matters

Attack Surface Reduction Rules help reduce common malware and attacker behaviors on Windows endpoints.

Instead of immediately blocking activity, this lab uses **Audit** mode first. Audit mode is useful in real environments because it lets administrators evaluate possible impact before changing rules to Block or Warn mode.

Simple deployment flow:

```text
Create ASR policy in Intune
-> Configure selected ASR rules in Audit mode
-> Assign policy to pilot device group
-> Device receives policy
-> Verify policy status in Intune
-> Validate ASR rule configuration locally with PowerShell
```

This is a safer real-world approach because endpoint security policies should usually be piloted before broad enforcement.

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Policy area | Endpoint security |
| Policy type | Attack surface reduction |
| Platform | Windows |
| Profile | Attack Surface Reduction Rules |
| Policy name | ASR-WIN-Audit-Mode-Pilot |
| Policy mode | Audit |
| Assignment group | GRP-Autopilot-Devices |
| Test device | WINAUTO452 |
| Device platform | Windows |
| Validation method | Intune device status and PowerShell |
| Current status | Completed |

---

## Prerequisites

Before starting this lab, the following should be completed:

- Microsoft Intune tenant available.
- Windows test device enrolled in Intune.
- Test device assigned to the pilot device group.
- Microsoft Defender Antivirus available on the Windows device.
- Endpoint security policy permissions available in Intune.
- Screenshots captured and sanitized before upload.

---

## Important Notes

This lab uses **Audit** mode only.

Audit mode was selected to safely validate policy deployment without immediately blocking user or system activity.

Future enforcement can be tested later by changing selected rules from:

```text
Audit
```

to:

```text
Block
```

or:

```text
Warn
```

Only after reviewing audit results and business impact.

---

## Policy Configuration Summary

| Setting | Value |
|---|---|
| Policy name | ASR-WIN-Audit-Mode-Pilot |
| Platform | Windows |
| Profile | Attack Surface Reduction Rules |
| Assignment | GRP-Autopilot-Devices |
| Deployment mode | Audit |
| Device status | Success |
| Endpoint validation | Completed |

---

## ASR Rules Configured

The following ASR rules were configured in **Audit** mode:

| ASR Rule | Mode |
|---|---|
| Block Office applications from creating executable content | Audit |
| Block credential stealing from the Windows local security authority subsystem | Audit |
| Block JavaScript or VBScript from launching downloaded executable content | Audit |
| Block executable content from email client and webmail | Audit |
| Block abuse of exploited vulnerable signed drivers | Audit |
| Use advanced protection against ransomware | Audit |
| Block all Office applications from creating child processes | Audit |

---

## Steps Performed

### Step 1: Opened Attack Surface Reduction Policy Area

Opened the Intune admin center and navigated to:

```text
Endpoint security
-> Attack surface reduction
-> Create Policy
```

Selected:

```text
Platform: Windows
Profile: Attack Surface Reduction Rules
```

---

### Step 2: Configured Policy Basics

Configured the policy basics:

```text
Name: ASR-WIN-Audit-Mode-Pilot
Description: Audit mode Attack Surface Reduction policy for pilot Windows devices. This policy is used to validate ASR rule deployment before enforcement.
```

---

### Step 3: Configured ASR Rules in Audit Mode

Configured selected Attack Surface Reduction Rules using **Audit** mode.

Audit mode was selected to observe how the rules would behave before enforcing them in block mode.

---

### Step 4: Assigned the Policy

Assigned the policy to the pilot device group:

```text
GRP-Autopilot-Devices
```

The group was used to target a limited test device scope before expanding policy deployment.

---

### Step 5: Reviewed and Created the Policy

Reviewed the policy configuration and confirmed:

- Policy name
- Description
- ASR rule settings
- Assignment group
- Audit mode configuration

The policy was then created.

---

### Step 6: Verified Policy Deployment Status

After policy deployment, the Intune report showed the target device with assignment status:

```text
Success
```

The test device shown in the policy status report was:

```text
WINAUTO452
```

This confirmed that the ASR policy reached the target device successfully.

---

### Step 7: Validated ASR Rules on the Endpoint

On the Windows endpoint, PowerShell was opened as administrator.

The following command was used to verify ASR rule configuration locally:

```powershell
Get-MpPreference | Select-Object AttackSurfaceReductionRules_Ids, AttackSurfaceReductionRules_Actions
```

The output showed ASR rule IDs and corresponding rule actions, confirming that ASR rule settings were present on the endpoint.

---

## Expected Result

After completing this lab:

- The ASR policy should exist in Intune.
- The selected ASR rules should be configured in Audit mode.
- The policy should be assigned to the pilot device group.
- The target Windows device should report policy success.
- PowerShell should show ASR rule IDs and action values on the endpoint.
- The policy should be ready for later monitoring and possible enforcement testing.

---

## Test Result

| Test Item | Result |
|---|---|
| ASR policy created | Completed |
| Policy basics configured | Completed |
| ASR rules configured in Audit mode | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| Review and create completed | Completed |
| Device status checked in Intune | Completed |
| Device assignment status showed Success | Completed |
| Endpoint PowerShell validation completed | Completed |
| Final lab result | Completed |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/endpoint-security/
```

### ASR policy profile creation

![ASR policy profile creation](../screenshots/sanitized/endpoint-security/asr-policy-01-create-profile-sanitized.png)

### ASR policy basics

![ASR policy basics](../screenshots/sanitized/endpoint-security/asr-policy-02-basics-sanitized.png)

### ASR rules configured in Audit mode

![ASR rules configured in Audit mode](../screenshots/sanitized/endpoint-security/asr-policy-03-rules-audit-mode-sanitized.png)

### ASR policy assignment

![ASR policy assignment](../screenshots/sanitized/endpoint-security/asr-policy-04-assignment-sanitized.png)

### ASR policy review and create

![ASR policy review and create](../screenshots/sanitized/endpoint-security/asr-policy-05-review-create-sanitized.png)

### ASR policy device status success

![ASR policy device status success](../screenshots/sanitized/endpoint-security/asr-policy-06-device-status-success-sanitized.png)

### ASR endpoint PowerShell validation

![ASR endpoint PowerShell validation](../screenshots/sanitized/endpoint-security/asr-policy-07-endpoint-validation-sanitized.png)

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, device IDs, object IDs, serial numbers, and top-right signed-in account details were hidden.

---

## Screenshot Files

```text
asr-policy-01-create-profile-sanitized.png
asr-policy-02-basics-sanitized.png
asr-policy-03-rules-audit-mode-sanitized.png
asr-policy-04-assignment-sanitized.png
asr-policy-05-review-create-sanitized.png
asr-policy-06-device-status-success-sanitized.png
asr-policy-07-endpoint-validation-sanitized.png
```

---

## Troubleshooting Notes

If the ASR policy does not apply:

1. Confirm the target device is enrolled in Intune.
2. Confirm the device is a member of the assigned group.
3. Confirm Microsoft Defender Antivirus is the active antivirus provider.
4. Sync the device from Intune or from the Windows device.
5. Wait for policy check-in and refresh the device status report.
6. Check for policy conflicts with other ASR policies or security baselines.

If PowerShell does not show ASR rule IDs:

1. Confirm the policy status shows success in Intune.
2. Run PowerShell as administrator.
3. Re-run the validation command after syncing the device.
4. Restart the device if policy status is delayed.
5. Check whether another policy is overriding or conflicting with the ASR settings.

If the policy shows conflict:

1. Review other Endpoint security ASR policies.
2. Review Security Baseline settings.
3. Check whether the same ASR rule is configured differently in another policy.
4. Keep pilot ASR testing scoped to one group where possible.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Full real email addresses
- Real tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Passwords
- MFA QR codes
- BitLocker recovery keys
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Device IDs
- Object IDs
- Serial numbers
- Any sensitive endpoint identifiers

---

## Current Status

| Task | Status |
|---|---|
| attack-surface-reduction-policy.md created | Completed |
| ASR policy created in Intune | Completed |
| ASR rules configured in Audit mode | Completed |
| Policy assigned to pilot device group | Completed |
| Device status verified | Completed |
| Endpoint PowerShell validation completed | Completed |
| Screenshots added | Completed |

---

## Next Step

Continue to the next endpoint security lab:

```text
06-endpoint-security/windows-security-baseline.md
```

This next lab will document Windows Security Baseline configuration and compare baseline security settings with individual endpoint security policies.
