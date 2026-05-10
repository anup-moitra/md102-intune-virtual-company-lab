# Win32 App Deployment: 7-Zip

This file documents the planned Win32 application deployment lab for 7-Zip using Microsoft Intune.

---

## Status

Planned / documentation template prepared / not yet tested

---

## Objective

Deploy 7-Zip as a **Windows app (Win32)** using Microsoft Intune.

This lab will validate that:

- A Win32 app source folder can be prepared.
- A Win32 installer can be packaged into `.intunewin` format.
- The `.intunewin` package can be uploaded to Intune.
- Install and uninstall commands can be configured.
- Detection rules can verify whether the app is installed.
- The app can be assigned as **Required** to a pilot group.
- A managed Windows device can receive and install the app.
- Installation status can be verified from both Intune and the endpoint.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy applications to managed Windows devices.

This lab continues the application deployment section after Microsoft Store app deployment.

Simple deployment flow:

```text
Download 7-Zip installer
-> Prepare Win32 source folder
-> Package installer as .intunewin
-> Upload Win32 app to Intune
-> Configure commands and detection rule
-> Assign app to pilot users
-> Sync managed Windows device
-> Verify installation
```

---

## Why This Lab Matters

Microsoft Store apps are easy to deploy from Intune, but many real business applications are still delivered as traditional `.exe` or `.msi` installers.

For those apps, Intune commonly uses the **Win32 app** deployment model.

This is important because Win32 deployment gives administrators more control over:

- Installer packaging
- Silent install commands
- Silent uninstall commands
- Detection rules
- Restart behavior
- Requirements
- Return codes
- App installation monitoring

In real environments, this method is used for apps such as:

- 7-Zip
- Adobe Reader
- Google Chrome
- Zoom
- VPN clients
- Security tools
- Line-of-business applications

---

## Important Concept

A Win32 app in Intune is not uploaded directly as a normal `.exe` file.

The installer must first be converted into an Intune package format:

```text
Original installer: 7zip.exe
Packaged installer: 7zip.intunewin
```

Intune then uses the **Intune Management Extension** on the Windows device to process Win32 app installation.

---

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | `user01` |
| Assignment group | `GRP-Pilot-Users` |
| App deployed | 7-Zip |
| App type | Windows app (Win32) |
| Package format | `.intunewin` |
| Assignment type | Required |

---

## Application Details

| Item | Planned value |
|---|---|
| Application | 7-Zip |
| Installer type | EXE |
| Renamed installer | `7zip.exe` |
| Architecture | x64 |
| Publisher | Igor Pavlov |
| Version | Record the version used during the lab |
| Source folder | `C:\IntuneWin32\7zip\Source` |
| Output folder | `C:\IntuneWin32\7zip\Output` |
| Packaged file | `7zip.intunewin` |

> [!NOTE]
> Record the actual 7-Zip version used during the hands-on lab. Do not rely on this template as the final version record until the installer is downloaded and verified.

---

## Required Tools

This lab requires:

- 7-Zip Windows x64 installer
- Microsoft Win32 Content Prep Tool
- Microsoft Intune admin center access
- A managed Windows test device
- A pilot user or pilot device group

---

## Local Folder Plan

Create the following folders on the admin/test machine:

```text
C:\IntuneWin32\7zip\Source
C:\IntuneWin32\7zip\Output
C:\IntuneWin32\Tool
```

Place the renamed installer here:

```text
C:\IntuneWin32\7zip\Source\7zip.exe
```

---

## Package Creation Command

Run the Microsoft Win32 Content Prep Tool from the folder where `IntuneWinAppUtil.exe` is stored.

Example command:

```cmd
IntuneWinAppUtil.exe -c "C:\IntuneWin32\7zip\Source" -s "7zip.exe" -o "C:\IntuneWin32\7zip\Output" -q
```

Expected output:

```text
C:\IntuneWin32\7zip\Output\7zip.intunewin
```

---

## Intune App Configuration

### App Type

In Intune, create a new Windows app using:

```text
App type: Windows app (Win32)
```

Upload:

```text
7zip.intunewin
```

---

## App Information

