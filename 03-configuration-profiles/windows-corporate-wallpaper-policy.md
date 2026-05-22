# Windows Corporate Wallpaper Policy

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Configuration profiles |
| Platform | Windows 10 and later |
| Target device | WINAUTO452 |
| Target user | user01 |
| Script name | SCRIPT-WIN-Stage-Corporate-Wallpaper |
| Script assignment group | GRP-Autopilot-Devices |
| Profile name | CFG-WIN-Corporate-Wallpaper-ADMX |
| Profile assignment group | GRP-Pilot-Users |

---

## Lab Objective

Deploy a corporate desktop wallpaper to an Autopilot-managed Windows device using a two-part approach: a PowerShell platform script to stage the image locally, and an ADMX-backed configuration profile to apply it in the user context.

---

## Why This Lab Matters

A reliable corporate wallpaper deployment needs to separate two responsibilities — getting the file onto the device and applying it as a user setting. This lab demonstrates that pattern, and documents a real troubleshooting case where an earlier approach failed and had to be rebuilt.

---

## Prerequisites

- GRP-Pilot-Users and GRP-Autopilot-Devices available
- WINAUTO452 enrolled and able to sync with Intune
- Wallpaper image uploaded to the GitHub repository

Wallpaper image path in repo:
```text
assets/wallpapers/homelab-corporate-wallpaper.jpg
```

Raw GitHub URL used by the staging script:
```text
https://raw.githubusercontent.com/anup-moitra/md102-intune-virtual-company-lab/main/assets/wallpapers/homelab-corporate-wallpaper.jpg
```

---

## Deployment Design

| Component | Purpose | Assignment |
|---|---|---|
| PowerShell platform script | Downloads and stages the wallpaper to `C:\ProgramData` | GRP-Autopilot-Devices (device group) |
| ADMX-backed configuration profile | Applies the wallpaper in the signed-in user context | GRP-Pilot-Users (user group) |

The script must run first so the file exists before the ADMX policy tries to apply it. Device group assignment ensures the file is staged on the endpoint regardless of which user signs in. User group assignment ensures the wallpaper setting applies to the correct user session.

---

## Configuration Flow

```text
Create and upload PowerShell staging script
-> Assign script to GRP-Autopilot-Devices
-> Verify script success on WINAUTO452
-> Create Settings catalog profile
-> Configure ADMX Desktop Wallpaper user setting
-> Assign profile to GRP-Pilot-Users
-> Sync device and sign in as user01
-> Verify policy success in Intune
-> Validate wallpaper on endpoint desktop
```

---

## Steps Performed

### Step 1 — Created the PowerShell staging script

Script filename: `Stage-HomeLab-Corporate-Wallpaper.ps1`

```powershell
$WallpaperUrl = "https://raw.githubusercontent.com/anup-moitra/md102-intune-virtual-company-lab/main/assets/wallpapers/homelab-corporate-wallpaper.jpg"

$WallpaperFolder = "C:\ProgramData\HomeLab\Wallpapers"
$WallpaperPath = Join-Path $WallpaperFolder "homelab-corporate-wallpaper.jpg"

New-Item -ItemType Directory -Path $WallpaperFolder -Force | Out-Null

Invoke-WebRequest -Uri $WallpaperUrl -OutFile $WallpaperPath -UseBasicParsing

if (Test-Path $WallpaperPath) {
    Write-Output "Wallpaper staged successfully at $WallpaperPath"
    exit 0
}
else {
    Write-Output "Wallpaper staging failed."
    exit 1
}
```

---

### Step 2 — Uploaded and assigned the script in Intune

Navigated to:

```text
Devices -> Scripts and remediations -> Platform scripts -> Add -> Windows 10 and later
```

| Setting | Value |
|---|---|
| Name | SCRIPT-WIN-Stage-Corporate-Wallpaper |
| Run using logged-on credentials | No (runs as system — appropriate for writing to `C:\ProgramData`) |
| Enforce script signature check | No |
| Run script in 64-bit PowerShell Host | Yes |

Assigned to `GRP-Autopilot-Devices` (device-based, so the file is staged regardless of which user signs in).

![PowerShell script basics](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-basics-sanitized.png)

![PowerShell script settings](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-settings-sanitized.png)

![PowerShell script assignment](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-assignment-sanitized.png)

![PowerShell script review and create](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-review-create-sanitized.png)

---

### Step 3 — Verified script success

