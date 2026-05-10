# Win32 App Deployment: 7-Zip

This file documents Win32 application deployment using Microsoft Intune for the MD-102 Intune virtual company lab.

---

## Objective

Deploy 7-Zip as a **Windows app (Win32)** using Microsoft Intune.

This lab validates that:

- A Win32 app source folder can be prepared.
- A Win32 installer can be packaged into `.intunewin` format.
- The `.intunewin` package can be uploaded to Intune.
- Install and uninstall commands can be configured.
- Detection rules can verify whether the app is installed.
- The app can be assigned as **Required** to a pilot group.
- A managed Windows device can receive and install the app.
- Installation status can be verified from Intune.
- Local installation can be verified on the endpoint.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy applications to managed Windows devices.

This lab continues the application deployment section after Microsoft Store app deployment. Microsoft Store apps are simpler because they are selected directly from the Store app catalog. Win32 apps require an extra packaging step before they can be uploaded to Intune.

Simple deployment flow:

```text
Download 7-Zip installer
-> Prepare Win32 source folder
-> Package installer as .intunewin
-> Upload Win32 app to Intune
-> Configure commands and detection rule
-> Assign app to pilot users
-> Sync managed Windows device
-> Verify installation status
-> Confirm the app is available on the endpoint
```

---

## Why This Lab Matters

Many real business applications are still delivered as traditional `.exe` or `.msi` installers.

For those apps, Intune commonly uses the **Win32 app** deployment model.

This is important because Win32 deployment gives administrators control over:

- Installer packaging
- Silent install commands
- Silent uninstall commands
- Detection rules
- Restart behavior
- Requirements
- Return codes
- App installation monitoring

In real environments, this method is commonly used for apps such as:

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

The installer must first be converted into Intune's package format:

```text
Original installer: 7zip.exe
Packaged installer: 7zip.intunewin
```

Intune then uses the **Intune Management Extension** on the Windows device to process Win32 app installation.

---

## Lab Environment

| Item | Value |
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

| Item | Value |
|---|---|
| Application | 7-Zip |
| Installer type | EXE |
| Renamed installer | `7zip.exe` |
| Architecture | x64 |
| Publisher | Igor Pavlov |
| Version | 26.01 |
| Source folder | `C:\IntuneWin32\7zip\Source` |
| Output folder | `C:\IntuneWin32\7zip\Output` |
| Packaged file | `7zip.intunewin` |

---

## Required Tools

This lab used:

- 7-Zip Windows x64 installer
- Microsoft Win32 Content Prep Tool
- Microsoft Intune admin center
- Managed Windows test device
- Pilot user group for assignment

---

## Local Folder Structure

The following local folders were used on the admin/test machine:

```text
C:\IntuneWin32\7zip\Source
C:\IntuneWin32\7zip\Output
C:\IntuneWin32\Tool
```

The 7-Zip installer was renamed to:

```text
7zip.exe
```

and placed in:

```text
C:\IntuneWin32\7zip\Source\7zip.exe
```

---

## Package Creation Command

The Microsoft Win32 Content Prep Tool was used to create the `.intunewin` package.

Command used:

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

In Intune, a new Windows app was created using:

```text
App type: Windows app (Win32)
```

Uploaded package:

```text
7zip.intunewin
```

---

## App Information

| Setting | Value |
|---|---|
| Name | `7-Zip` |
| Description | `Deploys 7-Zip as a Win32 app for the MD-102 Intune lab.` |
| Publisher | `Igor Pavlov` |
| Category | Productivity or Utilities |
| Owner | IT Admin |
| Notes | Win32 app deployment test for MD-102 Intune lab |
| Logo | Not configured |

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

| Setting | Value |
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

A file-based detection rule was used.

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

The app was assigned as:

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

## Steps Performed

### Step 1: Downloaded 7-Zip Installer

The Windows x64 7-Zip EXE installer was downloaded.

The installer was renamed to:

```text
7zip.exe
```

The renamed installer was placed in:

```text
C:\IntuneWin32\7zip\Source
```

### Step 2: Downloaded Win32 Content Prep Tool

The Microsoft Win32 Content Prep Tool was downloaded and extracted.

The tool used was:

```text
IntuneWinAppUtil.exe
```

### Step 3: Created the `.intunewin` Package

The following command was used:

```cmd
IntuneWinAppUtil.exe -c "C:\IntuneWin32\7zip\Source" -s "7zip.exe" -o "C:\IntuneWin32\7zip\Output" -q
```

