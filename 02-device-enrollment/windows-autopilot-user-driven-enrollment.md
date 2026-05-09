# Windows Autopilot User-Driven Enrollment

This file documents the Windows Autopilot user-driven enrollment lab for the MD-102 Intune virtual company project.

## Objective

The objective of this lab is to register a Windows device with Windows Autopilot and use a user-driven Autopilot deployment profile to enroll the device into Microsoft Intune.

This lab validates that:

- A Windows device can be manually registered with Windows Autopilot using a hardware hash CSV.
- A Windows Autopilot deployment profile can be created and assigned.
- The device can receive the assigned Autopilot profile.
- User 01 can sign in during Windows OOBE.
- The device can join Microsoft Entra ID and enroll into Microsoft Intune.
- The Autopilot-enrolled device can later receive apps and policies from Intune.

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company uses Microsoft Entra ID and Microsoft Intune to manage corporate Windows devices.

This Autopilot lab builds on the earlier completed work:

| Requirement | Status |
|---|---|
| Microsoft Intune tenant available | Completed |
| Microsoft Entra ID users created | Completed |
| Intune licenses assigned | Completed |
| Microsoft 365 Business Premium trial activated | Completed |
| User 01 licensed for Intune and Microsoft 365 Apps | Completed |
| Autopilot test device available | Completed |
| Autopilot device group created | Completed |

## Important Concept

Windows Autopilot is used to set up and configure Windows devices during the out-of-box experience, also known as OOBE.

In a traditional setup, an IT admin may manually configure Windows, join the device, install apps, and apply settings.

With Autopilot, the device can contact Microsoft cloud services during OOBE and receive the correct organization setup automatically.

Simple flow:

```text
Device starts at Windows OOBE
→ Device connects to the internet
→ Device checks for Autopilot registration
→ Assigned Autopilot profile is downloaded
→ User signs in with Microsoft Entra ID account
→ Device joins Microsoft Entra ID
→ Device enrolls into Intune
→ Intune applies policies and apps
```

## Lab Design

This lab uses a user-driven Autopilot deployment.

| Item | Value |
|---|---|
| Autopilot deployment type | User-driven |
| Join type | Microsoft Entra joined |
| Device ownership | Corporate |
| Enrollment platform | Windows 11 |
| Test user | User 01 |
| User sign-in account | user01@anupmoitra.onmicrosoft.com |
| Autopilot group | GRP-Autopilot-Devices |
| Deployment profile | AP WIN User Driven Entra Join |
| Microsoft 365 Apps deployment | Created separately in Intune |

## Autopilot Device Group

A security group was created for Autopilot devices.

| Setting | Value |
|---|---|
| Group name | GRP-Autopilot-Devices |
| Group type | Security |
| Membership type | Assigned |
| Purpose | Contains Windows devices registered for Autopilot deployment in the MD-102 lab |

This group was used to assign the Autopilot deployment profile.

## Autopilot Deployment Profile

The following Windows Autopilot deployment profile was created.

| Setting | Value |
|---|---|
| Profile name | AP WIN User Driven Entra Join |
| Platform | Windows PC |
| Deployment mode | User-driven |
| Join to Microsoft Entra ID as | Microsoft Entra joined |
| User account type | Standard |
| Microsoft Software License Terms | Hide |
| Privacy settings | Hide |
| Hide change account options | Hide |
| Allow pre-provisioned deployment | No |
| Language / region | Operating system default |
| Automatically configure keyboard | Yes |
| Apply device name template | No |
| Assigned group | GRP-Autopilot-Devices |

## Device Naming Note

For this first Autopilot lab, the device name template was not enabled.

Because of this, Windows may assign a default device name during setup.

Future improvement:

```text
Enable Autopilot device name template
Example template: WINAP%RAND:5%
```

This can create cleaner device names such as:

```text
WINAP12345
```

## Hardware Hash Collection