| Item | Result |
|---|---|
| Script | SCRIPT-WIN-Stage-Corporate-Wallpaper |
| Device | WINAUTO452 |
| Status | Succeeded |
| Local path | `C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg` |

![PowerShell script device status success](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-device-status-success-sanitized.png)

---

### Step 4 — Created and configured the ADMX wallpaper profile

Navigated to:

```text
Devices -> Configuration -> Create -> New policy
```

Selected Windows 10 and later / Settings catalog. Named the profile `CFG-WIN-Corporate-Wallpaper-ADMX`.

Settings catalog path used:

```text
Administrative Templates -> Desktop -> Desktop -> Desktop Wallpaper (User)
```

| Setting | Value |
|---|---|
| Desktop Wallpaper (User) | Enabled |
| Wallpaper Name | `C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg` |
| Wallpaper Style | Fill |

> [!IMPORTANT]
> Use the normal Windows file path, not a `file:///` URL. The `file:///` format applies to the older `Personalization > Desktop Image Url` setting and caused errors on Windows 11 Pro. The ADMX-backed Desktop Wallpaper setting requires a standard path.

Assigned to `GRP-Pilot-Users` (user-based, since this is a user setting that applies in the signed-in user context).

![Create Settings Catalog profile](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-create-profile-sanitized.png)

![ADMX wallpaper profile basics](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-profile-basics-sanitized.png)

![ADMX desktop wallpaper setting](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-setting-sanitized.png)

![ADMX wallpaper policy assignment](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-assignment-sanitized.png)

![ADMX wallpaper policy review and create](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-review-create-sanitized.png)

---

### Step 5 — Synced, restarted, and validated

Synced WINAUTO452 from Intune and from Windows Settings. Restarted the device and signed in as user01. The corporate wallpaper appeared on the desktop.

| Item | Result |
|---|---|
| Profile | CFG-WIN-Corporate-Wallpaper-ADMX |
| Device | WINAUTO452 |
| User | user01 |
| Assignment status | Success |
| Endpoint result | Wallpaper applied |

![ADMX wallpaper device status success](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-device-status-success-sanitized.png)

![Corporate wallpaper endpoint validation](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-endpoint-validation-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| PowerShell script created and uploaded | Completed |
| Script assigned to GRP-Autopilot-Devices | Completed |
| Script succeeded on WINAUTO452 | Completed |
| Wallpaper staged under `C:\ProgramData` | Completed |
| ADMX wallpaper profile created | Completed |
| Desktop Wallpaper user setting configured | Completed |
| Profile assigned to GRP-Pilot-Users | Completed |
| Profile reported Success for WINAUTO452 | Completed |
| Wallpaper visible on endpoint desktop | Completed |

---

## Troubleshooting Notes

**Earlier approach failed — Desktop Image Url returned an error** — the first attempt used `Personalization > Desktop Image Url` with a `file:///` local path. The endpoint returned an error even though the file existed and could be opened manually. The lab was rebuilt using the ADMX-backed `Administrative Templates > Desktop > Desktop > Desktop Wallpaper (User)` setting with a standard Windows file path, which applied successfully.

**Wallpaper policy succeeds in Intune but does not apply on the endpoint** — check that the staging script ran successfully first and the file exists at `C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg`. Also confirm the user-targeted policy is assigned to the correct user group and that the user has signed in after the policy synced. Some settings require a sign-out/sign-in or reboot to take effect.

---

## Enterprise Reflection

In production, separating file delivery from policy enforcement is the right design pattern for wallpaper deployment:

| Requirement | Recommended approach |
|---|---|
| Stage wallpaper file | PowerShell script, Win32 app, or Intune Remediation assigned to device group |
| Apply wallpaper setting | ADMX-backed user policy assigned to user group |
| Monthly wallpaper changes | Host images at a company-controlled HTTPS location with versioned filenames |
| Reliable detection | Use Win32 app detection rules or Remediation detection scripts |
| Pilot rollout | Validate on pilot groups before broad deployment |

---

## Key Learning Outcomes

- How to stage a file on a Windows endpoint using an Intune PowerShell platform script
- Why device group assignment is used for file staging and user group assignment for wallpaper policy
- How the ADMX-backed Desktop Wallpaper setting differs from the Settings catalog Desktop Image Url setting
- How to diagnose a failed wallpaper deployment and rebuild with a working approach
- Why endpoint visual validation is required alongside Intune policy success reporting
