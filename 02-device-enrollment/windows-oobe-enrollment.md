# Windows OOBE Enrollment

## Lab status

**Status:** Completed  
**Lab category:** Device enrollment  
**Platform:** Windows 10 and later  
**Management platform:** Microsoft Intune  
**Enrollment method:** Windows out-of-box experience (OOBE)  
**Join type:** Microsoft Entra joined  
**Initial device name:** WIN-CORP-001  
**Primary test user:** user01  
**Final ownership result:** Personal  
**Final management result:** Managed by Intune  

---

## Lab objective

The objective of this lab is to enroll a Windows device into Microsoft Intune during the Windows out-of-box experience.

This lab validates that:

- A Windows device can be configured during OOBE using a work or school account.
- The device can join Microsoft Entra ID.
- The device can appear in Microsoft Intune.
- Enrollment status can be checked from the endpoint and the Intune admin center.
- An enrollment issue can be identified and resolved.
- The final managed device state can be documented with screenshots.

Final result:

```text
WIN-CORP-001 appeared in Microsoft Intune as managed by Intune and compliant.
```

---

## Why this lab matters

Windows OOBE enrollment is one of the first practical steps in learning Microsoft Intune device management.

In real environments, administrators need to understand how a Windows device becomes:

```text
Microsoft Entra joined
-> Enrolled into Intune
-> Managed by policies and apps
-> Reported in Intune inventory
```

This lab is important because it shows the difference between:

| Scenario | Result |
|---|---|
| Microsoft Entra joined only | Device is joined to cloud identity but may not be managed by Intune |
| Microsoft Entra joined + MDM enrolled | Device is joined and managed by Intune |
| Manual Windows enrollment | Useful for testing, but often results in Personal ownership |
| Windows Autopilot enrollment | Better corporate provisioning method for production devices |

This lab also produced a useful troubleshooting scenario where the device initially showed:

```text
MDM: None
```

That issue was later resolved by completing manual MDM enrollment.

---

## Lab environment

| Item | Value |
|---|---|
| Admin portal | Microsoft Intune admin center |
| Identity platform | Microsoft Entra ID |
| Device platform | Windows 11 |
| Enrollment method | Windows OOBE / work or school setup |
| Test device name | `WIN-CORP-001` |
| Test user | `user01` |
| Initial issue | Device showed `MDM: None` |
| Resolution | Manual MDM enrollment from Windows Settings |
| Final management state | Managed by Intune |
| Final compliance state | Compliant |
| Final ownership state | Personal |

---

## Prerequisites

Before starting this lab, the following were completed:

- Microsoft Entra ID tenant available.
- Microsoft Intune tenant available.
- Test user `user01` created.
- `user01` assigned the required Intune/Microsoft 365 license.
- Automatic MDM enrollment settings reviewed.
- Windows test device available for reset or clean setup.
- Internet connectivity available during Windows OOBE.
- Access to Microsoft Intune admin center.
- Screenshots sanitized before upload to the public GitHub repository.

---

## Deployment / Configuration flow

Simple enrollment flow:

```text
Reset or prepare Windows device
-> Start Windows OOBE
-> Select work or school setup
-> Sign in with user01
-> Join device to Microsoft Entra ID
-> Check Microsoft Entra device state
-> Check MDM/Intune enrollment state
-> Troubleshoot MDM: None if required
-> Complete manual MDM enrollment
-> Verify device in Intune
-> Confirm compliance visibility
```

Expected successful result:

```text
Device appears in Intune
-> Managed by Intune
-> Compliance state visible
-> Device can receive policies and apps
```

---

## Steps performed

### Step 1: Prepared the Windows device

A spare Windows 11 device was prepared for enrollment testing.

The device was reset/reimaged so that the Windows out-of-box experience could be completed from the beginning.

Target device name used during setup:

```text
WIN-CORP-001
```

---

### Step 2: Started Windows OOBE

During Windows OOBE, the device was configured using the work or school setup option.

This allowed the device to connect to the Microsoft Entra ID tenant during initial Windows setup.

---

### Step 3: Signed in with the test user

The device was signed in using the lab user:

```text
user01
```

