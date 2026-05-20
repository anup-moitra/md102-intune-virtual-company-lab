# Restart, Retire, and Wipe Remote Actions

This lab documents the use of Microsoft Intune remote device actions for Windows devices.

The lab validates how remote actions are initiated from the Intune admin center and how their status is confirmed from the device action status page and the Device Actions monitoring report.

> **Important:** Retire and Wipe are destructive or semi-destructive actions. In a production environment, these actions should only be used after confirming device ownership, business impact, backup requirements, and approval. In this lab, the actions were performed in a test environment.

---

## Lab Information

| Item | Details |
|---|---|
| Lab section | 07 - Remote Actions and Monitoring |
| Lab file | `restart-retire-wipe-actions.md` |
| Portal | Microsoft Intune admin center |
| Primary test device | `WINAUTO452` |
| Additional test device | `WIN-CORP-001` |
| Platform | Windows |
| Management authority | Intune |
| Main actions tested | Restart, Retire, Wipe |
| Result | Remote actions completed and validated |

---

## Lab Objective

The objective of this lab was to validate Intune remote actions by performing and monitoring the following actions:

- Restart a managed Windows device.
- Review and perform Retire on a managed Windows device.
- Review and perform Wipe on a separate test Windows device.
- Confirm remote action status from the device page and the Device Actions report.

---

## Why This Lab Matters

In a real endpoint administration role, Intune remote actions are used to support devices without requiring physical access.

Examples:

| Remote action | Real-world use case |
|---|---|
| Restart | Restart a managed device after policy deployment, update installation, or troubleshooting. |
| Retire | Remove company data and Intune management from a device that is no longer used for work. |
| Wipe | Factory reset a lost, repurposed, or compromised device. |

These actions are powerful because they can affect device access, user data, and management state. For that reason, every remote action should be verified from Intune monitoring reports.

---

## Important Action Difference

| Action | What it does | Data impact | Used in this lab |
|---|---|---|---|
| Restart | Sends a restart command to the device. | No data removal. | Yes |
| Retire | Removes company data and Intune management. Personal data is generally preserved. | Removes work management and corporate data. | Yes |
| Wipe | Factory resets the device. | Removes personal and company data/settings. | Yes |

---

## Devices Used

| Device | Action performed | Final observed result |
|---|---|---|
| `WINAUTO452` | Restart | Completed |
| `WINAUTO452` | Retire | Initiated and completed in the Device Actions report |
| `WIN-CORP-001` | Wipe | Initiated and completed in the Device Actions report |

---

## Prerequisites

Before starting this lab, the following items were already completed:

- At least one Windows device was enrolled into Intune.
- The device appeared under Windows devices.
- The device had checked in successfully.
- The account had permission to perform remote actions.
- Test devices were available for destructive action validation.

---

## Step 1: Open the Windows Device

Navigation path:

```text
Microsoft Intune admin center
-> Devices
-> Windows
-> Windows devices
-> Select device
```

The primary test device used was:

```text
WINAUTO452
```

The device overview page showed the device as Intune-managed and compliant.

![Device overview](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-01-device-overview.png)

---

## Step 2: Locate Restart Under Remote Actions

In the current Intune admin center interface, the Restart action was available under:

```text
Remote actions
-> Restart
```

This confirmed that Restart is grouped under the Remote actions menu for the selected Windows device.

![Remote actions restart menu](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-02-remote-actions-restart-menu.png)

---

## Step 3: Trigger Restart

The Restart action was initiated for:

```text
WINAUTO452
```

After the restart command was sent, the device action status showed the Restart action as pending.

![Restart status pending](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-03-restart-status-pending.png)

After the device received and processed the command, the action status changed to Complete.

![Restart status complete](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-04-restart-status-complete.png)

---

## Step 4: Review Remove Data Actions

The Remove data menu included the following actions:

```text
Retire
Wipe
Fresh start
Autopilot reset
```

The menu was reviewed to understand where destructive remote actions are located in the Intune admin center.

![Remove data menu](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-05-remove-data-menu.png)

---

## Step 5: Retire Action Confirmation

The Retire confirmation dialog was opened for:

```text
WINAUTO452
```

The confirmation screen explained that Retire removes company data managed by Intune and that the user's personal data is not removed.

![Retire confirmation](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-06-retire-confirmation.png)

The Retire action was initiated and appeared as pending on the device action status page.

![Retire status pending](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-07-retire-status-pending.png)

---

## Step 6: Wipe Action Confirmation

The Wipe confirmation dialog was opened for a separate test device:

```text
WIN-CORP-001
```

The confirmation screen explained that factory reset returns the device to default settings and removes personal and company data from the device.

![Wipe confirmation](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-08-wipe-confirmation.png)

---

## Step 7: Validate Action Notifications

The notification panel showed that multiple remote actions were initiated:

```text
Restart initiated
Retire initiated
Wipe initiated
```

This confirmed that Intune accepted the remote action requests and queued them for the target devices.

![Notifications actions initiated](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-09-notifications-actions-initiated.png)

---

