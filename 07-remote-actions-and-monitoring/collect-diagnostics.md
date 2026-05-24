# Collect Diagnostics Remote Action

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Remote actions and monitoring |
| Remote action | Collect diagnostics |
| Test device | WINAUTO452 |
| Device ownership | Corporate |
| Result | Action completed successfully |

---

## Lab Objective

Trigger the Collect diagnostics remote action on WINAUTO452 from the Intune admin center, verify the action completes from the device-level action status tab, and review tenant diagnostics settings.

---

## Why This Lab Matters

When users report device issues, Intune administrators can remotely collect diagnostic data without needing physical access to the endpoint. This is especially useful for distributed or remote devices where hands-on investigation is not practical.

---

## Prerequisites

- WINAUTO452 enrolled in Intune with internet connectivity
- Admin account has permission to run the Collect diagnostics remote action
- Tenant device diagnostics settings enabled

---

## Remote Action Reference

| Action | Purpose | Risk |
|---|---|---|
| Collect diagnostics | Collects troubleshooting logs from the managed device | Non-destructive — but diagnostic packages can contain sensitive device and user-identifiable data |

> [!NOTE]
> Collect diagnostics does not affect the device state, installed apps, or user data. The ZIP package produced by the action should be treated as sensitive operational data and must not be uploaded to public repositories.

---

## Steps Performed

### Step 1 — Opened WINAUTO452 in Intune

Navigated to:

```text
Devices -> Windows -> Windows devices -> WINAUTO452
```

Confirmed device state (Compliant, Corporate, managed by Intune) and verified the Collect diagnostics action was available in the top action bar.

![Device overview](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-01-device-overview.png)

---

### Step 2 — Triggered and confirmed the action

Selected Collect diagnostics from the action bar. The confirmation prompt explained that Intune would collect diagnostic data from the device and referenced the monitoring location at `Monitor -> Device diagnostics`. Confirmed by selecting Collect data.

![Collect diagnostics action selected](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-02-collect-diagnostics-action-selected.png)

![Confirm collect diagnostics](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-03-confirm-collect-diagnostics.png)

---

### Step 3 — Verified action completion

Checked the device-level action status tab:

```text
WINAUTO452 -> Device action status
```

The action showed:

| Action | Status |
|---|---|
| Collect diagnostics | Complete |

![Device action status complete](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-04-device-action-status-complete.png)

> [!NOTE]
> Microsoft documentation references a separate `Monitor -> Device diagnostics` report for checking collection status. In this lab tenant, that report was not visible under Devices > Monitor. The device-level Device action status tab showing Complete was used as the validation evidence instead, which clearly confirms the action processed successfully.

---

### Step 4 — Reviewed tenant diagnostics settings

Navigated to:

```text
Tenant administration -> Device diagnostics
```

Confirmed the following were enabled:

- Device diagnostics for corporate-managed Windows devices
- Automatic diagnostic capture during Windows Autopilot failures
- Diagnostic data for devices managed by Intune app protection policy

![Device diagnostics settings enabled](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-05-device-diagnostics-settings-enabled.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| WINAUTO452 opened in Intune | Completed |
| Collect diagnostics action triggered | Completed |
| Action confirmed via Collect data prompt | Completed |
| Device action status showed Complete | Completed |
| Tenant diagnostics settings reviewed and confirmed enabled | Completed |
| Diagnostic ZIP excluded from GitHub | Completed |

---

## Troubleshooting Notes

**Collect diagnostics not visible** — confirm the device is enrolled and corporate-owned, the admin role has permission to run remote actions, and check whether the action is in the overflow menu rather than the main action bar.

**Action stays Pending** — confirm the device is powered on with internet access and can communicate with Intune. Sync the device and wait for reporting to update. Restart the device if the action does not complete after an extended period.

**Action fails** — check whether the device was online during the request window, confirm tenant diagnostics settings are enabled under `Tenant administration -> Device diagnostics`, and verify required Intune network endpoints are not blocked by firewall rules.

---

## Enterprise Reflection

Collect diagnostics is a non-disruptive first-response tool for remote troubleshooting. In production, it is most useful when a device is failing policy deployment, showing compliance errors, or experiencing enrollment issues that cannot be reproduced in the admin portal alone. The diagnostic package contains event logs, registry exports, and system information — treat it as sensitive data with the same care as any support ticket attachment.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `07-remote-actions-and-monitoring/device-sync-remote-actions.md` | Sync action — used before collecting diagnostics to ensure latest policy state |
| `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Reviews tenant-level monitoring reports alongside device-level action status |
| `08-troubleshooting/remote-actions-diagnostics-troubleshooting.md` | Case study using this lab as a reference scenario |

---

## Key Learning Outcomes

- How to trigger and confirm the Collect diagnostics remote action in Intune
- Why the device-level Device action status tab is a reliable validation point when tenant-level diagnostic reports are not visible
- Why diagnostic ZIP packages must not be uploaded to public repositories
- When Collect diagnostics is the appropriate first-response tool for remote device troubleshooting
