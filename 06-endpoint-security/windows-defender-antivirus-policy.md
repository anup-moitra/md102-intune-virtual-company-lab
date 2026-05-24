# Microsoft Defender Antivirus Policy

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Endpoint security |
| Policy name | WIN-Autopilot-Defender-Antivirus-Policy |
| Policy type | Antivirus — Microsoft Defender Antivirus |
| Assignment group | GRP-Autopilot-Devices |
| Validation device | WINAUTO452 |
| Final policy status | Success |

---

## Lab Objective

Create a Microsoft Defender Antivirus endpoint security policy in Intune, assign it to the Autopilot device group, and validate successful deployment on WINAUTO452.

---

## Why This Lab Matters

Defender Antivirus is built into Windows and can be centrally managed through Intune Endpoint security policies. This lab proves that an Autopilot-enrolled corporate device can receive and apply antivirus settings after enrollment and report success back to Intune.

---

## Prerequisites

- WINAUTO452 enrolled via Autopilot and member of GRP-Autopilot-Devices
- Endpoint security policy permissions available in Intune

---

## Defender Antivirus Settings Configured

| Setting | Value |
|---|---|
| Allow Archive Scanning | Allowed |
| Allow Behavior Monitoring | Allowed |
| Allow Cloud Protection | Allowed |
| Allow Email Scanning | Allowed |
| Allow Full Scan on Removable Drive Scanning | Allowed |
| Allow Realtime Monitoring | Allowed |
| Allow Scanning Network Files | Allowed |
| Allow Script Scanning | Allowed |
| Allow On Access Protection | Allowed |
| Check for Signatures Before Running Scan | Enabled |
| Cloud Block Level | High |
| Cloud Extended Timeout | 50 |
| Days to Retain Cleaned Malware | 30 |
| Enable Network Protection | Enabled (Audit mode) |
| PUA Protection | Enabled |
| Real Time Scan Direction | Monitor all files |
| Submit Samples Consent | Send safe samples automatically |

**Threat remediation actions:**

| Severity | Action |
|---|---|
| Severe | Quarantine |
| High | Quarantine |
| Moderate | Quarantine |
| Low | Quarantine |

**Exclusions:** Intentionally left blank — no excluded extensions, paths, or processes.

---

## Configuration Flow

```text
Create Microsoft Defender Antivirus policy
-> Configure Defender settings
-> Assign to GRP-Autopilot-Devices
-> Sync WINAUTO452
-> Verify device status in Intune
```

---

## Steps Performed

### Step 1 — Created and configured the Defender Antivirus policy

Navigated to:

```text
Endpoint security -> Antivirus -> Create Policy
```

Selected Windows platform and Microsoft Defender Antivirus profile. Named the policy `WIN-Autopilot-Defender-Antivirus-Policy` and configured the settings in the tables above.

![Autopilot device group member](../screenshots/sanitized/endpoint-security/defender-autopilot-device-group-member-sanitized.png)

![Defender Antivirus profile creation](../screenshots/sanitized/endpoint-security/defender-antivirus-profile-create-sanitized.png)

![Defender Antivirus policy basics](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-basics-sanitized.png)

![Defender Antivirus policy settings](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-settings-sanitized.png)

---

### Step 2 — Assigned to GRP-Autopilot-Devices and created

Assigned to `GRP-Autopilot-Devices` and created the policy.

![Defender Antivirus policy assignment](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-assignment-autopilot-devices-sanitized.png)

![Defender Antivirus policy list](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-list-sanitized.png)

---

### Step 3 — Verified policy deployment status

After device sync, the Intune policy status report showed:

| Field | Result |
|---|---|
| Device | WINAUTO452 |
| Assignment status | Success |
| Succeeded | 1 |
| Error | 0 |
| Conflict | 0 |

![Defender Antivirus device status success](../screenshots/sanitized/endpoint-security/defender-antivirus-device-status-winauto452-succeeded-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Defender Antivirus policy created | Completed |
| Core settings configured including PUA and cloud protection | Completed |
| Threat remediation set to Quarantine for all severities | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| WINAUTO452 device status showed Success | Completed |

---

## Troubleshooting Notes

**Policy stays Pending** — confirm the device is in `GRP-Autopilot-Devices`, sync from both Windows Settings and Intune, and wait for reporting to refresh. Check for conflicts with other antivirus or endpoint security policies.

**Policy shows Conflict** — check whether another antivirus policy or a Security Baseline configures overlapping Defender settings. Remove duplicate settings from one policy, sync the device, and refresh the report.

**Device not appearing in the status report** — confirm the device is enrolled in Intune, is a member of `GRP-Autopilot-Devices`, and has checked in recently. Trigger a manual sync and wait for reporting to update.

---

## Enterprise Reflection

Defender Antivirus policies should be assigned to device groups representing corporate-managed devices, not user groups. Key production considerations: avoid unnecessary exclusions (they reduce protection), use Cloud Block Level High with a reasonable timeout, and validate with Intune reporting before expanding beyond the pilot group. If Microsoft Defender for Endpoint is licensed, integrate it for stronger threat visibility and response capabilities.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Provides the Autopilot-enrolled corporate device WINAUTO452 |

---

## Key Learning Outcomes

- How to create a Microsoft Defender Antivirus policy using Intune Endpoint security
- Which core Defender settings to enable for a baseline antivirus policy
- Why exclusions should be left blank unless there is a specific justified reason
- How to validate Defender Antivirus policy deployment using Intune device status reporting
