# Collect Diagnostics Remote Action

This lab documents how to trigger the **Collect diagnostics** remote action for a Windows device from the Microsoft Intune admin center and verify that the action completes successfully.

---

## Objective

Use Microsoft Intune remote actions to collect diagnostic information from an enrolled Windows device for troubleshooting.

This lab validates that:

- A managed Windows device can be opened from the Intune admin center.
- The **Collect diagnostics** remote action is available from the device overview page.
- The collect diagnostics request can be confirmed from Intune.
- The action status can be monitored from the device-level **Device action status** tab.
- Tenant-level device diagnostics settings can be reviewed under **Tenant administration**.
- Diagnostic packages are treated as sensitive data and are not uploaded to GitHub.

---

## Why This Lab Matters

In real endpoint administration, users may report issues such as failed policy deployment, enrollment problems, compliance errors, app installation failures, Windows Autopilot issues, or general device behavior problems.

Instead of asking the user to manually gather logs, an Intune administrator can remotely collect diagnostics from the device. This helps support teams investigate problems without needing direct physical access to the endpoint.

Simple flow:

```text
Intune admin center
-> Open managed Windows device
-> Trigger Collect diagnostics
-> Device uploads diagnostic data to Intune
-> Admin monitors the action status
-> Admin downloads/reviews diagnostics if required
```

This is useful for troubleshooting distributed or remote Windows devices where hands-on access is limited.

---

## Lab Environment

| Item | Value |
|---|---|
| Management platform | Microsoft Intune |
| Device platform | Windows |
| Test device | WINAUTO452 |
| Device ownership | Corporate |
| Device state | Compliant |
| Managed by | Intune |
| Primary user | user01 |
| Lab section | Remote Actions and Monitoring |
| Current status | Completed |

---

## Prerequisites

Before starting this lab, the following should already be completed:

- Windows device enrolled into Microsoft Intune.
- Device visible in the Intune admin center.
- Device has internet connectivity.
- Device is corporate-owned or otherwise eligible for diagnostics collection.
- Signed-in admin account has permission to perform the **Collect diagnostics** remote action.
- Tenant device diagnostics settings are enabled.

---

## Important Notes

This lab uses the **Collect diagnostics** remote action only.

The following destructive remote actions were not performed in this lab:

```text
Retire
Wipe
Delete
Autopilot reset
Fresh start
```

Those actions can remove data, reset the device, or remove management. They should be tested only in dedicated reset/removal labs.

---

## Remote Action Used

| Remote Action | Purpose | Risk Level |
|---|---|---|
| Collect diagnostics | Collects troubleshooting logs and diagnostic data from the managed device | Medium |

The risk level is marked as **Medium** because the action is not destructive, but the collected diagnostic package can contain sensitive device or user-identifiable information.

---

## Steps Performed

### Step 1: Opened the Windows Device in Intune

Navigation used:

```text
Microsoft Intune admin center
-> Devices
-> Windows
-> Windows devices
-> WINAUTO452
```

The device overview page confirmed:

- Device name: `WINAUTO452`
- Compliance state: `Compliant`
- Ownership: `Corporate`
- Managed by: `Intune`
- Primary user was visible.
- Last check-in time was visible.
- The **Collect diagnostics** action was available in the top action bar.

---

### Step 2: Selected Collect Diagnostics

From the device overview page, the following remote action was selected:

```text
Collect diagnostics
```

This opened the collect diagnostics confirmation prompt for the selected Windows device.

---

### Step 3: Confirmed Collect Diagnostics Action

The confirmation dialog explained that Intune would attempt to collect diagnostics from the device.

The action was confirmed by selecting:

```text
Collect data
```

The confirmation dialog also referenced the diagnostics monitoring location:

```text
Monitor -> Device diagnostics
```

---

### Step 4: Monitored Device Action Status

After the request was submitted, the device-level action status was reviewed from the device page.

Navigation used:

```text
WINAUTO452
-> Device action status
```

The action list showed:

```text
Action: Collect diagnostics
Request status: Complete
```

Observed result:

```text
Collect diagnostics completed successfully for WINAUTO452
```

---

### Step 5: Reviewed Tenant Device Diagnostics Settings

The tenant-level diagnostics settings were reviewed from:

```text
Tenant administration
-> Device diagnostics
```

The following settings were visible as enabled:

- Device diagnostics for corporate-managed Windows devices.
- Automatic diagnostic capture during Windows Autopilot failures.
- Diagnostic data for devices managed by Intune app protection policy.

This confirmed that the tenant had diagnostics-related settings enabled.

---

## Portal UI Observation

Microsoft documentation mentions checking collection status from:

```text
Monitor -> Device diagnostics
```

In this lab tenant, a separate **Device diagnostics** report was not visible under **Devices -> Monitor**. Instead, the successful result was verified from the device-level **Device action status** tab.

This was accepted as valid lab evidence because the device page clearly showed:

```text
Collect diagnostics -> Complete
```

The tenant-level diagnostics settings page was also reviewed separately under:

