# Windows OOBE Enrollment

This file documents the first corporate Windows device enrollment using Windows Out-of-Box Experience and Microsoft Intune.

## Objective

Enroll a corporate Windows 11 device into Microsoft Intune by signing in with a Microsoft Entra ID work account during Windows OOBE.

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The goal is to prove that a corporate Windows device can be:

- Joined to Microsoft Entra ID
- Enrolled into Microsoft Intune
- Managed as a corporate device
- Evaluated by compliance policy

## Device Details

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Physical laptop |
| Manufacturer | Lenovo |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows OOBE work or school setup |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Result | Successfully enrolled |

## Prerequisites

Before starting this lab, the following were completed:

- Microsoft Intune tenant verified
- Microsoft Entra users created
- Intune license assigned to user01
- Automatic MDM enrollment configured
- Windows device reset/reinstalled and ready for OOBE

## Steps Performed

1. Started Windows 11 OOBE on the physical laptop.
2. Selected region and keyboard settings.
3. Connected the device to the internet.
4. Selected work or school account setup.
5. Signed in as user01.
6. Completed authentication prompts.
7. Allowed Windows setup to complete.
8. Confirmed device appeared in Intune.
9. Confirmed device was Microsoft Entra joined.
10. Confirmed the device was managed by Intune.

## Test Result

| Test Item | Result |
|---|---|
| Device completed OOBE | Successful |
| User signed in with work account | Successful |
| Device joined Microsoft Entra ID | Successful |
| Device enrolled into Intune | Successful |
| Device appeared in Windows devices | Successful |
| Primary user showed as user01 | Successful |
| Final result | Successful |

## What This Proves

This lab proves the basic modern Windows corporate enrollment flow:

```text
Windows OOBE
→ User signs in with Microsoft Entra ID account
→ Device joins Microsoft Entra ID
→ Automatic MDM enrollment sends device to Intune
→ Device becomes managed
```

## Screenshots

Suggested folder:

```text
screenshots/sanitized/device-enrollment/
```

Suggested screenshots:

```text
win-corp-001-intune-overview-sanitized.jpg
win-corp-001-access-work-school-sanitized.jpg
win-corp-001-entra-joined-sanitized.jpg
```

## Security Notes

Hide tenant names, full email addresses, device IDs, serial numbers, object IDs, and any sensitive account details before uploading screenshots.

## Current Lab Status

Completed:

- WIN-CORP-001 enrolled through Windows OOBE
- Device appears in Intune
- Device is Microsoft Entra joined
- Device is managed by Intune
- Device later reported compliant

Pending:

- Add sanitized screenshots as available
