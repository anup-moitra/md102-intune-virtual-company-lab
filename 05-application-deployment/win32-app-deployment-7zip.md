# Win32 App Deployment: 7-Zip

## Lab status

**Status:** Completed  
**Lab category:** Application deployment  
**Platform:** Windows  
**Management platform:** Microsoft Intune  
**Identity platform:** Microsoft Entra ID  
**Test device:** WIN-CORP-001  
**Test user:** user01  
**Assignment group:** GRP-Pilot-Users  
**App deployed:** 7-Zip  
**App type:** Windows app (Win32)  
**Package format:** `.intunewin`  
**Assignment type:** Required  
**Final result:** 7-Zip installed successfully on the managed Windows endpoint  

---

## Lab objective

The objective of this lab is to deploy 7-Zip as a **Windows app (Win32)** using Microsoft Intune.

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

## Why this lab matters

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

Simple deployment flow:

```text
Download installer
-> Prepare Win32 source folder
-> Package installer as .intunewin
-> Upload Win32 app to Intune
-> Configure commands and detection rule
-> Assign app to pilot users
-> Sync managed Windows device
-> Verify installation status
-> Confirm the app is installed on the endpoint
```

---

## Lab environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | user01 |
| Assignment group | GRP-Pilot-Users |
| App deployed | 7-Zip |
| App type | Windows app (Win32) |
| Installer type | EXE |
| Package format | `.intunewin` |
| Assignment type | Required |
| Install behavior | System |
| Final lab status | Completed |

---

## Prerequisites

Before starting this lab, the following were required:

- Microsoft Intune tenant available.
- Microsoft Entra ID users created.
- `user01` created and licensed.
- `user01` added to `GRP-Pilot-Users`.
- Windows device enrolled into Intune.
- Test device `WIN-CORP-001` available.
- 7-Zip Windows x64 installer downloaded.
- Microsoft Win32 Content Prep Tool downloaded.
- Device able to sync with Intune.
- Internet access available on the endpoint.

---

## App packaging design

A Win32 app in Intune is not uploaded directly as a normal `.exe` file.

The installer must first be converted into Intune's package format:

```text
Original installer: 7zip.exe
Packaged installer: 7zip.intunewin
```

Intune then uses the **Intune Management Extension** on the Windows device to process the Win32 app installation.

### Application details

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
| Tool folder | `C:\IntuneWin32\Tool` |
| Packaged file | `7zip.intunewin` |

### Local folder structure

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

## Configuration flow

```text
Download 7-Zip installer
-> Rename installer to 7zip.exe
-> Place installer in source folder
-> Download Win32 Content Prep Tool
-> Package installer as .intunewin
-> Create Windows app (Win32) in Intune
-> Upload 7zip.intunewin
-> Configure app information
-> Configure install and uninstall commands
-> Configure requirements
-> Configure detection rule
-> Assign app as Required to GRP-Pilot-Users
-> Sync WIN-CORP-001
-> Verify install status in Intune
-> Verify 7-Zip locally on endpoint
```

---

## Steps performed

### Step 1 - Downloaded 7-Zip installer

The Windows x64 7-Zip EXE installer was downloaded.

The installer was renamed to:

```text
7zip.exe
```

The renamed installer was placed in:

```text
C:\IntuneWin32\7zip\Source
```

---

### Step 2 - Downloaded Win32 Content Prep Tool

The Microsoft Win32 Content Prep Tool was downloaded and extracted.

The tool used was:

```text
IntuneWinAppUtil.exe
```

---

### Step 3 - Created the `.intunewin` package

The Microsoft Win32 Content Prep Tool was used to create the `.intunewin` package.

Command used:

```cmd
IntuneWinAppUtil.exe -c "C:\IntuneWin32\7zip\Source" -s "7zip.exe" -o "C:\IntuneWin32\7zip\Output" -q
```

Expected output:

```text
C:\IntuneWin32\7zip\Output\7zip.intunewin
```

The output package was created successfully:

```text
7zip.intunewin
```

---

