# Windows Basic Compliance Policy

## Lab status

| Item | Status |
|---|---|
| Lab | Windows Basic Compliance Policy |
| Section | 04 - Compliance and Conditional Access |
| Platform | Windows 10 and later |
| Policy type | Windows 10/11 compliance policy |
| Policy name | `COMP-WIN-Basic-Security-Compliance` |
| Target group | `GRP-Autopilot-Devices` |
| Target device | `WINAUTO452` |
| Final result | Completed successfully |
| Compliance result | `WINAUTO452` reported as Compliant |

---

## Lab objective

The objective of this lab was to create a basic Windows compliance policy in Microsoft Intune and validate that an Autopilot-managed Windows device meets core security requirements.

The compliance policy was configured to check important Windows security controls such as BitLocker, Secure Boot, Code Integrity, Firewall, TPM, Antivirus, Antispyware, Microsoft Defender Antimalware, and Real-time protection.

The target device for this lab was:

```text
WINAUTO452
```

The policy was assigned to the device group:

```text
GRP-Autopilot-Devices
```

---

## Why this lab matters

Compliance policies are an important part of modern endpoint management.

In a traditional environment, administrators often checked device health manually or relied on domain-based tools and Group Policy. In a modern Microsoft Intune environment, compliance policies allow administrators to define the security requirements a device must meet before it is considered trusted.

This becomes especially important when combined with Conditional Access.

A typical enterprise flow looks like this:

```text
User signs in
        ↓
Microsoft Entra ID checks identity
        ↓
Intune reports device compliance
        ↓
Conditional Access evaluates compliance state
        ↓
Access is allowed or blocked
```

This lab proves that a managed Windows device can be evaluated by Intune and marked compliant only when required security settings are healthy.

---

## Lab environment

| Component | Value |
|---|---|
| Tenant | Home lab Microsoft Intune tenant |
| Device name | `WINAUTO452` |
| Device platform | Windows |
| Ownership | Corporate |
| Management authority | Microsoft Intune |
| Enrollment type | Windows Autopilot / Microsoft Entra joined |
| Target group | `GRP-Autopilot-Devices` |
| Compliance policy | `COMP-WIN-Basic-Security-Compliance` |

---

## Prerequisites

Before starting this lab, the following items were already completed:

- Windows device was enrolled into Intune.
- Device was available in the Intune admin center.
- Device was a member of `GRP-Autopilot-Devices`.
- BitLocker policy had already been deployed.
- Microsoft Defender Antivirus policy had already been deployed.
- Windows Firewall policy had already been deployed.
- Administrator access was available on the Windows device.
- BIOS/UEFI access was available for Secure Boot troubleshooting.

---

## Configuration flow

The lab followed this flow:

```text
Create Windows compliance policy
        ↓
Configure required security settings
        ↓
Assign policy to GRP-Autopilot-Devices
        ↓
Sync WINAUTO452
        ↓
Review compliance result
        ↓
Troubleshoot Secure Boot noncompliance
        ↓
Enable Secure Boot in BIOS
        ↓
Sync device again
        ↓
Confirm final compliant status
```

---

## Step 1 - Create the compliance policy

In the Microsoft Intune admin center, the compliance policy was created from:

```text
Devices
-> Compliance
-> Policies
-> Create policy
```

The selected platform and profile type were:

| Setting | Value |
|---|---|
| Platform | Windows 10 and later |
| Profile type | Windows 10/11 compliance policy |

![Create Windows compliance policy](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-01-create-policy-sanitized.png)

---

## Step 2 - Configure policy basics

The following name and description were used:

| Field | Value |
|---|---|
| Name | `COMP-WIN-Basic-Security-Compliance` |
| Description | Basic Windows compliance policy for MD-102 lab. Validates BitLocker, Secure Boot, Defender, Firewall, TPM, and device health on Autopilot-managed Windows devices. |

![Compliance policy basics](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-02-basics-sanitized.png)

---

## Step 3 - Configure compliance settings

The compliance policy was configured with a basic security baseline suitable for an Intune-managed Windows corporate device.

### Device Health settings

| Setting | Configuration |
|---|---|
| BitLocker | Require |
| Secure Boot | Require |
| Code integrity | Require |

### System Security settings

| Setting | Configuration |
|---|---|
| Firewall | Require |
| Trusted Platform Module (TPM) | Require |
| Antivirus | Require |
| Antispyware | Require |
| Microsoft Defender Antimalware | Require |
| Real-time protection | Require |

### Settings intentionally left not configured

The following settings were intentionally left as `Not configured` for this first compliance lab:

| Setting area | Reason |
|---|---|
| Minimum / maximum OS version | Avoided because incorrect build values can make a healthy device noncompliant |
| Password requirements | Not required for this first device-health compliance test |
| Microsoft Defender for Endpoint risk score | Defender for Endpoint integration was not part of this lab |
| Microsoft Defender Antimalware minimum version | Avoided to prevent version-specific reporting issues |
| Security intelligence up-to-date | Avoided for the first pass lab because definition update reporting can be delayed |

![Compliance policy settings](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-03-compliance-settings-sanitized.png)

---

## Step 4 - Configure actions for noncompliance

The default noncompliance action was kept.

| Action | Schedule |
|---|---|
| Mark device noncompliant | Immediately |

No email notification action was added in this lab.

![Actions for noncompliance](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-04-actions-for-noncompliance-sanitized.png)

---

## Step 5 - Assign the compliance policy