```text
Tenant administration -> Device diagnostics
```

---

## Diagnostic ZIP Handling

The diagnostic ZIP package was **not uploaded to GitHub**.

Reason:

```text
Diagnostic packages can include user-identifiable or device-identifiable information.
```

For a public learning portfolio, screenshots proving the action was completed are enough. The actual diagnostic package should be treated as sensitive operational data.

---

## Expected Result

After this lab:

- The Windows device should remain visible in Intune.
- The **Collect diagnostics** action should be available from the device overview action bar.
- The confirmation prompt should appear.
- The diagnostic collection request should be submitted.
- The device action status should show the request as complete.
- Tenant diagnostics settings should be enabled.
- No diagnostic ZIP should be uploaded to the public GitHub repository.

---

## Test Result

| Test Item | Result |
|---|---|
| Windows device opened in Intune | Completed |
| Device status verified as Compliant | Completed |
| Device verified as Intune managed | Completed |
| Collect diagnostics action selected | Completed |
| Collect diagnostics confirmation prompt displayed | Completed |
| Collect data action confirmed | Completed |
| Device action status reviewed | Completed |
| Collect diagnostics action completed | Completed |
| Tenant diagnostics settings reviewed | Completed |
| Diagnostic ZIP excluded from GitHub | Completed |
| Final lab result | Completed |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

### Device overview

![Device overview](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-01-device-overview.png)

### Collect diagnostics action selected

![Collect diagnostics action selected](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-02-collect-diagnostics-action-selected.png)

### Confirm collect diagnostics

![Confirm collect diagnostics](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-03-confirm-collect-diagnostics.png)

### Device action status complete

![Device action status complete](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-04-device-action-status-complete.png)

### Device diagnostics settings enabled

![Device diagnostics settings enabled](../screenshots/sanitized/remote-actions-and-monitoring/collect-diagnostics-05-device-diagnostics-settings-enabled.png)

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, serial numbers, device identifiers, account identifiers, and top-right signed-in account details should be hidden before publishing publicly.

---

## Screenshot Files

```text
collect-diagnostics-01-device-overview.png
collect-diagnostics-02-collect-diagnostics-action-selected.png
collect-diagnostics-03-confirm-collect-diagnostics.png
collect-diagnostics-04-device-action-status-complete.png
collect-diagnostics-05-device-diagnostics-settings-enabled.png
```

---

## Observations

The collect diagnostics action completed successfully on the test Windows device.

The device-level **Device action status** tab showed the action as complete. This provides strong evidence that the remote diagnostic request was processed successfully by Intune.

The tenant diagnostics settings page confirmed that diagnostics features were enabled. This is important because diagnostics collection depends on tenant/device support and communication with the Intune service.

The actual diagnostic ZIP was not included in this repository because diagnostic data can contain sensitive device or user information.

---

## Troubleshooting Notes

If **Collect diagnostics** is not visible:

1. Confirm the device is enrolled in Intune.
2. Confirm the device is a supported platform.
3. Confirm the device is corporate-owned when required.
4. Confirm the admin role has permission to run the remote action.
5. Check whether the action is hidden under the overflow menu.

If the action remains pending:

1. Confirm the device is powered on.
2. Confirm the device has internet connectivity.
3. Confirm the device can communicate with Intune.
4. Wait and refresh the device action status page.
5. Sync the device if needed.
6. Restart the device if the action does not complete after a long time.

If diagnostics fail:

1. Check whether the device was online during the request window.
2. Check whether diagnostics settings are enabled under **Tenant administration -> Device diagnostics**.
3. Confirm required network endpoints are not blocked.
4. Review whether the device can upload diagnostic data.
5. Re-run the action only if required.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Diagnostic ZIP packages
- Full real email addresses
- Real tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Exchange IDs
- Internal IP addresses
- Passwords
- MFA codes or QR codes
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Device identifiers
- Serial numbers
- Local account identifiers
- Organization-specific identifiers

---

## References

- Microsoft Learn: Device action: Collect diagnostics  
  https://learn.microsoft.com/en-us/intune/device-management/actions/collect-diagnostics

- Microsoft Learn: Device actions in Microsoft Intune  
  https://learn.microsoft.com/en-us/intune/device-management/actions/

---

## Current Status

| Task | Status |
|---|---|
| collect-diagnostics.md created | Completed |
| Device opened in Intune | Completed |
| Collect diagnostics action selected | Completed |
| Confirmation prompt captured | Completed |
| Collect diagnostics completed | Completed |
| Tenant diagnostics settings reviewed | Completed |
| Screenshots added | Completed |
| Diagnostic ZIP excluded from GitHub | Completed |
| Final lab status | Completed |

---

## Next Step

Continue to the next Remote Actions and Monitoring lab:

```text
07-remote-actions-and-monitoring/restart-device-remote-action.md
```

Recommended approach for the next lab:

```text
Start with Restart only
Do not test Wipe, Delete, Retire, Fresh Start, or Autopilot Reset on the active lab device unless intentionally testing device reset behavior
```