### Step 4 - Created Win32 app in Intune

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

---

### Step 5 - Configured app information

The app information was configured as follows:

| Setting | Value |
|---|---|
| Name | 7-Zip |
| Description | Deploys 7-Zip as a Win32 app for the MD-102 Intune lab. |
| Publisher | Igor Pavlov |
| Category | Productivity or Utilities |
| Owner | IT Admin |
| Notes | Win32 app deployment test for MD-102 Intune lab |
| Logo | Not configured |

---

### Step 6 - Configured program commands

Program settings were configured as follows:

| Setting | Value |
|---|---|
| Install command | `7zip.exe /S` |
| Uninstall command | `"C:\Program Files\7-Zip\Uninstall.exe" /S` |
| Install behavior | System |
| Device restart behavior | No specific action |

> [!NOTE]
> The `/S` silent install switch is case-sensitive for the 7-Zip installer.

---

### Step 7 - Configured requirements

Requirements were configured for 64-bit Windows devices.

| Setting | Value |
|---|---|
| Operating system architecture | 64-bit |
| Minimum operating system | Windows 10 1607 or later / Windows 11 |
| Disk space required | Not configured |
| Physical memory required | Not configured |
| Minimum number of logical processors | Not configured |
| Minimum CPU speed | Not configured |

---

### Step 8 - Configured detection rule

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

### Step 9 - Configured dependencies and supersedence

No dependencies were configured.

No supersedence relationship was configured.

This was a first-time deployment, so there was no older app version to replace.

---

### Step 10 - Assigned the app

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

### Step 11 - Created the app

The Win32 app was created in Microsoft Intune.

---

### Step 12 - Verified install status in Intune

The install status was checked from:

```text
Intune admin center
-> Apps
-> Windows
-> 7-Zip
-> Monitor
-> Device install status
```

The install status was reviewed and captured for documentation.

---

### Step 13 - Verified 7-Zip on the endpoint

On `WIN-CORP-001`, 7-Zip was verified locally by checking that the app was installed and available from the Start menu.

The expected file path was also validated:

```text
C:\Program Files\7-Zip\7zFM.exe
```

---

## Validation

### Package validation

Validation confirmed that:

- The 7-Zip installer was downloaded.
- The installer was renamed to `7zip.exe`.
- The source folder was prepared.
- The Win32 Content Prep Tool created the `.intunewin` package.
- The output file `7zip.intunewin` was created successfully.

---

### Intune app configuration validation

Validation confirmed that:

- The app type was set to **Windows app (Win32)**.
- The `.intunewin` package was uploaded.
- App information was configured.
- Program install and uninstall commands were configured.
- Requirements were configured for 64-bit Windows.
- A file-based detection rule was configured.
- Dependencies and supersedence were not required for this app.

---

### Assignment validation

Validation confirmed that:

- The app was assigned as **Required**.
- The target assignment group was `GRP-Pilot-Users`.
- `user01` was included through the pilot group.

---

### Endpoint validation

Validation confirmed that:

- `WIN-CORP-001` received the required Win32 app assignment.
- Intune app install status was reviewed.
- 7-Zip was installed on the endpoint.
- The detection path existed:

```text
C:\Program Files\7-Zip\7zFM.exe
```

---

## Final test result

| Validation item | Status |
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
| 7-Zip local installation verified on WIN-CORP-001 | Completed |
| Screenshots captured and uploaded | Completed |
| Final lab result | Completed |

Observed final result:

```text
7-Zip was packaged as a Win32 app, uploaded to Intune, assigned as Required, installed on WIN-CORP-001, and verified successfully.
```

---

## Screenshots captured

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

## Screenshot file list

```text
7zip-source-folder-sanitized.png
7zip-intunewin-created-sanitized.png
7zip-win32-app-upload-sanitized.png
7zip-app-information-sanitized.png
7zip-program-settings-sanitized.png
7zip-requirements-sanitized.png
7zip-detection-rule-sanitized.png
7zip-required-assignment-sanitized.png
7zip-device-install-status-sanitized.png
```

---

## Troubleshooting notes

