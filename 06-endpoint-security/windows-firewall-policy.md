# Windows Firewall Policy

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Endpoint security |
| Policy name | WIN-Autopilot-Windows-Firewall-Policy |
| Policy type | Firewall — Windows Firewall |
| Assignment group | GRP-Autopilot-Devices |
| Validation device | WINAUTO452 |
| Final policy status | Success |

---

## Lab Objective

Create a Windows Firewall endpoint security policy in Intune, enable firewall protection for Domain, Private, and Public network profiles, assign the policy to the Autopilot device group, and validate successful deployment on WINAUTO452.

---

## Why This Lab Matters

Windows Firewall reduces the attack surface of a corporate device by blocking unsolicited inbound connections. Managed via Intune, firewall settings can be enforced consistently across all corporate devices without relying on local configuration.

---

## Prerequisites

- WINAUTO452 enrolled via Autopilot and member of GRP-Autopilot-Devices
- Endpoint security policy permissions available in Intune

---

## Firewall Settings Configured

| Setting | Value |
|---|---|
| Enable Domain Network Firewall | True |
| Enable Private Network Firewall | True |
| Enable Public Network Firewall | True |
| Default inbound action — Domain | Block |
| Default inbound action — Private | Block |
| Default inbound action — Public | Block |
| Default outbound action | Allow |
| Shielded mode | False |
| Log file path | `%systemroot%\system32\LogFiles\Firewall\pfirewall.log` |
| Log max file size | 1024 |

> [!NOTE]
> This lab configured the firewall baseline profile only. Custom inbound/outbound firewall rules were not created. Shielded mode was left disabled — enabling it without testing can disrupt remote management and network connectivity.

---

## Configuration Flow

```text
Create Windows Firewall policy in Endpoint security
-> Enable Firewall for Domain, Private, and Public profiles
-> Assign to GRP-Autopilot-Devices
-> Sync WINAUTO452
-> Verify device status in Intune
```

---

## Steps Performed

### Step 1 — Created and configured the Firewall policy

Navigated to:

```text
Endpoint security -> Firewall -> Create Policy
```

Selected Windows platform and Windows Firewall profile (not Windows Firewall Rules or Hyper-V Firewall Rules — those are for specific rule and Hyper-V scenarios). Named the policy `WIN-Autopilot-Windows-Firewall-Policy` and configured the settings in the table above.

![Create Windows Firewall profile](../screenshots/sanitized/endpoint-security/firewall-profile-create-sanitized.png)

![Firewall policy basics](../screenshots/sanitized/endpoint-security/firewall-policy-basics-sanitized.png)

![Firewall policy settings](../screenshots/sanitized/endpoint-security/firewall-policy-settings-sanitized.png)

---

### Step 2 — Assigned to GRP-Autopilot-Devices and created

Assigned to `GRP-Autopilot-Devices` and created the policy.

![Firewall policy assignment](../screenshots/sanitized/endpoint-security/firewall-policy-assignment-autopilot-devices-sanitized.png)

---

### Step 3 — Verified policy list and device status

After creation, the policy appeared in the Firewall policies list. The device status report confirmed:

| Field | Result |
|---|---|
| Device | WINAUTO452 |
| Assignment status | Success |
| Succeeded | 1 |
| Error | 0 |
| Conflict | 0 |

![Firewall policy list](../screenshots/sanitized/endpoint-security/firewall-policy-list-sanitized.png)

![Firewall device status success](../screenshots/sanitized/endpoint-security/firewall-device-status-winauto452-succeeded-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Windows Firewall policy created | Completed |
| Domain, Private, and Public firewall profiles enabled | Completed |
| Default inbound Block configured | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| WINAUTO452 device status showed Success | Completed |

---

## Troubleshooting Notes

**Policy stays Pending** — sync the device from both Windows Settings (`Settings -> Accounts -> Access work or school -> Info -> Sync`) and from Intune remote actions, then wait for reporting to refresh.

**Policy not applying** — confirm the device is enrolled, is in `GRP-Autopilot-Devices`, has internet connectivity, and has checked in recently. Check for conflicts with other firewall policies or Security Baseline settings that configure the same profiles.

**Policy shows Conflict** — check whether a Security Baseline or another Intune policy configures overlapping Windows Firewall settings. Remove the duplicate configuration from one policy, sync the device, and refresh the report.

---

## Enterprise Reflection

Key considerations before broad firewall policy rollout:

- Test with a pilot device group first and validate that normal connectivity and remote management still work
- Do not block outbound traffic unless there is a specific tested requirement — unexpected outbound blocks can disrupt business applications
- Do not enable shielded mode without validating remote access paths
- Create custom firewall rules only after identifying and testing the required ports, protocols, and network profiles

---

## Related Labs

| Lab | Relationship |
|---|---|
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Provides the Autopilot-enrolled corporate device WINAUTO452 |

---

## Key Learning Outcomes

- How to create a Windows Firewall policy using Intune Endpoint security
- The difference between Windows Firewall profile settings and Windows Firewall Rules
- Why default inbound Block with outbound Allow is the safe baseline starting point
- Why Shielded mode should be validated carefully before enabling in production
