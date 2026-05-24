# Device Sync Remote Action

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Remote actions and monitoring |
| Remote action | Sync |
| Test device | WINAUTO452 |
| Result | Sync completed — last check-in updated |

---

## Lab Objective

Trigger the Sync remote action on WINAUTO452 from the Intune admin center, verify the last check-in updates, and confirm local sync from Windows Settings.

---

## Why This Lab Matters

When a policy, app, or compliance rule is assigned in Intune, the device may not receive it immediately. Triggering a sync requests the device to check in and apply the latest configuration. This is one of the most common first steps in Intune troubleshooting.

---

## Prerequisites

- WINAUTO452 enrolled in Intune with internet connectivity
- Admin account has permission to perform Intune remote actions

---

## Remote Action Reference

| Action | Purpose | Risk |
|---|---|---|
| Sync | Requests the device to check in with Intune and apply latest policies | Low — non-destructive |

---

## Steps Performed

### Step 1 — Triggered sync from Intune

Navigated to:

```text
Devices -> Windows -> Windows devices -> WINAUTO452
```

Confirmed device state (Compliant, Corporate, Intune managed) and noted the last check-in time. Selected Sync from the action bar, confirmed the prompt, and received the notification:

```text
Sync initiated — Sync will occur when the device is notified.
```

![Device overview before sync](../screenshots/sanitized/remote-actions-and-monitoring/device-sync-remote-actions-01-device-overview-before-sync.png)

![Remote sync confirmation](../screenshots/sanitized/remote-actions-and-monitoring/device-sync-remote-actions-02-remote-sync-confirmation.png)

![Sync initiated notification](../screenshots/sanitized/remote-actions-and-monitoring/device-sync-remote-actions-03-sync-initiated-notification.png)

---

### Step 2 — Verified last check-in updated

After the sync, refreshed the device overview. The last check-in time updated, confirming the device communicated with Intune.

![Last check-in after remote sync](../screenshots/sanitized/remote-actions-and-monitoring/device-sync-remote-actions-04-last-check-in-after-remote-sync.png)

---

### Step 3 — Performed local sync from Windows Settings

On WINAUTO452, navigated to:

```text
Settings -> Accounts -> Access work or school -> Managed by HomeLAB -> Device sync status -> Sync
```

The page confirmed:

```text
The sync was successful
```

![Local Windows sync success](../screenshots/sanitized/remote-actions-and-monitoring/device-sync-remote-actions-05-local-windows-sync-success.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Remote Sync action triggered from Intune | Completed |
| Sync initiated notification received | Completed |
| Last check-in time updated after sync | Completed |
| Local Windows sync confirmed successful | Completed |

---

## Troubleshooting Notes

**Sync action not visible** — confirm the device is enrolled, the platform supports the action, the admin role has the required permissions, and check whether the action is in the overflow menu.

**Sync initiated but device doesn't check in** — confirm the device is powered on with internet access. Wait several minutes, refresh the device overview, and perform a local sync from Windows Settings as a secondary confirmation.

**Local sync fails** — confirm the work or school account is still connected, the device is enrolled, and the user has a valid Intune-capable license. Restart the device and retry.

---

## Enterprise Reflection

Sync is the non-destructive first action in any Intune troubleshooting workflow. Before investigating policy failures, app deployment issues, or compliance delays, triggering a sync ensures the device has the latest state from Intune. Both the remote sync from the admin center and the local sync from Windows Settings are valid approaches — the local sync is useful when the device is accessible and the admin wants immediate confirmation.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` | More impactful remote actions performed after sync validation |
| `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Monitoring views that show device check-in and action status |

---

## Key Learning Outcomes

- How to trigger the Sync remote action from the Intune admin center
- How to confirm sync success using last check-in time rather than waiting for the device action status report
- How to perform a local sync from Windows Settings as a secondary validation
- When sync is the appropriate first troubleshooting step before investigating policy or compliance issues
