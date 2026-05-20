# Configuration Policy Conflict Troubleshooting

This troubleshooting case study documents the real policy conflict and error remediation performed during the Windows Security Baseline lab.

---

## Case Study Status

| Item | Status |
|---|---|
| Troubleshooting scenario documented | Completed |
| Source lab completed | Completed |
| Screenshots reused from existing repo evidence | Completed |
| New screenshots created for this file | No |

---

## Related Source Lab

```text
06-endpoint-security/windows-security-baseline.md
```

Screenshots are reused from the existing endpoint security evidence folder:

```text
screenshots/sanitized/endpoint-security/
```

---

## Issue Summary

During the Windows Security Baseline lab, the assigned baseline initially showed policy reporting states such as:

```text
Pending
Conflict
Error
Success
```

The important troubleshooting findings were:

```text
Firewall and Defender related policy conflicts
Device Guard / Virtualization Based Security error
Error code: 65000
```

After remediation, the final device assignment status showed:

```text
Success
```

---

## Why This Matters

In Microsoft Intune, it is common for multiple policy types to target the same device.

Example:

```text
Windows Firewall policy
Defender Antivirus policy
Attack Surface Reduction policy
Windows Security Baseline
```

If two policies manage the same setting differently, Intune can report a conflict. A successful Intune administrator must know how to identify the conflicting setting and decide which policy should manage it.

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Policy area | Endpoint security |
| Source lab | Windows Security Baseline |
| Policy name | WIN-Security-Baseline-Pilot |
| Assignment group | GRP-Autopilot-Devices |
| Test device | WINAUTO452 |
| Initial result | Conflict and Error |
| Final result | Success |

---

## Issue 1: Firewall and Defender Policy Conflicts

The baseline reported conflicts for settings such as:

```text
Allow Local Ipsec Policy Merge
Allow Local Policy Merge
Disable Inbound Notifications
Enable Log Dropped Packets
Enable Log Success Connections
Enable Network Protection
Log Max File Size
Submit Samples Consent
```

These settings overlapped with existing dedicated endpoint security policies.

Main conflict areas:

- Windows Firewall
- Microsoft Defender Antivirus
- Defender or network protection related settings

---

## Resolution for Policy Conflicts

The overlapping baseline settings were changed to:

```text
Not configured
```

This allowed dedicated endpoint security policies to remain the source of truth for those settings.

Firewall related settings remediated:

```text
Allow Local Ipsec Policy Merge
Allow Local Policy Merge
Disable Inbound Notifications
Enable Log Dropped Packets
Enable Log Success Connections
Log Max File Size
```

Defender related settings remediated:

```text
Enable Network Protection
Submit Samples Consent
```

---

## Issue 2: Device Guard and VBS Error

The baseline also showed an error for:

```text
Enable Virtualization Based Security
Error code: 65000
```

This type of issue can depend on device capability, firmware settings, virtualization support, Secure Boot, TPM, and Windows security configuration.

---

## Resolution for VBS Error

The following Device Guard and virtualization-based security settings were changed to:

```text
Not configured
```

Settings remediated:

```text
Configure System Guard Launch
Credential Guard
Enable Virtualization Based Security
Machine Identity Isolation
Require Platform Security Features
Hypervisor Enforced Code Integrity
```

After saving the policy and syncing the device, the device assignment report moved to success.

---

## Troubleshooting Method Used

The troubleshooting approach was:

```text
Open baseline profile
-> Review Device assignment status
-> Open affected device
-> Filter policy settings by Conflict or Error
-> Identify setting names
-> Compare overlapping policies
-> Change duplicate or unsupported baseline settings to Not configured
-> Save policy
-> Sync device
-> Regenerate/review report
-> Confirm Success
```

---

## Evidence Screenshots

### Device status pending

![Device status pending](../screenshots/sanitized/endpoint-security/windows-security-baseline-06-device-status-pending-sanitized.png)

### Device status error

![Device status error](../screenshots/sanitized/endpoint-security/windows-security-baseline-07-device-status-error-sanitized.png)

### Policy setting error for VBS

![Policy setting error for VBS](../screenshots/sanitized/endpoint-security/windows-security-baseline-08-policy-setting-error-vbs-sanitized.png)

### VBS remediation set to Not configured

![VBS remediation set to Not configured](../screenshots/sanitized/endpoint-security/windows-security-baseline-09-remediation-vbs-not-configured-sanitized.png)

### Device status conflict

![Device status conflict](../screenshots/sanitized/endpoint-security/windows-security-baseline-10-device-status-conflict-sanitized.png)

### Policy settings conflict details

![Policy settings conflict details](../screenshots/sanitized/endpoint-security/windows-security-baseline-11-policy-settings-conflict-details-sanitized.png)

### Final device status success

![Final device status success](../screenshots/sanitized/endpoint-security/windows-security-baseline-13-device-status-success-sanitized.png)

---

## Key Learning

The main lesson from this case study is:

```text
Security baselines are broad policy packages and can overlap with dedicated endpoint security policies.
```

Best practice:

```text
Use security baselines as a starting point.
Use dedicated endpoint security policies when you need more focused control.
Avoid configuring the same setting differently in multiple policies.
Pilot first before broad deployment.
```

---

## Admin Checklist for Similar Issues

If Intune reports Error or Conflict:

1. Open the affected policy.
2. Review device assignment status.
3. Review per-setting status.
4. Filter by Error or Conflict.
5. Identify the exact setting name.
6. Compare with other policies assigned to the same device.
7. Decide which policy should own the setting.
8. Set duplicate settings to Not configured where appropriate.
9. Sync the device.
10. Wait for reporting to update.
11. Confirm final Success status.

---

## Related Files

```text
06-endpoint-security/windows-security-baseline.md
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/windows-defender-antivirus-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
08-troubleshooting/troubleshooting-summary.md
```

---

## Final Status

| Task | Status |
|---|---|
| Conflict identified | Completed |
| Error 65000 identified | Completed |
| Overlapping settings reviewed | Completed |
| Duplicate/unsupported settings remediated | Completed |
| Final status verified as Success | Completed |
| Troubleshooting case documented | Completed |