The Autopilot test laptop was already at the Windows OOBE screen.

To collect the hardware hash, Command Prompt was opened from OOBE using:

```text
Shift + F10
```

PowerShell was started from Command Prompt:

```powershell
powershell
```

The following commands were used to collect the hardware hash:

```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned -Force
Install-Script -Name Get-WindowsAutopilotInfo -Force
Get-WindowsAutopilotInfo -OutputFile C:\AutopilotHWID.csv
```

The CSV file was saved as:

```text
C:\AutopilotHWID.csv
```

The file was copied to a USB drive and imported into Intune.

## Autopilot Device Import

The hardware hash CSV was imported into Intune from:

```text
Intune admin center
→ Devices
→ Windows
→ Windows enrollment
→ Windows Autopilot
→ Devices
→ Import
```

Imported CSV file:

```text
AutopilotHWID.csv
```

After import, the device appeared in the Autopilot devices list.

| Item | Result |
|---|---|
| Hardware hash imported | Successful |
| Device manufacturer | Lenovo |
| Device appeared in Autopilot devices | Yes |
| Initial profile status | Not assigned |
| Later profile status | Assigned |

## Profile Assignment

After the device was imported, it was added to:

```text
GRP-Autopilot-Devices
```

The Autopilot profile assignment then changed from:

```text
Not assigned
```

to:

```text
Pending
```

and finally to:

```text
Assigned
```

This confirmed that the Autopilot deployment profile was assigned successfully.

## Microsoft 365 Apps Deployment Connection

Before restarting the OOBE device, a Microsoft 365 Apps deployment was created separately in Intune.

The reason for this was to test a realistic Autopilot flow where the device enrolls and then receives required business apps.

App deployment details are documented separately in:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

Simple relationship:

```text
Autopilot profile = controls device setup and enrollment
Intune app deployment = installs required apps after enrollment
Enrollment Status Page = can show app and policy setup progress
```

## Autopilot OOBE Test

After the profile showed as assigned, the OOBE laptop was restarted.

Command used from OOBE Command Prompt:

```cmd
shutdown /r /t 0
```

After restart, the device connected to the internet and began the Autopilot setup experience.

The user signed in using:

```text
user01@anupmoitra.onmicrosoft.com
```

## Expected Result

The expected result of this lab is:

```text
User 01 signs in during OOBE
→ Device receives Autopilot profile
→ Device joins Microsoft Entra ID
→ Device enrolls into Microsoft Intune
→ Device appears in Intune Windows devices
→ Assigned policies and apps begin applying
```

## Verification Steps

After the device reaches the Windows desktop, verify the following.

### Check Windows work or school connection

On the Autopilot device:

```text
Settings
→ Accounts
→ Access work or school
```

Expected result:

```text
Connected to the organization
Managed by Microsoft Intune
```

### Check Microsoft Entra join status

Run this command:

```cmd
dsregcmd /status
```

Expected values:

```text
AzureAdJoined: YES
DomainJoined: NO
```

### Check Intune device record

In Intune admin center:

```text
Devices
→ Windows devices
```

Expected values:

| Field | Expected result |
|---|---|
| Managed by | Intune |
| Join type | Microsoft Entra joined |
| Ownership | Corporate |
| Primary user | User 01 |
| Compliance | Depends on policy evaluation |

### Check app deployment later

Microsoft 365 Apps deployment should be reviewed from:

```text
Apps
→ All apps
→ Microsoft 365 Apps for Windows - Autopilot Lab
→ Monitor
→ Device install status
```

## Test Result

| Test item | Result |
|---|---|
| Autopilot device group created | Successful |
| Autopilot deployment profile created | Successful |
| Hardware hash collected | Successful |
| Hardware hash imported | Successful |
| Device added to Autopilot device group | Successful |
| Autopilot profile assigned | Successful |
| OOBE sign-in with User 01 | In progress / to be verified |
| Device Entra joined | To be verified |
| Device enrolled into Intune | To be verified |
| Microsoft 365 Apps deployment | Created separately / install to be verified |