The policy was assigned to the pilot Autopilot device group.

| Assignment type | Group |
|---|---|
| Included group | `GRP-Autopilot-Devices` |

The policy was not assigned to all users or all devices. This keeps the rollout controlled and safer for lab testing.

![Compliance policy assignment](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-05-assignment-sanitized.png)

---

## Step 6 - Review and create

The final review page confirmed the policy name, platform, compliance settings, noncompliance action, and assignment group.

![Review and create compliance policy](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-06-review-create-sanitized.png)

---

## Initial validation result

After the policy was created and assigned, the device initially reported as not compliant.

The per-setting compliance report showed that most settings were compliant, but Secure Boot was failing.

| Setting | Result |
|---|---|
| Anti-Spyware | Compliant |
| Real-time protection | Compliant |
| Antivirus | Compliant |
| Microsoft Defender Antimalware | Compliant |
| Secure Boot | Noncompliant |
| Code Integrity | Compliant |
| BitLocker | Compliant |
| Firewall | Compliant |
| Trusted Platform Module (TPM) | Compliant |

![Secure Boot noncompliant per-setting status](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-07-per-setting-secure-boot-noncompliant-sanitized.png)

---

## Troubleshooting performed

The Secure Boot failure was checked locally on `WINAUTO452` using PowerShell.

The following command was used:

```powershell
Confirm-SecureBootUEFI
hostname
```

The initial result showed:

```text
Confirm-SecureBootUEFI = False
hostname = WINAUTO452
```

This confirmed that Secure Boot was disabled locally on the device.

![Secure Boot false in PowerShell](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-08-secure-boot-false-powershell-sanitized.png)

---

## Remediation performed

Secure Boot was enabled from the Lenovo laptop BIOS/UEFI settings.

After the BIOS change, the device was restarted and the same PowerShell command was run again:

```powershell
Confirm-SecureBootUEFI
hostname
```

The updated result showed:

```text
Confirm-SecureBootUEFI = True
hostname = WINAUTO452
```

This confirmed that Secure Boot was successfully enabled.

![Secure Boot true in PowerShell](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-09-secure-boot-true-powershell-sanitized.png)

---

## Final validation

After Secure Boot was enabled, the device was synced with Intune again.

The compliance policy report then showed:

| Metric | Result |
|---|---|
| Compliant | 1 |
| Noncompliant | 0 |
| Others | 0 |
| Total | 1 |

The target device `WINAUTO452` reported as compliant for the policy `COMP-WIN-Basic-Security-Compliance`.

![Final compliant status](../screenshots/sanitized/compliance-and-conditional-access/windows-basic-compliance-policy-10-device-status-compliant-sanitized.png)

---

## Final test result

| Test | Result |
|---|---|
| Policy created successfully | Passed |
| Policy assigned to `GRP-Autopilot-Devices` | Passed |
| Device received compliance policy | Passed |
| Device initially detected Secure Boot issue | Passed |
| Secure Boot issue identified from per-setting status | Passed |
| Secure Boot remediated in BIOS/UEFI | Passed |
| Device synced after remediation | Passed |
| `WINAUTO452` became compliant | Passed |

Final result:

```text
WINAUTO452 = Compliant
```

---

## Troubleshooting summary

The most important troubleshooting result in this lab was the Secure Boot failure.

Intune correctly detected that Secure Boot was not enabled. The local PowerShell validation confirmed the same result. After enabling Secure Boot in BIOS/UEFI, the local device check returned `True`, and Intune later reported the device as compliant.

This showed that compliance policies are not only configuration checks. They can also reveal real device firmware and security posture issues.

---

## Enterprise reflection

In a real enterprise environment, this type of compliance policy would help administrators identify devices that do not meet the minimum security standard.

For example, if a device has Secure Boot disabled, BitLocker disabled, Defender disabled, or Firewall disabled, the device can be marked noncompliant. Conditional Access can then use this compliance signal to block or limit access to corporate resources.

This lab also showed why pilot testing is important. If this policy had been assigned broadly without testing, many devices with Secure Boot disabled could suddenly become noncompliant. A controlled pilot group gives administrators time to troubleshoot and fix issues before enforcing access controls.

---

## Key learning outcomes

- Created a Windows 10/11 compliance policy in Microsoft Intune.
- Configured core Windows security checks for compliance.
- Assigned the compliance policy to a pilot Autopilot device group.
- Validated per-setting compliance status.
- Identified Secure Boot as the failed compliance setting.
- Confirmed Secure Boot status locally using PowerShell.
- Enabled Secure Boot in BIOS/UEFI.
- Synced the device with Intune after remediation.
- Confirmed final compliant status in the Intune admin center.
- Learned how device compliance prepares the environment for Conditional Access.

---

## Lab conclusion

This lab was completed successfully.

The Windows compliance policy `COMP-WIN-Basic-Security-Compliance` was created and assigned to `GRP-Autopilot-Devices`. The target device `WINAUTO452` initially failed compliance because Secure Boot was disabled. After enabling Secure Boot in the Lenovo BIOS/UEFI settings and syncing the device again, Intune reported the device as compliant.

This lab establishes the foundation for the next Conditional Access lab, where access to cloud apps can be controlled based on whether the device is marked compliant.

---

## Next lab

Recommended next lab:

```text
04-compliance-and-conditional-access/conditional-access-compliant-device.md
```

The next lab should create a Conditional Access policy in report-only mode that requires a compliant device.