The goal was to join the Windows device to Microsoft Entra ID and begin the device enrollment process.

---

### Step 4: Verified Microsoft Entra join

After OOBE completed, the device was checked from Windows and the admin portals.

The device successfully joined Microsoft Entra ID.

At this stage, the device was present in the cloud identity environment, but the MDM state still needed to be validated.

---

### Step 5: Identified initial MDM enrollment issue

During validation, the device showed:

```text
MDM: None
```

This meant the device was Microsoft Entra joined, but it was not yet managed by Intune.

This was an important troubleshooting finding because a device can be joined to Microsoft Entra ID without being fully enrolled into Intune MDM.

---

### Step 6: Triggered manual MDM enrollment

To resolve the issue, manual MDM enrollment was completed from Windows Settings.

Local Windows path used:

```text
Settings
-> Accounts
-> Access work or school
-> Enroll only in device management
```

After enrollment, the device was synced and checked again.

---

### Step 7: Verified the device in Intune

The device appeared in Microsoft Intune as a managed Windows device.

Validated device:

```text
WIN-CORP-001
```

Final management result:

```text
Managed by Intune
```

Final compliance visibility:

```text
Compliant
```

---

### Step 8: Documented the ownership result

The device appeared as:

```text
Ownership: Personal
```

This was expected for this enrollment path because the device was manually enrolled rather than provisioned through Windows Autopilot as a corporate device.

This became a useful comparison point for the later Windows Autopilot lab, where the Autopilot-enrolled device appeared as corporate-owned.

---

## Validation

Validation was completed in three places:

1. Windows endpoint settings
2. Microsoft Entra ID device view
3. Microsoft Intune device view

### Endpoint validation

The endpoint showed the work or school account connection and completed device management enrollment after manual MDM enrollment.

### Microsoft Entra validation

The device was visible as a Microsoft Entra joined Windows device.

### Microsoft Intune validation

The device appeared in Intune with management and compliance status visible.

Observed final result:

```text
WIN-CORP-001 appeared in Intune as managed by Intune and compliant.
```

Ownership observation:

```text
The device ownership showed as Personal after manual MDM enrollment.
```

---

## Final test result

| Validation item | Status |
|---|---|
| Windows device prepared for OOBE | Completed |
| Work or school setup selected | Completed |
| Signed in with `user01` | Completed |
| Microsoft Entra join completed | Completed |
| Initial MDM issue identified | Completed |
| Device initially showed `MDM: None` | Completed |
| Manual MDM enrollment triggered | Completed |
| Device appeared in Intune | Completed |
| Device showed managed by Intune | Completed |
| Compliance visibility confirmed | Completed |
| Ownership result documented as Personal | Completed |
| Final lab result | Completed |

Final observed result:

```text
WIN-CORP-001 appeared in Microsoft Intune as managed by Intune and compliant.
```

---

## Screenshots captured

Screenshots for this lab are stored in:

```text
screenshots/sanitized/device-enrollment/
```

### Windows OOBE region selection

![Windows OOBE region selection](../screenshots/sanitized/device-enrollment/windows-oobe-region-selection-sanitized.png)

### Windows OOBE device name

![Windows OOBE device name](../screenshots/sanitized/device-enrollment/windows-oobe-device-name-sanitized.png)

### Windows OOBE work or school selection

![Windows OOBE work or school selection](../screenshots/sanitized/device-enrollment/windows-oobe-work-school-selection-sanitized.png)

### Windows OOBE user sign-in

![Windows OOBE user sign-in](../screenshots/sanitized/device-enrollment/windows-oobe-user01-signin-sanitized.png)

### Windows device name verification

![Windows device name verification](../screenshots/sanitized/device-enrollment/win-corp-001-device-name-sanitized.png)

### Access work or school verification

![Access work or school verification](../screenshots/sanitized/device-enrollment/win-corp-001-access-work-school-sanitized.png)

### Entra device record with initial MDM status

![Entra device record with initial MDM status](../screenshots/sanitized/device-enrollment/win-corp-001-entra-device-mdm-none-sanitized.png)

### Intune Windows devices list

![Intune Windows devices list](../screenshots/sanitized/device-enrollment/win-corp-001-intune-windows-devices-list-sanitized.png)

