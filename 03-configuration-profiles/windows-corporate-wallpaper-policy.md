# Windows Corporate Wallpaper Policy

This file documents the configuration and testing of a corporate desktop wallpaper policy using Microsoft Intune.

## Objective

Apply a standard corporate wallpaper to a managed Windows device using a PowerShell platform script and a configuration profile.

## Lab Environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Operating system | Windows 11 |
| Management | Microsoft Intune |
| Assignment group | GRP-Pilot-Users |
| Wallpaper source | GitHub repository raw file URL |
| Local wallpaper path | C:\\CorpWall\\Wallpaper.jpg |

## Components Used

| Component | Purpose |
|---|---|
| PowerShell platform script | Downloads the wallpaper to the local device |
| Settings catalog profile | Applies the wallpaper path as a Windows policy |
| Pilot user group | Safely targets the test user/device |

## PowerShell Script

Script name:

```text
WIN-CORP-Download-Corporate-Wallpaper
```

Script content:

```powershell
New-Item -Path "C:\CorpWall" -ItemType Directory -Force

Invoke-WebRequest `
  -Uri "https://raw.githubusercontent.com/anup-moitra/md102-intune-virtual-company-lab/main/assets/wallpapers/Wallpaper.jpg" `
  -OutFile "C:\CorpWall\Wallpaper.jpg" `
  -UseBasicParsing
```

## Configuration Profile

| Setting | Value |
|---|---|
| Profile name | WIN-CORP-Corporate-Wallpaper-Policy |
| Platform | Windows 10 and later |
| Profile type | Settings catalog |
| Setting category | Administrative Templates |
| Setting path | Desktop > Desktop |
| Setting name | Desktop Wallpaper (User) |
| Wallpaper name | C:\\CorpWall\\Wallpaper.jpg |
| Wallpaper style | Fit |
| Assignment | GRP-Pilot-Users |

## Test Result

| Test Item | Result |
|---|---|
| PowerShell script created `C:\\CorpWall` | Successful |
| Wallpaper downloaded to `C:\\CorpWall\\Wallpaper.jpg` | Successful |
| Wallpaper configuration profile applied | Successful |
| Wallpaper appeared immediately after sync | No |
| Wallpaper appeared after restart | Successful |
| Final lab result | Successful |

## Key Learning

This lab showed that a corporate wallpaper deployment may require more than one Intune component.

```text
PowerShell script = delivers the wallpaper file
Configuration profile = applies the wallpaper policy
Restart/sign-in refresh = allows the user-based wallpaper setting to appear
```

## Screenshots

Suggested folder:

```text
screenshots/sanitized/configuration-profiles/
```

Suggested screenshots:

```text
wallpaper-script-device-status-sanitized.jpg
wallpaper-file-downloaded-sanitized.jpg
wallpaper-policy-settings-sanitized.jpg
wallpaper-policy-device-status-sanitized.jpg
wallpaper-applied-desktop-sanitized.jpg
```

## Current Lab Status

Completed:

- Wallpaper uploaded/prepared in GitHub assets folder
- PowerShell platform script created
- Wallpaper file downloaded to WIN-CORP-001
- Wallpaper configuration profile created
- Wallpaper policy assigned to GRP-Pilot-Users
- Wallpaper applied successfully after restart

Pending:

- Add sanitized screenshots as available
