# Windows Security Baseline

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Endpoint security |
| Policy name | WIN-Security-Baseline-Pilot |
| Policy type | Security Baseline for Windows 10 and later |
| Assignment group | GRP-Autopilot-Devices |
| Test device | WINAUTO452 |
| Initial result | Conflict and Error |
| Final result | Success |

---

## Lab Objective

Create a Windows Security Baseline profile in Intune, assign it to the pilot device group, investigate and remediate the resulting Firewall/Defender conflicts and a VBS error 65000, and confirm final Success status.

---

## Why This Lab Matters

A Windows Security Baseline is Microsoft's recommended group of security settings for Windows devices. Because it configures a broad range of areas — Firewall, Defender, Device Guard, Browser, LAPS, and more — it can conflict with dedicated endpoint security policies already in place.

This lab is valuable not just for showing policy creation, but for showing real Intune troubleshooting: identifying conflicts, understanding why they occur, and remediating them without breaking existing policies.

```text
Dedicated endpoint security policy = focused on one area (Firewall, Defender, BitLocker)
Security baseline = broad Microsoft-recommended package covering many areas at once
```

When both exist, settings configured in both will conflict. The resolution is to set the duplicate baseline settings to Not configured, leaving the dedicated policy as the owner.

---

## Prerequisites

- WINAUTO452 enrolled via Autopilot and member of GRP-Autopilot-Devices
- Existing Defender Antivirus, Firewall, BitLocker, and ASR policies already deployed to WINAUTO452

---

## Configuration Flow

```text
Create Windows Security Baseline profile
-> Review baseline sections
-> Assign to GRP-Autopilot-Devices
-> Sync WINAUTO452
-> Identify Firewall and Defender conflicts
-> Set overlapping settings to Not configured
-> Identify VBS Error 65000
-> Set Device Guard and VBS settings to Not configured
-> Sync again and confirm Success
```

---

## Steps Performed

### Step 1 — Created the baseline profile

Navigated to:

```text
Endpoint security -> Security baselines -> Security Baseline for Windows 10 and later -> Create policy
```

Named the profile `WIN-Security-Baseline-Pilot`. Reviewed the baseline sections — Administrative Templates, Auditing, Browser, Defender, Device Guard, Firewall, Local Security Authority, SmartScreen, Virtualization Based Technology, Windows Hello, LAPS, and others — before assigning.

![Baseline overview](../screenshots/sanitized/endpoint-security/windows-security-baseline-01-baseline-overview-sanitized.png)

![Create baseline profile](../screenshots/sanitized/endpoint-security/windows-security-baseline-02-create-profile-pane-sanitized.png)

![Baseline profile basics](../screenshots/sanitized/endpoint-security/windows-security-baseline-03-basics-sanitized.png)

![Baseline configuration settings](../screenshots/sanitized/endpoint-security/windows-security-baseline-04-configuration-settings-sanitized.png)

---

### Step 2 — Assigned to GRP-Autopilot-Devices

Assigned the profile to `GRP-Autopilot-Devices` and created it.

![Baseline assignment](../screenshots/sanitized/endpoint-security/windows-security-baseline-05-assignment-autopilot-devices-sanitized.png)

---

### Step 3 — Observed initial Pending state

After device sync, the device assignment status showed Pending, then progressed to Conflict and Error. This is expected during baseline processing when overlapping policies are present.

![Device status pending](../screenshots/sanitized/endpoint-security/windows-security-baseline-06-device-status-pending-sanitized.png)

---

### Step 4 — Identified and remediated Firewall and Defender conflicts

The per-setting policy report showed conflicts for the following settings, which were already configured by the dedicated Firewall and Defender Antivirus policies:

**Firewall conflicts:**
- Allow Local Ipsec Policy Merge
- Allow Local Policy Merge
- Disable Inbound Notifications
- Enable Log Dropped Packets
- Enable Log Success Connections
- Log Max File Size

**Defender conflicts:**
- Enable Network Protection
- Submit Samples Consent

All conflicting settings were changed to `Not configured` in the baseline, leaving the dedicated policies as the source of truth for these areas.

