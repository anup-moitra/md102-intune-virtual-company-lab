# Win32 App Deployment: 7-Zip

This file documents Win32 application deployment using Microsoft Intune.

## Objective

Deploy 7-Zip as a Win32 app using Microsoft Intune.

This lab demonstrates how to:

- Prepare a Win32 app source folder
- Package an installer into `.intunewin` format
- Upload the Win32 app to Intune
- Configure install and uninstall commands
- Configure detection rules
- Assign the app as Required
- Confirm installation on a managed Windows device

## Lab Environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Operating system | Windows 11 |
| Management | Microsoft Intune |
| Test user | user01 |
| Assignment group | GRP-Pilot-Users |
| App deployed | 7-Zip |
| App type | Windows app (Win32) |
| Package format | `.intunewin` |

## Application Details

| Item | Value |
|---|---|
| Application | 7-Zip |
| Installer type | EXE |
| Renamed installer | 7zip.exe |
| Architecture | x64 |
| Publisher | Igor Pavlov |
| Version | 26.01 |

## Program Settings

| Setting | Value |
|---|---|
| Install command | `7zip.exe /S` |
| Uninstall command | `"C:\\Program Files\\7-Zip\\Uninstall.exe" /S` |
| Install behavior | System |
| Device restart behavior | No specific action |

## Detection Rule

| Setting | Value |
|---|---|
| Rule type | File |
| Path | `C:\\Program Files\\7-Zip` |
| File or folder | `7zFM.exe` |
| Detection method | File or folder exists |

## Test Result

| Test Item | Result |
|---|---|
| Installer downloaded | Successful |
| `.intunewin` package created | Successful |
| Win32 app uploaded to Intune | Successful |
| Install command configured | Successful |
| Detection rule configured | Successful |
| App assigned to GRP-Pilot-Users | Successful |
| 7-Zip installed on WIN-CORP-001 | Successful |
| Final lab result | Successful |

## Key Learning

| Microsoft Store app | Win32 app |
|---|---|
| Search app in Intune | Download installer manually |
| No packaging needed | Must package as `.intunewin` |
| Basic assignment | Install/uninstall commands required |
| Easier setup | Detection rules required |

## Screenshots

Suggested folder:

```text
screenshots/sanitized/application-deployment/
```

Suggested screenshots:

```text
7zip-source-folder-sanitized.jpg
7zip-intunewin-created-sanitized.jpg
7zip-win32-app-properties-summary-sanitized.jpg
7zip-detection-rule-sanitized.jpg
7zip-device-install-status-sanitized.jpg
```

## Current Lab Status

Completed:

- 7-Zip installer downloaded
- Installer renamed to `7zip.exe`
- Win32 app package created as `7zip.intunewin`
- 7-Zip uploaded as a Windows app (Win32)
- Install and uninstall commands configured
- Detection rule configured
- App assigned as Required to GRP-Pilot-Users
- 7-Zip installed successfully on WIN-CORP-001

Pending:

- Add screenshots as available
