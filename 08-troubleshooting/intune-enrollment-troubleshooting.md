# Intune Enrollment Troubleshooting

This troubleshooting case study documents a real issue from the Windows OOBE enrollment lab where a device successfully joined Microsoft Entra ID, but did not immediately enroll into Microsoft Intune.

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
02-device-enrollment/windows-oobe-enrollment.md
```

Screenshots are reused from the existing device enrollment evidence folder:

```text
screenshots/sanitized/device-enrollment/
```

---

## Issue Summary

During the Windows OOBE enrollment lab, the device completed Microsoft Entra join but did not immediately appear as managed by Intune.

Observed issue:

```text
Device name: WIN-CORP-001
Join type: Microsoft Entra joined
MDM: None
```

Meaning:

```text
Microsoft Entra join completed.
Intune MDM enrollment had not completed yet.
```

---

## Why This Matters

A Windows device can exist in Microsoft Entra ID without being managed by Intune.

| State | Meaning |
|---|---|
| Microsoft Entra joined | Device is joined to cloud identity |
| MDM: None | No MDM provider is managing the device |
| Managed by Intune | Device can receive Intune policies and apps |

For endpoint administrators, this distinction matters because configuration profiles, compliance policies, app deployment, and endpoint security policies require Intune management.

---

## Lab Environment

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Platform | Windows 11 |
| Test user | user01 |
| Initial identity state | Microsoft Entra joined |
| Initial MDM state | None |
| Final MDM state | Managed by Intune |
| Final compliance state | Compliant |
| Final ownership in Intune | Personal |

---

## Troubleshooting Timeline

### Step 1: Windows OOBE completed

The device was reimaged and configured through Windows OOBE.

The device name used during setup was:

```text
WIN-CORP-001
```

The test user was:

```text
user01
```

### Step 2: Work or school connection verified locally

Local Windows path checked:

```text
Settings
-> Accounts
-> Access work or school
```

The device showed a connected work or school account.

### Step 3: Microsoft Entra device record checked

The Microsoft Entra device record showed:

```text
Join type: Microsoft Entra joined
MDM: None
```

This confirmed that identity join worked, but Intune MDM enrollment was not complete.

### Step 4: Intune device list checked

The Intune Windows device list did not show the device at first.

This matched the Microsoft Entra finding that MDM was still set to `None`.

### Step 5: Manual MDM enrollment completed

Manual MDM enrollment was completed from the Windows device.

After the device checked in, the device appeared in the Intune admin center.

### Step 6: Final Intune state verified

Final observed state:

```text
Device: WIN-CORP-001
Managed by: Intune
Compliance: Compliant
Primary user: user01
Ownership: Personal
```

---

## Root Cause Analysis

The device did not fail Microsoft Entra join. The issue was that MDM enrollment was not complete at the time of validation.

Common checks for similar cases:

- MDM user scope is set to All or correctly targets the user/group.
- The user has an Intune-capable license.
- Device enrollment restrictions allow Windows enrollment.
- Device check-in and sync have completed.
- Enrollment failures are reviewed in Intune.
- Manual enrollment may be required in a lab recovery scenario.

---

## Troubleshooting Checklist

### Check Microsoft Entra device state

```text
Microsoft Entra admin center
-> Devices
-> All devices
```

Look for:

```text
Join type: Microsoft Entra joined
MDM provider
```

### Check MDM user scope

```text
Microsoft Entra admin center
-> Identity
-> Mobility (MDM and WIP)
-> Microsoft Intune
```

Expected lab configuration:

```text
MDM user scope: All
```

or:

```text
MDM user scope: Some
Target group includes user01 or GRP-Pilot-Users
```

### Check user license

Confirm `user01` has an Intune-capable license.

### Check enrollment failures

```text
Intune admin center
-> Devices
-> Monitor
-> Enrollment failures
```

### Sync and retry enrollment

Sync the device from Windows Settings and retry enrollment if needed.

---

## Resolution

Manual MDM enrollment was completed from the Windows device.

Final result:

```text
WIN-CORP-001 appeared in Intune as managed by Intune and compliant.
```

---

## Evidence Screenshots

### Access work or school connection

![Access work or school connection](../screenshots/sanitized/device-enrollment/win-corp-001-access-work-school-sanitized.png)

### Microsoft Entra device record showing MDM None

![Microsoft Entra device record showing MDM None](../screenshots/sanitized/device-enrollment/win-corp-001-entra-device-mdm-none-sanitized.png)

### Intune Windows devices list after successful enrollment

![Intune Windows devices list after successful enrollment](../screenshots/sanitized/device-enrollment/win-corp-001-intune-windows-devices-list-sanitized.png)

### Intune device overview after successful enrollment

![Intune device overview after successful enrollment](../screenshots/sanitized/device-enrollment/win-corp-001-intune-overview-sanitized.png)

---

## Key Learning

```text
Microsoft Entra joined does not automatically prove that the device is managed by Intune.
```

Always verify both:

```text
Join state
MDM management state
```

---

## Related Files

```text
02-device-enrollment/windows-oobe-enrollment.md
00-project-overview/device-inventory.md
08-troubleshooting/troubleshooting-summary.md
```

---

## Final Status

| Task | Status |
|---|---|
| Issue identified | Completed |
| MDM None state documented | Completed |
| Manual MDM enrollment completed | Completed |
| Device visible in Intune | Completed |
| Troubleshooting case documented | Completed |