The output package was created successfully:

```text
7zip.intunewin
```

### Step 4: Created Win32 App in Intune

Navigation used:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
-> Create
```

Selected app type:

```text
Windows app (Win32)
```

Uploaded package:

```text
7zip.intunewin
```

### Step 5: Configured App Information

The app information was configured with:

```text
Name: 7-Zip
Publisher: Igor Pavlov
Owner: IT Admin
```

### Step 6: Configured Program Commands

Program settings were configured as:

```text
Install command: 7zip.exe /S
Uninstall command: "C:\Program Files\7-Zip\Uninstall.exe" /S
Install behavior: System
Device restart behavior: No specific action
```

### Step 7: Configured Requirements

Requirements were configured for 64-bit Windows devices.

### Step 8: Configured Detection Rule

A file detection rule was configured for:

```text
C:\Program Files\7-Zip\7zFM.exe
```

### Step 9: Configured Dependencies and Supersedence

No dependencies were configured.

No supersedence relationship was configured.

This was a first-time deployment, so there was no older app version to replace.

### Step 10: Assigned the App

The app was assigned as **Required** to:

```text
GRP-Pilot-Users
```

### Step 11: Created the App

The Win32 app was created in Intune.

### Step 12: Verified Install Status in Intune

The install status was checked from:

```text
Intune admin center
-> Apps
-> Windows
-> 7-Zip
-> Monitor
-> Device install status
```

The install status screenshot was captured for documentation.

### Step 13: Verified 7-Zip on the Endpoint

On `WIN-CORP-001`, 7-Zip was verified locally by checking that the app was installed and available from the Start menu.

The expected file path was also validated:

```text
C:\Program Files\7-Zip\7zFM.exe
```

---

## Test Result

| Test item | Result |
|---|---|
| 7-Zip installer downloaded | Completed |
| Installer renamed to `7zip.exe` | Completed |
| Source folder prepared | Completed |
| Win32 Content Prep Tool downloaded | Completed |
| `.intunewin` package created | Completed |
| Win32 app uploaded to Intune | Completed |
| App information configured | Completed |
| Install command configured | Completed |
| Uninstall command configured | Completed |
| Requirements configured | Completed |
| Detection rule configured | Completed |
| Dependencies configured | Not required |
| Supersedence configured | Not required |
| App assigned as Required | Completed |
| Device install status reviewed | Completed |
| 7-Zip local installation verified on `WIN-CORP-001` | Completed |
| Final lab result | Completed |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/application-deployment/
```

### 7-Zip source folder

![7-Zip source folder](../screenshots/sanitized/application-deployment/7zip-source-folder-sanitized.png)

### 7-Zip `.intunewin` package created

![7-Zip intunewin package created](../screenshots/sanitized/application-deployment/7zip-intunewin-created-sanitized.png)

### 7-Zip Win32 app upload

![7-Zip Win32 app upload](../screenshots/sanitized/application-deployment/7zip-win32-app-upload-sanitized.png)

### 7-Zip app information

![7-Zip app information](../screenshots/sanitized/application-deployment/7zip-app-information-sanitized.png)

### 7-Zip program settings

![7-Zip program settings](../screenshots/sanitized/application-deployment/7zip-program-settings-sanitized.png)

### 7-Zip requirements

![7-Zip requirements](../screenshots/sanitized/application-deployment/7zip-requirements-sanitized.png)

### 7-Zip detection rule

![7-Zip detection rule](../screenshots/sanitized/application-deployment/7zip-detection-rule-sanitized.png)

### 7-Zip required assignment

![7-Zip required assignment](../screenshots/sanitized/application-deployment/7zip-required-assignment-sanitized.png)

### 7-Zip device install status

![7-Zip device install status](../screenshots/sanitized/application-deployment/7zip-device-install-status-sanitized.png)

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
9. Check the local installation path on the device.
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
| 7-Zip installer prepared | Completed |
| `.intunewin` package created | Completed |
| Win32 app created in Intune | Completed |
| App assigned to pilot group | Completed |
| Device install status reviewed | Completed |
| Endpoint installation verified | Completed |
| Screenshots uploaded | Completed |
| Documentation updated with final evidence | Completed |

---

## Next Step

Continue with the next application deployment lab or update the project roadmap/README to reflect that the Win32 7-Zip deployment lab is completed.
