# Device Monitoring and Reports

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Remote actions and monitoring |
| Primary test device | WINAUTO452 |
| Lab type | Read-only monitoring review |

---

## Lab Objective

Review the key Intune monitoring and reporting views — device inventory, compliance state, remote action history, and configuration policy assignment status — to validate the operational state of managed Windows devices.

---

## Why This Lab Matters

Creating policies is only half of the Intune administrator job. The other half is confirming that policies reached devices and that devices remain healthy. This lab covers the monitoring views an administrator would use during daily operations and troubleshooting.

---

## Prerequisites

- WINAUTO452 enrolled in Intune with at least one policy assigned
- At least one remote action previously performed
- Admin account has permission to view devices and reports

---

## Reports and Views Reviewed

| View / Report | Purpose |
|---|---|
| Devices overview | High-level platform and health dashboard |
| Windows devices list | Device inventory with compliance, ownership, last check-in |
| Device overview | Device-specific compliance, ownership, management details |
| Device action status | Device-level remote action history |
| Devices → Monitor | Central list of operational monitoring reports |
| Device Actions report | Tenant-level remote action history |
| Noncompliant devices report | Identifies devices failing compliance |
| Configuration policy status | Assignment result for a specific policy |

---

## Steps Performed

### Step 1 — Reviewed Devices overview

Navigated to `Devices -> Overview`. Reviewed the high-level dashboard showing platform counts, noncompliant device tiles, configuration policy failure summaries, and entry points to detailed reports.

![Devices overview](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-01-devices-overview.png)

---

### Step 2 — Reviewed Windows devices list

Navigated to `Devices -> Windows -> Windows devices` and located WINAUTO452. Confirmed it showed as Intune-managed, corporate-owned, and compliant, with last check-in visible.

![Windows devices list](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-02-windows-devices-list.png)

---

### Step 3 — Reviewed device overview and action status

Opened the WINAUTO452 device record. The device overview confirmed Compliant status, Corporate ownership, Intune management, and visible last check-in. The Device action status tab showed previous completed actions:

| Action | Status |
|---|---|
| Collect diagnostics | Complete |
| Restart | Complete |

![Device overview](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-03-device-overview.png)

![Device action status](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-04-device-action-status.png)

---

### Step 4 — Reviewed Devices Monitor report list

Navigated to `Devices -> Monitor`. The page listed available operational reports including Device actions, Noncompliant devices, Configuration policy assignment failures, Device encryption status, and Enrollment failures.

![Devices Monitor report list](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-05-devices-monitor-report-list.png)

---

### Step 5 — Reviewed Device Actions report

Navigated to `Devices -> Monitor -> Device actions`. The report showed tenant-level remote action history with columns for device name, action, status, initiated by, and date/time.

Actions visible from previous lab activity included Restart, Retire, Wipe, and Delete.

> [!NOTE]
> Historical Wipe, Delete, and Retire entries were visible from previous lab activity. This monitoring lab did not execute any of those actions.

![Device Actions report](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-06-device-actions-report.png)

---

### Step 6 — Reviewed Noncompliant devices report

Navigated to `Devices -> Monitor -> Noncompliant devices`. The report identified a Windows BYOD test device as Not compliant, showing device name, primary UPN, compliance status, platform, OS version, ownership, last check-in, and management authority.

![Noncompliant devices report](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-07-noncompliant-devices-report.png)

---

### Step 7 — Reviewed configuration policy assignment status

Navigated to `Devices -> Configuration -> WIN-Autopilot-Defender-Antivirus-Policy -> Device assignment status`.

| Status | Count |
|---|---|
| Success | 1 |
| Error | 0 |
| Conflict | 0 |
| Pending | 0 |

WINAUTO452 reported Success for the selected policy.

![Configuration policy status](../screenshots/sanitized/remote-actions-and-monitoring/device-monitoring-08-configuration-policy-status.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Devices overview reviewed | Completed |
| Windows devices list reviewed | Completed |
| WINAUTO452 located and confirmed Compliant | Completed |
| Device action status reviewed | Completed |
| Devices Monitor report list reviewed | Completed |
| Device Actions report reviewed | Completed |
| Noncompliant devices report reviewed | Completed |
| Configuration policy assignment status reviewed | Completed |

---

## Reporting Delay Notes

Intune reporting is not always real-time. Report data depends on device check-in timing, policy refresh cycles, device connectivity, and service-side report generation. Some reports include a notice that data may be delayed.

When troubleshooting, always cross-reference:
- Device last check-in time
- Report generation time
- Device action status
- Policy assignment status

Refreshing or regenerating a report manually (`Generate again` where available) and syncing the device will surface the most current data.

---

## Troubleshooting Notes

**Device not appearing in the Windows devices list** — confirm the device is enrolled, the correct platform filter is selected, and the device hasn't been retired or deleted. Search by device name if the list is large.

**Report data looks outdated** — click Refresh or Generate again where available, sync the device from Intune or Windows Settings, and wait for reporting to update.

**Policy shows Error or Conflict** — open the policy, review per-device assignment status and per-setting status where available. Compare against other policies that may configure the same setting. Check the error code for specifics.

**Device shows Noncompliant** — open the device record, review which compliance setting failed, confirm the device has checked in recently, sync it, and check whether Conditional Access is blocking access as a result.

---

## Enterprise Reflection

Monitoring is as important as policy deployment in production Intune environments. The views covered in this lab are the ones helpdesk and endpoint administrators use most during daily operations: the device list for inventory checks, the device overview for per-device health, action status for remote action audit, the noncompliant devices report for compliance-driven access control, and policy assignment status for deployment verification.

---

## Key Learning Outcomes

- How to use the Windows devices list, device overview, and Device action status tab for device-level monitoring
- How to access and interpret the Device Actions, Noncompliant devices, and configuration policy assignment reports
- Why Intune reporting can be delayed and how to get current data
- How monitoring complements policy deployment as part of the full Intune administration workflow
