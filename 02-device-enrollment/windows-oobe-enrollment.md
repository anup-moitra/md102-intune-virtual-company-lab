# Windows OOBE Enrollment

This file documents the first corporate Windows device enrollment using Windows Out-of-Box Experience, Microsoft Entra ID, and Microsoft Intune.

---

## Objective

Enroll a Windows 11 device by signing in with a Microsoft Entra ID work account during Windows Out-of-Box Experience and then completing Microsoft Intune enrollment.

This lab validates that:

- A Windows device can be set up for work or school during OOBE.
- The device can be named using a consistent lab naming standard.
- The device can join Microsoft Entra ID.
- The device can appear in the Microsoft Entra admin center.
- The device can be enrolled into Microsoft Intune.
- The device can appear in the Intune admin center as a managed Windows device.
- Intune enrollment can be troubleshot if MDM enrollment does not complete automatically.

---

## Why This Lab Matters

Windows OOBE enrollment is one of the most important modern Windows enrollment methods.

In a real company, a user can receive a new or reset Windows device, connect it to the internet, sign in with a work account, and allow the device to become cloud managed.

Expected full flow:

```text
Windows OOBE
-> User signs in with Microsoft Entra ID account
-> Device joins Microsoft Entra ID
-> Automatic MDM enrollment enrolls the device into Intune
-> Device becomes managed
```

In this lab, the device successfully joined Microsoft Entra ID first. The MDM status initially showed as `None`, so manual MDM enrollment troubleshooting was performed. After running the manual enrollment trigger, the device appeared in Microsoft Intune.

---

## Lab Environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Device type | Laptop |
| Ownership | Personal in Intune |
| Operating system | Windows 11 |
| Enrollment method | Windows OOBE work or school setup + manual MDM enrollment trigger |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Assignment group | GRP-Pilot-Users |
| Current status | Completed |

> [!NOTE]
> The device was intended to simulate a corporate Windows endpoint. After manual MDM enrollment, Intune showed the ownership value as `Personal`. This is documented as an observed result for this lab.

---

## Prerequisites

Before starting this lab, the following was completed:

- Microsoft Entra ID lab users created.
- Microsoft Entra ID security groups created.
- user01 created and available for testing.
- user01 added to GRP-Pilot-Users.
- user01 assigned an Intune-capable license.
- Windows test device reset or ready for OOBE.
- Device connected to the internet during setup.

The following settings were checked or used during troubleshooting:

- Automatic MDM enrollment scope.
- user01 license assignment.
- Microsoft Entra device record.
- Manual MDM enrollment trigger.

---

## Important Notes

This lab is not Windows Autopilot.

This lab uses the basic Windows OOBE work or school setup flow.

Windows Autopilot will be documented separately in:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

---

## Device Naming

The lab device is documented as:

```text
WIN-CORP-001
```

During Windows setup, the OOBE device name option appeared and the device name was set to:

```text
WIN-CORP-001
```

This keeps the local device name, Entra device record, Intune record, screenshots, and GitHub documentation consistent.

---

## Steps Performed

### Step 1: Prepared the Windows Device

The spare Windows device was reimaged and started from Windows Out-of-Box Experience.

The OOBE setup flow displayed the initial setup screens, including:

```text
Region selection
Device name
Work or school setup
Microsoft work account sign-in
```

---

### Step 2: Selected Region

The country or region screen was displayed.

Selected region:

```text
India
```

---

### Step 3: Named the Device During OOBE

Windows setup displayed the device naming screen.

The device name was set to:

```text
WIN-CORP-001
```

---

### Step 4: Selected Work or School Setup

During Windows setup, the following option was selected:

```text
Set up for work or school
```

The personal setup option was not selected.

---

### Step 5: Signed In as user01

The Microsoft work or school sign-in screen was displayed.

Signed in using the lab user account:

```text
user01
```

The full user principal name was used during sign-in, but it was hidden in public screenshots.

---

### Step 6: Completed Authentication Prompts

Windows Hello and MFA/security setup prompts appeared during first sign-in.

Authentication setup was completed or skipped where appropriate.

No MFA QR codes, verification codes, passwords, or PIN setup screens were uploaded to GitHub.

---

### Step 7: Reached Windows Desktop

Windows setup completed and the device reached the desktop.

The local Windows device name was confirmed as:

```text
WIN-CORP-001
```

---

### Step 8: Verified Work or School Connection Locally

On the Windows device, the following page was checked:

```text
Settings
-> Accounts
-> Access work or school
```

The device showed a connected work or school account.

This confirmed that the device was connected to the lab Microsoft Entra ID tenant.

---

### Step 9: Verified Device in Microsoft Entra Admin Center

The device appeared in Microsoft Entra admin center under:

```text
Entra admin center
-> Devices
-> All devices
```

The device was listed as:

```text
WIN-CORP-001
```

The Microsoft Entra device record initially showed:

```text
Join type: Microsoft Entra joined
MDM: None
```

This confirmed that Microsoft Entra join completed successfully, but Intune MDM enrollment did not complete automatically at first.

---

### Step 10: Triggered Manual MDM Enrollment

Manual MDM enrollment was triggered from the Windows device using:

```cmd
start ms-device-enrollment:?mode=mdm
```

After completing the enrollment prompt and waiting for check-in, the device appeared in the Intune admin center.

---

### Step 11: Verified Device in Microsoft Intune

The device appeared in Intune under:

```text
Intune admin center
-> Devices
-> Windows
-> Windows devices
```

The Intune device list showed:

```text
Device name: WIN-CORP-001
Managed by: Intune
Compliance: Compliant
OS: Windows
Primary user: user01
```

The observed ownership value in Intune was:

```text
Personal
```

---

## Expected Result

Expected full result:

- WIN-CORP-001 completes Windows OOBE.
- WIN-CORP-001 uses the planned lab device name.
- user01 signs in with a work account.
- The device joins Microsoft Entra ID.
- The device enrolls into Microsoft Intune.
- The device appears under Windows devices in Intune.
- The device is ready for compliance, app deployment, and configuration profile testing.

Observed result:

- WIN-CORP-001 completed Windows OOBE.
- The device name was configured successfully.
- user01 signed in successfully.
- The device joined Microsoft Entra ID.
- The device initially showed `MDM: None` in Microsoft Entra ID.
- Manual MDM enrollment was triggered.
- The device appeared in Intune.
- The device showed as managed by Intune.
- The device showed as compliant.
- Intune displayed the ownership value as `Personal`.

---

## Test Result

| Test Item | Result |
|---|---|
| Windows OOBE started | Completed |
| Region selected | Completed |
| Device name set to WIN-CORP-001 | Completed |
| Work or school setup selected | Completed |
| user01 signed in successfully | Completed |
| Windows Hello/MFA prompts completed | Completed |
| Device reached Windows desktop | Completed |
| Device joined Microsoft Entra ID | Completed |
| Device visible in Microsoft Entra admin center | Completed |
| Initial MDM status checked | Completed |
| Manual MDM enrollment triggered | Completed |
| Device enrolled into Intune | Completed |
| Device visible in Intune | Completed |
| Device compliance shown in Intune | Completed |
| Final lab result | Completed |

---

## Screenshots

Screenshots are stored in:

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

> [!NOTE]
> Screenshots were sanitized before upload. Tenant names, full email addresses, device IDs, product IDs, object IDs, serial numbers, and top-right signed-in account details were hidden.

---

## Screenshot Files

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

---

## Troubleshooting Notes

### Issue Encountered

The device appeared in Microsoft Entra admin center, but the MDM column initially showed:

```text
None
```

This meant the device was Microsoft Entra joined, but not enrolled into Intune MDM yet.

### Troubleshooting Performed

Manual MDM enrollment was triggered from the Windows device using:

```cmd
start ms-device-enrollment:?mode=mdm
```

After the enrollment process completed and the device checked in, it appeared in Microsoft Intune.

### Result After Troubleshooting

The device appeared in:

```text
Intune admin center
-> Devices
-> Windows
-> Windows devices
```

The Intune record showed:

```text
Managed by: Intune
Compliance: Compliant
Primary user: user01
```

### Ownership Observation

The device ownership value appeared as:

```text
Personal
```

This was noted because the device was manually enrolled after the initial OOBE/Entra join process. Future corporate ownership behavior will be compared with Windows Autopilot enrollment.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Full real email addresses
- Real tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Autopilot hardware hashes
- BitLocker recovery keys
- Passwords
- MFA QR codes
- Internal IP addresses
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Device IDs
- Object IDs
- Serial numbers
- Product IDs
- Any recovery keys, tokens, or QR codes

---

## Current Status

| Task | Status |
|---|---|
| windows-oobe-enrollment.md created | Completed |
| Windows device prepared for OOBE | Completed |
| Device name configured as WIN-CORP-001 | Completed |
| Work or school setup selected | Completed |
| user01 sign-in completed | Completed |
| Microsoft Entra join verified | Completed |
| Initial MDM issue documented | Completed |
| Manual MDM enrollment completed | Completed |
| Intune enrollment verified | Completed |
| Intune screenshots added | Completed |
| OOBE screenshots added | Completed |

---

## Next Step

Continue to the next device enrollment lab:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

This next lab will compare the manual OOBE enrollment experience with Windows Autopilot user-driven enrollment.