### App does not install

If the app does not install:

1. Confirm the app is assigned as **Required**.
2. Confirm `user01` is a member of `GRP-Pilot-Users`.
3. Confirm `WIN-CORP-001` is enrolled and checking in to Intune.
4. Trigger a manual sync from Windows Settings.
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

---

### App installs but Intune reports failure

If the app installs but Intune still reports failure:

1. Check whether `7zFM.exe` exists in the configured detection path.
2. Confirm the detection rule uses the correct file name.
3. Confirm the app installed to `C:\Program Files\7-Zip` and not a different path.
4. Confirm the detection rule is not configured as a 32-bit app on 64-bit clients.
5. Review Intune Management Extension logs if needed.

Common log location:

```text
C:\ProgramData\Microsoft\IntuneManagementExtension\Logs\IntuneManagementExtension.log
```

---

### Package upload issue

If the `.intunewin` package fails to upload:

1. Confirm the package was created successfully.
2. Confirm the file extension is `.intunewin`.
3. Confirm the original source folder was not modified during upload.
4. Recreate the package if needed.
5. Try uploading the package again.

---

### Silent install command issue

If the installer opens interactively or does not install silently:

1. Confirm the install command uses uppercase `/S`.
2. Confirm the installer file name matches the uploaded source file.
3. Test the install command locally before packaging.
4. Repackage the app if the source file name changes.

Correct command:

```cmd
7zip.exe /S
```

---

## Enterprise reflection

Win32 app deployment is one of the most important Intune administration skills because many business apps are not available through the Microsoft Store.

In production environments, admins should carefully plan:

| Area | Recommendation |
|---|---|
| Source folder | Keep a clean source folder for each app/version |
| Installer naming | Use consistent installer names |
| Silent install command | Test locally before packaging |
| Detection rule | Use reliable file, registry, or MSI detection |
| Assignment group | Use pilot groups first |
| Restart behavior | Configure carefully to avoid user disruption |
| Versioning | Create clear app names or supersedence rules |
| Logs | Use Intune Management Extension logs for troubleshooting |

A safer enterprise rollout model is:

```text
Package app
-> Test install command locally
-> Deploy to pilot group
-> Confirm detection rule
-> Monitor Intune install status
-> Expand to production groups
```

For this lab, the pilot assignment group was:

```text
GRP-Pilot-Users
```

This allowed the app to be tested safely before any broader deployment.

---

## Security and privacy notes

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
- Proprietary installers or licensed commercial software packages

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs
- Object IDs
- Any sensitive identifiers

---

## Related labs

| Lab file | Relationship |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Provides `user01` and `GRP-Pilot-Users` |
| `02-device-enrollment/windows-oobe-enrollment.md` | Provides the managed Windows test device `WIN-CORP-001` |
| `05-application-deployment/microsoft-store-app-deployment.md` | Previous app deployment lab using Microsoft Store apps |
| `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Next app deployment lab using Microsoft 365 Apps |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Validates required app deployment after Autopilot enrollment |

---

## Key learning outcomes

This lab demonstrated how to:

- Prepare a Win32 app source folder.
- Use the Microsoft Win32 Content Prep Tool.
- Package an EXE installer as `.intunewin`.
- Upload a Win32 app to Microsoft Intune.
- Configure app information.
- Configure silent install and uninstall commands.
- Configure app requirements.
- Configure a file-based detection rule.
- Assign a Win32 app as Required.
- Validate app deployment status in Intune.
- Confirm local app installation on a Windows endpoint.
- Understand the role of the Intune Management Extension.

---

## Lab conclusion

The Win32 7-Zip app deployment lab was completed successfully.

Final result:

```text
7-Zip was packaged into .intunewin format.
The Win32 app was uploaded to Microsoft Intune.
The install and uninstall commands were configured.
The detection rule was configured.
The app was assigned as Required to GRP-Pilot-Users.
7-Zip installed successfully on WIN-CORP-001.
```

This confirms that the lab tenant can deploy traditional Win32 applications through Microsoft Intune.