## Step 8: Validate Actions from Device Actions Report

Navigation path:

```text
Devices
-> Monitor
-> Device actions
```

The Device Actions report showed the final status for the remote actions.

Observed results:

| Device | Action | Status |
|---|---|---|
| `WIN-CORP-001` | Wipe | Complete |
| `WINAUTO452` | Retire | Complete |
| `WINAUTO452` | Restart | Complete |

![Device actions report complete](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-10-device-actions-report-complete.png)

---

## Step 9: Confirm Device Impact After Wipe

After the Wipe action completed for `WIN-CORP-001`, the Intune device record was no longer available from the opened device page and returned a Not found page.

This is expected behavior after a device wipe/removal workflow because the device record or page state can change after the remote action completes.

![WIN-CORP-001 not found after wipe](../screenshots/sanitized/remote-actions-and-monitoring/restart-retire-wipe-11-win-corp-not-found-after-wipe.png)

---

## Final Results

| Validation item | Result |
|---|---|
| Restart action located under Remote actions | Completed |
| Restart initiated on WINAUTO452 | Completed |
| Restart status monitored | Completed |
| Retire action reviewed and initiated on WINAUTO452 | Completed |
| Wipe action reviewed and initiated on WIN-CORP-001 | Completed |
| Device Actions report checked | Completed |
| Final action status documented | Completed |

---

## Key Observations

- Restart appears under the **Remote actions** menu.
- Retire and Wipe appear under the **Remove data** menu.
- Device action status can be checked from the individual device page.
- Tenant-wide remote action history can be checked from **Devices > Monitor > Device actions**.
- Restart completed successfully for `WINAUTO452`.
- Retire completed for `WINAUTO452`.
- Wipe completed for `WIN-CORP-001`.
- After the Wipe action, the `WIN-CORP-001` device page showed a Not found message.

---

## Troubleshooting Notes

### Restart shows Pending

If Restart remains pending:

- Confirm the device is online.
- Confirm the device has internet access.
- Trigger a device sync from Intune or from Windows Settings.
- Refresh the Device action status page.
- Check **Devices > Monitor > Device actions**.

### Retire or Wipe does not complete

If Retire or Wipe remains pending:

- Confirm the device is connected to the internet.
- Confirm the device has checked in recently.
- Confirm the device is still enrolled in Intune.
- Review the Device Actions report.
- Wait for the device to receive the command.

### Device page shows Not found

If a device page shows Not found after Wipe or Retire:

- Refresh the Windows devices list.
- Search for the device by name.
- Check Device Actions report for completion.
- Confirm whether the device record was removed or reset.

---

## Lessons Learned

- Remote actions are not just buttons; they are administrative commands with real device impact.
- Restart is safe for most active troubleshooting scenarios.
- Retire and Wipe should be treated as high-impact actions.
- Device action status is important evidence for confirming whether a remote action was actually processed.
- Screenshots of confirmation dialogs and Device Actions reports are valuable for audit and troubleshooting documentation.

---

## Screenshot Evidence

| Screenshot | Description |
|---|---|
| `restart-retire-wipe-01-device-overview.png` | WINAUTO452 device overview before remote actions. |
| `restart-retire-wipe-02-remote-actions-restart-menu.png` | Restart available under Remote actions. |
| `restart-retire-wipe-03-restart-status-pending.png` | Restart action pending. |
| `restart-retire-wipe-04-restart-status-complete.png` | Restart action completed. |
| `restart-retire-wipe-05-remove-data-menu.png` | Retire, Wipe, Fresh start, and Autopilot reset options. |
| `restart-retire-wipe-06-retire-confirmation.png` | Retire confirmation screen. |
| `restart-retire-wipe-07-retire-status-pending.png` | Retire action pending on WINAUTO452. |
| `restart-retire-wipe-08-wipe-confirmation.png` | Wipe confirmation screen for WIN-CORP-001. |
| `restart-retire-wipe-09-notifications-actions-initiated.png` | Notifications showing Restart, Retire, and Wipe initiated. |
| `restart-retire-wipe-10-device-actions-report-complete.png` | Device Actions report showing completed actions. |
| `restart-retire-wipe-11-win-corp-not-found-after-wipe.png` | Device page not found after Wipe action. |

---

## Security and Safety Notes

For production environments:

- Do not perform Retire or Wipe without approval.
- Confirm the target device name before sending the action.
- Confirm the assigned user and ownership.
- Confirm whether the device is corporate or personal.
- Export or document action status for audit evidence.
- Avoid using destructive actions on active production devices unless required.

---

## Related Files

```text
07-remote-actions-and-monitoring/collect-diagnostics.md
07-remote-actions-and-monitoring/device-monitoring-and-reports.md
08-troubleshooting/remote-actions-diagnostics-troubleshooting.md
```

---

## Final Lab Status

| Item | Status |
|---|---|
| Restart action tested | Completed |
| Retire action tested | Completed |
| Wipe action tested | Completed |
| Device action status validated | Completed |
| Screenshots captured | Completed |
| Lab documentation completed | Completed |
