# Remote Actions Diagnostics Troubleshooting

This troubleshooting case study documents the real portal navigation and validation issue observed during the Collect Diagnostics remote action lab.

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
07-remote-actions-and-monitoring/collect-diagnostics.md
```

Screenshots are reused from the existing remote actions evidence folder:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

---

## Issue Summary

During the Collect Diagnostics lab, Microsoft documentation referenced a diagnostics monitoring location, but the expected separate **Device diagnostics** report was not clearly visible under the Devices Monitor area in the lab tenant.

Expected documentation-style path:

```text
Monitor
-> Device diagnostics
```

Observed working validation path:

```text
Device page
-> Device action status
-> Collect diagnostics
-> Complete
```

Tenant diagnostics settings were also reviewed from:

```text
Tenant administration
-> Device diagnostics
```

---

## Why This Matters

Cloud admin portals change over time. Intune administrators should understand the intended workflow, but also know how to validate results using other available portal views.

In this case, the goal was not only to click **Collect diagnostics**. The goal was to prove that the action completed successfully and to handle diagnostic data safely.

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Remote action | Collect diagnostics |
| Test device | WINAUTO452 |
| Device ownership | Corporate |
| Device state | Compliant |
| Managed by | Intune |
| Final action status | Complete |
| Diagnostic ZIP uploaded to GitHub | No |

---

## Troubleshooting Timeline

### Step 1: Collect diagnostics action started

The managed Windows device was opened from Intune:

```text
Devices
-> Windows
-> Windows devices
-> WINAUTO452
```

The remote action selected was:

```text
Collect diagnostics
```

### Step 2: Confirmation prompt accepted

The confirmation prompt was reviewed and the action was submitted.

### Step 3: Expected monitoring location was checked

The expected diagnostics report path was reviewed, but a separate Device diagnostics report was not visible in the expected Devices Monitor view for this tenant.

### Step 4: Device action status was used instead

The device-level action status view was checked:

```text
WINAUTO452
-> Device action status
```

Observed result:

```text
Collect diagnostics
Request status: Complete
```

### Step 5: Tenant diagnostics settings were reviewed

Tenant-level diagnostics settings were checked from:

```text
Tenant administration
-> Device diagnostics
```

This confirmed that device diagnostics features were enabled in the tenant.

---

## Resolution

The lab was validated using the device-level action status page.

Final result:

```text
Collect diagnostics completed successfully for WINAUTO452.
```

The actual diagnostic package was not uploaded to GitHub because diagnostics can contain sensitive device or user information.

---

## Evidence Screenshots

### Device overview before action

![Device overview before action](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-01-device-overview.png)

### Collect diagnostics action selected

![Collect diagnostics action selected](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-02-collect-diagnostics-action-selected.png)

### Confirm collect diagnostics

![Confirm collect diagnostics](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-03-confirm-collect-diagnostics.png)

### Device action status complete

![Device action status complete](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-04-device-action-status-complete.png)

### Device diagnostics settings enabled

![Device diagnostics settings enabled](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-05-device-diagnostics-settings-enabled.png)

---

## Key Learning

The main lesson from this troubleshooting case is:

```text
If the exact documented report view is not visible, validate the remote action from the device-level action status and related tenant settings.
```

For Intune remote actions, useful validation locations include:

```text
Device overview page
Device action status
Devices -> Monitor -> Device actions
Tenant administration -> Device diagnostics
```

---

## Diagnostic Data Handling

Diagnostic ZIP packages should not be uploaded to a public GitHub portfolio.

Reason:

```text
Diagnostic packages can include user, device, tenant, log, and configuration data.
```

For public documentation, screenshots showing the action result are enough.

---

## Admin Checklist for Similar Issues

If the diagnostics report is difficult to find:

1. Confirm the device is Intune managed.
2. Confirm the device is online.
3. Trigger Collect diagnostics from the device overview page.
4. Check the device-level Device action status tab.
5. Check Devices -> Monitor -> Device actions if available.
6. Review Tenant administration -> Device diagnostics settings.
7. Do not upload diagnostic packages to GitHub.
8. Document any portal UI differences as an observation.

---

## Related Files

```text
07-remote-actions-and-monitoring/collect-diagnostics.md
07-remote-actions-and-monitoring/device-monitoring-and-reports.md
08-troubleshooting/troubleshooting-summary.md
```

---

## Final Status

| Task | Status |
|---|---|
| Collect diagnostics action triggered | Completed |
| Device action status checked | Completed |
| Action completed successfully | Completed |
| Tenant diagnostics settings reviewed | Completed |
| Diagnostic ZIP excluded from GitHub | Completed |
| Troubleshooting case documented | Completed |