| Setting | Planned value |
|---|---|
| Name | `7-Zip` |
| Description | `Deploys 7-Zip as a Win32 app for the MD-102 Intune lab.` |
| Publisher | `Igor Pavlov` |
| Category | Productivity or Utilities |
| Information URL | Optional |
| Privacy URL | Optional |
| Developer | Optional |
| Owner | IT Admin |
| Notes | `Win32 app deployment test for MD-102 Intune lab.` |
| Logo | Optional / leave blank for first test |

---

## Program Settings

| Setting | Value |
|---|---|
| Install command | `7zip.exe /S` |
| Uninstall command | `"C:\Program Files\7-Zip\Uninstall.exe" /S` |
| Install behavior | System |
| Device restart behavior | No specific action |

> [!NOTE]
> The `/S` silent install switch is case-sensitive for the 7-Zip installer.

---

## Requirements

| Setting | Planned value |
|---|---|
| Operating system architecture | 64-bit |
| Minimum operating system | Windows 10 1607 or later / Windows 11 |
| Disk space required | Not configured |
| Physical memory required | Not configured |
| Minimum number of logical processors | Not configured |
| Minimum CPU speed | Not configured |

---

## Detection Rule

Detection rules tell Intune how to confirm that the app is installed.

Use a file-based detection rule.

| Setting | Value |
|---|---|
| Rule type | File |
| Path | `C:\Program Files\7-Zip` |
| File or folder | `7zFM.exe` |
| Detection method | File or folder exists |
| Associated with a 32-bit app on 64-bit clients | No |

Expected detection path:

```text
C:\Program Files\7-Zip\7zFM.exe
```

---

## Assignments

Assign the app as:

```text
Required
```

Target group:

```text
GRP-Pilot-Users
```

Reason:

```text
user01 is a member of GRP-Pilot-Users and signs in to WIN-CORP-001 for app deployment testing.
```

---

## Steps to Perform

### Step 1: Download 7-Zip Installer

Download the Windows x64 7-Zip EXE installer.

Rename the installer to:

```text
7zip.exe
```

Place it in:

```text
C:\IntuneWin32\7zip\Source
```

### Step 2: Download Win32 Content Prep Tool

Download and extract the Microsoft Win32 Content Prep Tool.

Place `IntuneWinAppUtil.exe` in:

```text
C:\IntuneWin32\Tool
```

### Step 3: Create the `.intunewin` Package

Run:

```cmd
IntuneWinAppUtil.exe -c "C:\IntuneWin32\7zip\Source" -s "7zip.exe" -o "C:\IntuneWin32\7zip\Output" -q
```

Confirm this file is created:

```text
C:\IntuneWin32\7zip\Output\7zip.intunewin
```

### Step 4: Create Win32 App in Intune

Go to:

```text
Intune admin center
→ Apps
→ Windows
→ Windows apps
→ Create
```

Select:

```text
Windows app (Win32)
```

Upload:

```text
7zip.intunewin
```

### Step 5: Configure App Information

Configure the app information using the values in the **App Information** section.

### Step 6: Configure Program Commands

Configure:

```text
Install command: 7zip.exe /S
Uninstall command: "C:\Program Files\7-Zip\Uninstall.exe" /S
Install behavior: System
```

### Step 7: Configure Requirements

Set operating system architecture to:

```text
64-bit
```

Set the minimum operating system appropriate for Windows 10/11 devices.

### Step 8: Configure Detection Rule

Use the file detection rule:

```text
C:\Program Files\7-Zip\7zFM.exe
```

### Step 9: Assign the App

Assign as:

```text
Required
```

To:

```text
GRP-Pilot-Users
```

### Step 10: Review and Create

Review:

- App name
- Install command
- Uninstall command
- Detection rule
- Assignment group

Then select:

```text
Create
```

### Step 11: Sync the Test Device

On `WIN-CORP-001`, go to:

```text
Settings
→ Accounts
→ Access work or school
→ Connected work/school account
→ Info
→ Sync
```

### Step 12: Verify Installation on Device

On `WIN-CORP-001`, check:

```text
Start menu → 7-Zip File Manager
```

Also verify the file exists:

```text
C:\Program Files\7-Zip\7zFM.exe
```

### Step 13: Verify Install Status in Intune

Go to:

```text
Intune admin center
→ Apps
→ Windows
→ 7-Zip
→ Monitor
→ Device install status
```

Expected result:

```text
WIN-CORP-001 = Installed / Success
```

---

## Test Result