### Intune device overview

![Intune device overview](../screenshots/sanitized/device-enrollment/win-corp-001-intune-overview-sanitized.png)

### Uploaded screenshot files

```text
windows-oobe-region-selection-sanitized.png
windows-oobe-device-name-sanitized.png
windows-oobe-work-school-selection-sanitized.png
windows-oobe-user01-signin-sanitized.png
win-corp-001-device-name-sanitized.png
win-corp-001-access-work-school-sanitized.png
win-corp-001-entra-device-mdm-none-sanitized.png
win-corp-001-intune-windows-devices-list-sanitized.png
win-corp-001-intune-overview-sanitized.png
```

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, device IDs, product IDs, object IDs, serial numbers, and top-right signed-in account details were hidden.

---

## Troubleshooting notes

### Issue: Device showed MDM None

The main troubleshooting issue in this lab was:

```text
MDM: None
```

Meaning:

```text
The device was Microsoft Entra joined, but it was not yet enrolled into Intune MDM.
```

Resolution used:

```text
Manual MDM enrollment from Windows Settings
```

After manual enrollment and sync, the device appeared in Intune as managed.

### Important lesson

Microsoft Entra join and Intune enrollment are related, but they are not the same thing.

Simple comparison:

| State | Meaning |
|---|---|
| Microsoft Entra joined | Device is joined to cloud identity |
| Intune enrolled | Device is managed by Microsoft Intune |
| MDM: None | Device is not currently managed by an MDM provider |
| Managed by Intune | Device can receive Intune policies and app assignments |

### Ownership observation

The device showed as:

```text
Ownership: Personal
```

This was an important result to document because the device was manually enrolled.

For corporate-owned provisioning, Windows Autopilot is the better production method and was tested later in the project.

---

## Enterprise reflection

This lab is useful for understanding the fundamentals of Windows cloud enrollment, but it is not the ideal production method for corporate-owned device deployment.

For real organizations:

| Enrollment method | Best use case |
|---|---|
| Manual Windows enrollment | Small tests, BYOD, troubleshooting, lab validation |
| Windows Autopilot | Corporate-owned device provisioning |
| Bulk provisioning package | Certain shared device or staging scenarios |
| Co-management | Existing Configuration Manager environments moving to cloud management |

The key enterprise lesson is:

```text
A device should not only be joined to Microsoft Entra ID.
It must also be enrolled into Intune to receive management policies.
```

For production corporate Windows devices, Windows Autopilot gives a better lifecycle:

```text
Hardware registration
-> Deployment profile assignment
-> User-driven OOBE
-> Microsoft Entra join
-> Intune enrollment
-> Corporate ownership
-> Apps and policies deployed
```

This OOBE enrollment lab helped create the foundation for understanding the later Autopilot lab.

---

## Security and privacy notes

This is a public learning repository.

Do not upload screenshots that show:

- Full user email addresses
- Tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Hardware hashes
- Internal IP addresses
- MAC addresses
- Passwords
- MFA prompts
- Recovery keys
- Unsanitized device details

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device identifiers
- Serial numbers
- Any private endpoint details

---

## Key learning outcomes

This lab demonstrated:

- How Windows OOBE can be used to connect a device to a work or school account.
- How a Windows device joins Microsoft Entra ID during setup.
- How to check whether a device is also enrolled into Intune.
- What `MDM: None` means during troubleshooting.
- How to trigger manual MDM enrollment from Windows Settings.
- How to verify a Windows device in Microsoft Intune.
- How manual enrollment can result in Personal device ownership.
- Why Windows Autopilot is better for corporate-owned production devices.
- Why endpoint validation and admin portal validation are both important.

---

## Lab conclusion

The Windows OOBE enrollment lab was completed successfully.

Final result:

```text
WIN-CORP-001 completed Microsoft Entra join.
The initial MDM state showed MDM: None.
Manual MDM enrollment was completed from Windows Settings.
WIN-CORP-001 appeared in Microsoft Intune as managed by Intune and compliant.
The device ownership was documented as Personal.
```

This lab established the foundation for later Windows Autopilot, app deployment, configuration profile, and endpoint security testing.