## Screenshots

The following screenshots should be added after sanitizing sensitive information.

> [!NOTE]
> Screenshots must be sanitized before upload. Hide tenant names, full email addresses, IP addresses, device IDs, object IDs, serial numbers, hardware hashes, and any sensitive details.

### Autopilot deployment profile list

![Autopilot deployment profile list](../screenshots/sanitized/device-enrollment/autopilot-profile-list-sanitized.jpg)

### Autopilot deployment profile settings

![Autopilot deployment profile settings](../screenshots/sanitized/device-enrollment/autopilot-profile-settings-sanitized.jpg)

### Autopilot device import successful

![Autopilot device import successful](../screenshots/sanitized/device-enrollment/autopilot-device-import-sanitized.jpg)

### Autopilot profile assigned

![Autopilot profile assigned](../screenshots/sanitized/device-enrollment/autopilot-profile-assigned-sanitized.jpg)

### Autopilot OOBE sign-in

![Autopilot OOBE sign-in](../screenshots/sanitized/device-enrollment/autopilot-oobe-signin-sanitized.jpg)

### Intune Windows device record

![Autopilot Intune device record](../screenshots/sanitized/device-enrollment/autopilot-intune-device-record-sanitized.jpg)

## Screenshot Folder Path

Screenshots for this lab should be stored in:

```text
screenshots/sanitized/device-enrollment/
```

Suggested screenshot filenames:

```text
autopilot-profile-list-sanitized.jpg
autopilot-profile-settings-sanitized.jpg
autopilot-device-import-sanitized.jpg
autopilot-profile-assigned-sanitized.jpg
autopilot-oobe-signin-sanitized.jpg
autopilot-intune-device-record-sanitized.jpg
```

## Troubleshooting Notes

### Profile status shows Not assigned

If the imported Autopilot device shows `Not assigned`, check that:

1. The device is added to the correct Autopilot device group.
2. The Autopilot deployment profile is assigned to that group.
3. Autopilot devices have been synced.
4. Enough time has passed for assignment processing.

### Profile status shows Pending

`Pending` usually means the assignment is processing.

Recommended action:

```text
Wait 5–15 minutes
Click Sync
Refresh the Autopilot devices page
```

### Device does not show Autopilot experience during OOBE

Check that:

1. The device is connected to the internet during OOBE.
2. The Autopilot profile status is `Assigned` before restarting the device.
3. The hardware hash was imported successfully.
4. The device was not accidentally set up before the Autopilot profile was assigned.

### Device name is not custom

This is expected in this lab because device name template was disabled.

Future improvement:

```text
Enable device name template in Autopilot profile
Use: WINAP%RAND:5%
```

## Security and Privacy Notes

This is a public learning repository.

Do not upload sensitive information, including:

- Full real email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Unsanitized screenshots

## Current Lab Status

Completed:

- Microsoft 365 Business Premium trial activated
- User 01 licensed for Intune and Microsoft 365 Apps
- Autopilot device group created
- Autopilot deployment profile created
- Hardware hash collected from OOBE device
- Autopilot device imported into Intune
- Autopilot device added to GRP-Autopilot-Devices
- Autopilot profile assigned successfully
- Microsoft 365 Apps deployment created separately for Autopilot app testing

Pending:

- Complete OOBE sign-in as User 01
- Confirm device appears in Intune Windows devices
- Confirm Microsoft Entra join status
- Confirm Microsoft Intune enrollment status
- Confirm Microsoft 365 Apps installation and sign-in
- Add sanitized screenshots

## Next Step

The next step is to complete the OOBE sign-in with User 01 and verify the device in Intune.

After enrollment is confirmed, continue to the Microsoft 365 Apps deployment validation documented in:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```