| Test item | Result |
|---|---|
| 7-Zip installer downloaded | Pending |
| Installer renamed to `7zip.exe` | Pending |
| Source folder prepared | Pending |
| Win32 Content Prep Tool downloaded | Pending |
| `.intunewin` package created | Pending |
| Win32 app uploaded to Intune | Pending |
| App information configured | Pending |
| Install command configured | Pending |
| Uninstall command configured | Pending |
| Requirements configured | Pending |
| Detection rule configured | Pending |
| App assigned as Required | Pending |
| Device sync triggered | Pending |
| 7-Zip installed on `WIN-CORP-001` | Pending |
| Intune install status verified | Pending |
| Final lab result | Pending |

---

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/application-deployment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `7zip-source-folder-sanitized.png` | Pending | Show `7zip.exe` in the source folder |
| `7zip-intunewin-created-sanitized.png` | Pending | Show `7zip.intunewin` in the output folder |
| `7zip-win32-app-upload-sanitized.png` | Pending | Show Win32 app upload screen after selecting `.intunewin` |
| `7zip-app-information-sanitized.png` | Pending | Show app information page |
| `7zip-program-settings-sanitized.png` | Pending | Show install and uninstall commands |
| `7zip-requirements-sanitized.png` | Pending | Show architecture and minimum OS requirements |
| `7zip-detection-rule-sanitized.png` | Pending | Show file detection rule |
| `7zip-required-assignment-sanitized.png` | Pending | Show Required assignment to `GRP-Pilot-Users` |
| `7zip-review-create-sanitized.png` | Pending | Show final review page before creation |
| `device-sync-after-7zip-assignment-sanitized.png` | Pending | Show Windows device sync after assignment |
| `7zip-installed-on-device-sanitized.png` | Pending | Show 7-Zip installed or opened on the endpoint |
| `7zip-device-install-status-sanitized.png` | Pending | Show Intune device install status |

> [!IMPORTANT]
> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.

---

## Future Screenshot Links

After screenshots are uploaded, add image links in this section.

Example format:

```markdown
![7-Zip detection rule](../screenshots/sanitized/application-deployment/7zip-detection-rule-sanitized.png)
```

---

## Troubleshooting Notes

If the app does not install:

1. Confirm the app is assigned as **Required**.
2. Confirm `user01` is a member of `GRP-Pilot-Users`.
3. Confirm `WIN-CORP-001` is enrolled and checking in to Intune.
4. Trigger a manual sync from Windows settings.
5. Wait for Intune Management Extension processing.
6. Confirm the install command is correct:

   ```cmd
   7zip.exe /S
   ```

7. Confirm the detection rule points to the correct file:

   ```text
   C:\Program Files\7-Zip\7zFM.exe
   ```

8. Review Intune app install status.
9. Check local installation path on the device.
10. Restart the device if needed.

If the app installs but Intune still reports failure:

1. Check whether `7zFM.exe` exists in the configured detection path.
2. Confirm the detection rule uses the correct file name.
3. Confirm the app installed to `C:\Program Files\7-Zip` and not a different path.
4. Review Intune Management Extension logs if needed.

Common log location:

```text
C:\ProgramData\Microsoft\IntuneManagementExtension\Logs\IntuneManagementExtension.log
```

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Real tenant IDs
- Full real email addresses
- Passwords
- MFA QR codes
- Device serial numbers
- Device IDs
- Object IDs
- Internal IP addresses
- Unsanitized screenshots
- Production company data

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs
- Object IDs
- Any sensitive identifiers

---

## Current Status

| Task | Status |
|---|---|
| Win32 7-Zip lab documentation created | Completed |
| 7-Zip installer prepared | Pending |
| `.intunewin` package created | Pending |
| Win32 app created in Intune | Pending |
| App assigned to pilot group | Pending |
| Endpoint installation verified | Pending |
| Screenshots uploaded | Pending |
| Documentation updated with final evidence | Pending |

---

## Next Step

Prepare the 7-Zip installer and Win32 package:

```text
1. Download 7-Zip x64 EXE installer
2. Rename it to 7zip.exe
3. Place it in C:\IntuneWin32\7zip\Source
4. Run IntuneWinAppUtil.exe
5. Confirm 7zip.intunewin is created
```

Then capture:

```text
7zip-source-folder-sanitized.png
7zip-intunewin-created-sanitized.png
```