![Device status conflict](../screenshots/sanitized/endpoint-security/windows-security-baseline-10-device-status-conflict-sanitized.png)

![Policy settings conflict details](../screenshots/sanitized/endpoint-security/windows-security-baseline-11-policy-settings-conflict-details-sanitized.png)

![Baseline assignment edited](../screenshots/sanitized/endpoint-security/windows-security-baseline-12-assignment-edited-autopilot-devices-sanitized.png)

---

### Step 5 — Identified and remediated Device Guard and VBS error

After the conflict cleanup, one error remained:

```text
Enable Virtualization Based Security
Error code: 65000
```

This error is related to Device Guard and VBS settings that depend on hardware capabilities — specifically Secure Boot, TPM, virtualization support, and firmware configuration. The lab device could not satisfy these requirements.

The following settings were changed to `Not configured`:

- Configure System Guard Launch
- Credential Guard
- Enable Virtualization Based Security
- Machine Identity Isolation
- Require Platform Security Features
- Hypervisor Enforced Code Integrity

![Device status error](../screenshots/sanitized/endpoint-security/windows-security-baseline-07-device-status-error-sanitized.png)

![Policy setting error for VBS](../screenshots/sanitized/endpoint-security/windows-security-baseline-08-policy-setting-error-vbs-sanitized.png)

![VBS remediation set to Not configured](../screenshots/sanitized/endpoint-security/windows-security-baseline-09-remediation-vbs-not-configured-sanitized.png)

---

### Step 6 — Confirmed final Success status

After saving the updated baseline and syncing the device, the assignment report showed:

| Field | Result |
|---|---|
| Device | WINAUTO452 |
| Assignment status | Success |
| Succeeded | 1 |
| Error | 0 |
| Conflict | 0 |

![Final device status success](../screenshots/sanitized/endpoint-security/windows-security-baseline-13-device-status-success-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Windows Security Baseline profile created | Completed |
| Baseline assigned to GRP-Autopilot-Devices | Completed |
| Firewall and Defender conflicts identified | Completed |
| Overlapping settings set to Not configured | Completed |
| VBS Error 65000 identified | Completed |
| Device Guard and VBS settings set to Not configured | Completed |
| Final device status showed Success | Completed |

---

## Troubleshooting Notes

**Conflict after baseline assignment** — open the device from Device assignment status, filter by Conflict, and identify the setting names. Compare them against existing dedicated endpoint security policies. Set the duplicate baseline settings to `Not configured` so the dedicated policy remains the owner. Save the baseline, sync the device, and regenerate the report.

**Error 65000 for Enable Virtualization Based Security** — this error occurs when the device hardware cannot satisfy VBS and Device Guard requirements. Check Secure Boot, TPM, virtualization support, and firmware settings. If the lab device cannot meet these requirements, set the Device Guard and VBS-related baseline settings to `Not configured`. This does not remove the protection from devices that can support it — it simply stops enforcing it on devices that cannot.

**Pending after remediation** — pending is normal while Intune processes the updated baseline. Sync the device from Intune and from Windows Settings, restart the device if security settings changed, and wait before regenerating the report.

---

## Enterprise Reflection

Security baselines are a strong starting point for endpoint hardening, but they require careful pilot testing in environments with existing dedicated endpoint security policies. The key skill is not just deploying the baseline — it is knowing how to read conflict and error reports, trace them to specific settings, and decide which policy should own each area.

In production, set conflicting baseline settings to `Not configured` and let dedicated policies handle those areas. This keeps the baseline focused on the settings that dedicated policies do not cover, avoids redundant configuration, and prevents Intune from receiving conflicting signals for the same setting.

---

## Key Learning Outcomes

- How Security Baseline settings can conflict with dedicated Firewall, Defender, and ASR policies — and how to resolve those conflicts
- What Error 65000 means for Enable Virtualization Based Security and which settings to remediate
- Why setting conflicting baseline settings to Not configured is the correct resolution rather than removing the dedicated policy
- How to use per-setting policy status to isolate the exact setting causing a Conflict or Error
