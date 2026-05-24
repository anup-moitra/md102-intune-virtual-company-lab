# Configuration Policy Conflict Troubleshooting

## Case Study Status

| Field | Value |
|---|---|
| Status | Completed |
| Source lab | `06-endpoint-security/windows-security-baseline.md` |
| Policy | WIN-Security-Baseline-Pilot |
| Device | WINAUTO452 |
| Issues found | Firewall/Defender conflicts, VBS Error 65000 |
| Final result | Success |

Screenshots reused from `screenshots/sanitized/endpoint-security/`.

---

## Issue Summary

During the Windows Security Baseline lab, the assigned baseline initially cycled through Pending → Conflict → Error before reaching Success after remediation.

Two distinct issues required investigation:

1. **Firewall and Defender policy conflicts** — settings already managed by dedicated endpoint security policies
2. **Device Guard / VBS Error 65000** — settings requiring hardware capabilities the lab device could not satisfy

---

## Why This Matters

When multiple policy types target the same device simultaneously — a Firewall policy, a Defender Antivirus policy, an ASR policy, and a Security Baseline — any setting configured differently by two policies will produce a conflict. A successful Intune administrator must know how to identify the conflicting setting and decide which policy should own it.

---

## Issue 1 — Firewall and Defender Conflicts

**Conflicting settings identified:**

Firewall-related:
- Allow Local Ipsec Policy Merge
- Allow Local Policy Merge
- Disable Inbound Notifications
- Enable Log Dropped Packets
- Enable Log Success Connections
- Log Max File Size

Defender-related:
- Enable Network Protection
- Submit Samples Consent

These settings were already configured by the dedicated Windows Firewall and Defender Antivirus policies assigned to the same device.

**Resolution:** All conflicting settings were changed to `Not configured` in the baseline, leaving the dedicated policies as the source of truth for those areas.

![Device status conflict](../screenshots/sanitized/endpoint-security/windows-security-baseline-10-device-status-conflict-sanitized.png)

![Policy settings conflict details](../screenshots/sanitized/endpoint-security/windows-security-baseline-11-policy-settings-conflict-details-sanitized.png)

---

## Issue 2 — Device Guard and VBS Error 65000

**Error identified:**

```text
Enable Virtualization Based Security
Error code: 65000
```

This error indicates the device cannot satisfy the VBS and Device Guard requirements. These settings depend on hardware capabilities — specifically Secure Boot, TPM, virtualization support, and firmware configuration. The lab device could not meet these requirements.

**Resolution:** The following settings were changed to `Not configured` in the baseline:

- Configure System Guard Launch
- Credential Guard
- Enable Virtualization Based Security
- Machine Identity Isolation
- Require Platform Security Features
- Hypervisor Enforced Code Integrity

After saving and syncing the device, the assignment report showed Success.

![Device status pending](../screenshots/sanitized/endpoint-security/windows-security-baseline-06-device-status-pending-sanitized.png)

![Device status error](../screenshots/sanitized/endpoint-security/windows-security-baseline-07-device-status-error-sanitized.png)

![Policy setting error for VBS](../screenshots/sanitized/endpoint-security/windows-security-baseline-08-policy-setting-error-vbs-sanitized.png)

![VBS remediation set to Not configured](../screenshots/sanitized/endpoint-security/windows-security-baseline-09-remediation-vbs-not-configured-sanitized.png)

![Final device status success](../screenshots/sanitized/endpoint-security/windows-security-baseline-13-device-status-success-sanitized.png)

---

## Troubleshooting Method

```text
Open baseline profile
-> Review Device assignment status
-> Open affected device
-> Filter policy settings by Conflict or Error
-> Identify setting names
-> Compare with other policies assigned to the same device
-> Change duplicate or unsupported settings to Not configured
-> Save policy and sync device
-> Regenerate report and confirm Success
```

---

## Key Learning

Security baselines are broad policy packages that frequently overlap with dedicated endpoint security policies. The correct approach is not to remove the dedicated policies — it is to identify the overlap and set the duplicate baseline settings to `Not configured`, keeping the dedicated policy as the owner of that setting.

For Device Guard and VBS errors: setting these to `Not configured` does not remove protection from capable devices. It only stops enforcing the setting on devices that cannot satisfy the requirement.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `06-endpoint-security/windows-security-baseline.md` | Source lab where this issue occurred |
| `06-endpoint-security/windows-firewall-policy.md` | Dedicated Firewall policy that conflicted with baseline |
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Dedicated Defender policy that conflicted with baseline |
| `08-troubleshooting/troubleshooting-summary.md` | Summary of all troubleshooting case studies |
