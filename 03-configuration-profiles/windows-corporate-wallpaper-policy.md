# Windows Corporate Wallpaper Policy

## Lab status

**Status:** Completed  
**Lab category:** Configuration profiles  
**Platform:** Windows 10 and later  
**Management platform:** Microsoft Intune  
**Target endpoint:** WINAUTO452  
**Target user:** user01  
**Script target group:** GRP-Autopilot-Devices  
**Wallpaper policy target group:** GRP-Pilot-Users  

---

## Lab objective

The objective of this lab is to deploy a corporate desktop wallpaper to an Autopilot-managed Windows device using Microsoft Intune.

This rebuilt lab uses a cleaner and more reliable approach:

| Component | Purpose |
|---|---|
| PowerShell platform script | Downloads and stages the wallpaper image locally under `C:\ProgramData` |
| ADMX-backed configuration profile | Configures the desktop wallpaper using the local file path |
| User assignment group | Applies the wallpaper setting to the signed-in user |

Final result:

```text
Corporate wallpaper was successfully applied on WINAUTO452.
```

---

## Why this approach was used

The earlier wallpaper approach used the Settings Catalog setting:

```text
Personalization > Desktop Image Url
```

with a local file URL:

```text
file:///C:/ProgramData/HomeLab/Wallpapers/homelab-corporate-wallpaper.jpg
```

That approach returned an error on the Windows 11 Pro test device.

For the rebuilt lab, the policy was changed to the ADMX-backed setting:

```text
Administrative Templates
-> Desktop
-> Desktop
-> Desktop Wallpaper (User)
```

This approach uses a normal Windows file path:

```text
C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg
```

This design separates the lab into two clear parts:

```text
Stage wallpaper file locally
-> Apply user wallpaper policy
-> Validate wallpaper on endpoint
```

---

## Lab environment

| Item | Value |
|---|---|
| Device name | WINAUTO452 |
| Device type | Windows laptop |
| Device ownership | Corporate |
| Enrollment method | Windows Autopilot |
| Management | Microsoft Intune |
| Operating system | Windows 11 Pro |
| Primary user | user01 |
| Wallpaper source | GitHub raw image URL |
| Local wallpaper path | `C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg` |
| Script name | `SCRIPT-WIN-Stage-Corporate-Wallpaper` |
| Configuration profile name | `CFG-WIN-Corporate-Wallpaper-ADMX` |
| Final result | Completed successfully |

---

## Wallpaper source

The wallpaper image is stored in the GitHub repository under:

```text
assets/wallpapers/homelab-corporate-wallpaper.jpg
```

Raw GitHub URL used by the PowerShell script:

```text
https://raw.githubusercontent.com/anup-moitra/md102-intune-virtual-company-lab/main/assets/wallpapers/homelab-corporate-wallpaper.jpg
```

The script downloads this image and saves it locally as:

```text
C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg
```

---

## Deployment flow

```text
1. Create PowerShell script
2. Upload script to Intune
3. Assign script to corporate Autopilot device group
4. Script downloads wallpaper to C:\ProgramData
5. Create Settings Catalog profile
6. Configure ADMX-backed Desktop Wallpaper user setting
7. Assign wallpaper policy to pilot user group
8. Sync device and sign in as target user
9. Verify Intune policy success
10. Confirm wallpaper applied on endpoint
```

---

## Part 1 - Create the PowerShell staging script

### Script name

```text
Stage-HomeLab-Corporate-Wallpaper.ps1
```

### Script content

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

### What the script does

The script performs the following actions:

1. Defines the GitHub raw URL for the wallpaper image.
2. Creates the folder `C:\ProgramData\HomeLab\Wallpapers`.
3. Downloads the wallpaper image from GitHub.
4. Saves the image locally as `homelab-corporate-wallpaper.jpg`.
5. Confirms whether the file exists.
6. Returns success or failure based on the file validation.

---

## Part 2 - Deploy the PowerShell script from Intune

### Navigation path

```text
Microsoft Intune admin center
-> Devices
-> Scripts and remediations
-> Platform scripts
-> Add
-> Windows 10 and later
```

### Script basics

| Setting | Value |
|---|---|
| Name | `SCRIPT-WIN-Stage-Corporate-Wallpaper` |
| Description | Downloads the HomeLab corporate wallpaper from GitHub and stages it locally under `C:\ProgramData` for the ADMX desktop wallpaper policy. |

![PowerShell script basics](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-basics-sanitized.png)

---

### Script settings

| Setting | Value |
|---|---|
| PowerShell script | `Stage-HomeLab-Corporate-Wallpaper.ps1` |
| Run this script using the logged on credentials | No |
| Enforce script signature check | No |
| Run script in 64-bit PowerShell Host | Yes |

![PowerShell script settings](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-settings-sanitized.png)

### Why these script settings were used

| Setting | Reason |
|---|---|
| Run using logged-on credentials: No | Runs as system, which is suitable for writing to `C:\ProgramData` |
| Enforce script signature check: No | The lab script is not code-signed |
| Run script in 64-bit PowerShell Host: Yes | Uses the native 64-bit PowerShell host on the endpoint |

---

### Script assignment

The script was assigned to the corporate Autopilot device group:

```text
GRP-Autopilot-Devices
```

Target device:

```text
WINAUTO452
```

![PowerShell script assignment](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-assignment-sanitized.png)

---

### Script review and create

The script configuration was reviewed before creation.

![PowerShell script review and create](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-review-create-sanitized.png)

---

### Script deployment result

The PowerShell script completed successfully on the target device.

| Item | Result |
|---|---|
| Script | `SCRIPT-WIN-Stage-Corporate-Wallpaper` |
| Device | WINAUTO452 |
| User | user01 |
| Status | Succeeded |
| OS version | Windows 11 |
| Result | Wallpaper staged locally |

![PowerShell script device status success](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-script-device-status-success-sanitized.png)

---

## Part 3 - Create the ADMX-backed wallpaper configuration profile

### Navigation path

```text
Microsoft Intune admin center
-> Devices
-> Configuration
-> Create
-> New policy
```

Selected:

| Setting | Value |
|---|---|
| Platform | Windows 10 and later |
| Profile type | Settings catalog |

![Create Settings Catalog profile](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-create-profile-sanitized.png)

---

### Profile basics

| Setting | Value |
|---|---|
| Name | `CFG-WIN-Corporate-Wallpaper-ADMX` |
| Description | Configures the corporate desktop wallpaper using the ADMX-backed Desktop Wallpaper user setting. |

![ADMX wallpaper profile basics](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-profile-basics-sanitized.png)

---

## Part 4 - Configure the Desktop Wallpaper ADMX setting

### Settings Catalog path

```text
Administrative Templates
-> Desktop
-> Desktop
```

Configured setting:

```text
Desktop Wallpaper (User)
```

### Configuration values

| Setting | Value |
|---|---|
| Desktop Wallpaper (User) | Enabled |
| Wallpaper Name (User) | `C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg` |
| Wallpaper Style (User) | Fill |

![ADMX desktop wallpaper setting](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-setting-sanitized.png)

### Important note

This ADMX-backed setting uses a normal Windows file path.

Correct value:

```text
C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg
```

Do not use this value for the ADMX-backed Desktop Wallpaper setting:

```text
file:///C:/ProgramData/HomeLab/Wallpapers/homelab-corporate-wallpaper.jpg
```

The `file:///` format was part of the older Desktop Image Url approach and was not used in the rebuilt successful lab.

---

## Part 5 - Assign the ADMX wallpaper policy

Because `Desktop Wallpaper (User)` is a user setting, the configuration profile was assigned to a user group.

Assigned group:

```text
GRP-Pilot-Users
```

Target user:

```text
user01
```

![ADMX wallpaper policy assignment](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-assignment-sanitized.png)

---

### ADMX policy review and create

The ADMX wallpaper configuration profile was reviewed before creation.

![ADMX wallpaper policy review and create](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-review-create-sanitized.png)

---

## Part 6 - Validate policy deployment

After the policy was created, the target endpoint was synced and the policy status was reviewed in Intune.

### Sync methods used

From Intune:

```text
Devices
-> Windows
-> WINAUTO452
-> Sync
```

From the endpoint:

```text
Settings
-> Accounts
-> Access work or school
-> Connected work or school account
-> Info
-> Sync
```

The device was restarted and the target user signed in again.

---

### ADMX policy deployment result

The configuration profile reported success for the target device.

| Item | Result |
|---|---|
| Profile | `CFG-WIN-Corporate-Wallpaper-ADMX` |
| Target device | WINAUTO452 |
| Logged-in user | user01 |
| Assignment status | Success |
| Error | 0 |
| Conflict | 0 |
| Result | Wallpaper policy applied |

![ADMX wallpaper device status success](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-admx-device-status-success-sanitized.png)

---

## Part 7 - Endpoint validation

The wallpaper was successfully applied on the endpoint desktop.

Observed result:

```text
The desktop background changed to the corporate HomeLab wallpaper.
```

Endpoint validation device:

```text
WINAUTO452
```

![Corporate wallpaper endpoint validation](../screenshots/sanitized/configuration-profiles/windows-corporate-wallpaper-endpoint-validation-sanitized.png)

---

## Final test result

| Validation item | Status |
|---|---|
| Wallpaper image exists in GitHub repository | Completed |
| PowerShell staging script created | Completed |
| PowerShell script uploaded to Intune | Completed |
| Script assigned to Autopilot device group | Completed |
| Script executed successfully on WINAUTO452 | Completed |
| Wallpaper staged under `C:\ProgramData` | Completed |
| ADMX-backed wallpaper profile created | Completed |
| Desktop Wallpaper user setting configured | Completed |
| Wallpaper policy assigned to pilot user group | Completed |
| ADMX policy reported success for WINAUTO452 | Completed |
| Endpoint wallpaper visually validated | Completed |
| Final lab result | Completed |

---

## Screenshots captured

All screenshots are stored in:

```text
screenshots/sanitized/configuration-profiles/
```

| Screenshot | Purpose |
|---|---|
| `windows-corporate-wallpaper-script-basics-sanitized.png` | PowerShell script basics |
| `windows-corporate-wallpaper-script-settings-sanitized.png` | PowerShell script settings |
| `windows-corporate-wallpaper-script-assignment-sanitized.png` | PowerShell script assignment |
| `windows-corporate-wallpaper-script-review-create-sanitized.png` | PowerShell script review and create |
| `windows-corporate-wallpaper-script-device-status-success-sanitized.png` | PowerShell script success status |
| `windows-corporate-wallpaper-admx-create-profile-sanitized.png` | Settings Catalog profile creation |
| `windows-corporate-wallpaper-admx-profile-basics-sanitized.png` | ADMX wallpaper profile basics |
| `windows-corporate-wallpaper-admx-setting-sanitized.png` | Desktop Wallpaper ADMX setting |
| `windows-corporate-wallpaper-admx-assignment-sanitized.png` | ADMX policy assignment |
| `windows-corporate-wallpaper-admx-review-create-sanitized.png` | ADMX policy review and create |
| `windows-corporate-wallpaper-admx-device-status-success-sanitized.png` | ADMX policy success status |
| `windows-corporate-wallpaper-endpoint-validation-sanitized.png` | Endpoint wallpaper validation |

---

## Troubleshooting notes

### Previous issue: Desktop Image Url error

The earlier lab attempt used:

```text
Personalization -> Desktop Image Url
```

with this local file URL:

```text
file:///C:/ProgramData/HomeLab/Wallpapers/homelab-corporate-wallpaper.jpg
```

The endpoint returned an error for the `Desktop Image Url` setting. The file existed locally and opened successfully, but the profile still failed.

To resolve the issue, the lab was rebuilt using:

```text
Administrative Templates -> Desktop -> Desktop -> Desktop Wallpaper (User)
```

This ADMX-backed setting used the normal local path:

```text
C:\ProgramData\HomeLab\Wallpapers\homelab-corporate-wallpaper.jpg
```

The rebuilt approach applied successfully.

---

### Why the script and policy were separated

The wallpaper file must exist locally before the ADMX wallpaper setting can apply it.

The PowerShell script handles file staging:

```text
Download wallpaper
-> Create local folder
-> Save image to C:\ProgramData
```

The configuration profile handles user policy enforcement:

```text
Set desktop wallpaper
-> Use local file path
-> Apply to user context
```

This separation is useful for learning and troubleshooting because it makes the two responsibilities clear.

---

## Enterprise reflection

For a real corporate environment, wallpaper deployment can be handled in different ways depending on scale and requirements.

| Requirement | Recommended approach |
|---|---|
| Simple wallpaper deployment | Use an Intune configuration profile if supported |
| Monthly wallpaper changes | Host approved images in a company-controlled HTTPS location or package them with versioned filenames |
| Local wallpaper file required | Stage the image using Win32 app, script, or remediation |
| Reliable detection required | Use Win32 app detection rules or Intune Remediations |
| User-specific wallpaper policy | Assign ADMX-backed user setting to user groups |
| Device-wide file staging | Assign script/app/remediation to device groups |
| Pilot rollout | Use pilot groups before broad deployment |

For this lab, the final successful design was:

```text
Device group stages the file
User group receives the wallpaper policy
Endpoint confirms the wallpaper applied successfully
```

---

## Security and privacy notes

This is a public learning repository.

Do not publish screenshots that show:

- Full user email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Internal IP addresses
- MAC addresses
- Passwords
- Recovery keys
- Unsanitized tenant information
- Production company data

Screenshots should be sanitized before upload.

---

## Key learning outcomes

This lab demonstrated:

- How to rebuild a failed Intune wallpaper deployment using a better approach.
- How to stage a file locally with an Intune PowerShell platform script.
- How to assign a script to a device group.
- How to configure the ADMX-backed Desktop Wallpaper user setting.
- Why user settings should be assigned to user groups.
- How to validate script success in Intune.
- How to validate configuration profile success in Intune.
- How to confirm wallpaper application on the endpoint.
- How to document troubleshooting and final resolution professionally.

---

## Lab conclusion

The corporate wallpaper deployment was completed successfully.

Final result:

```text
SCRIPT-WIN-Stage-Corporate-Wallpaper succeeded on WINAUTO452.
CFG-WIN-Corporate-Wallpaper-ADMX succeeded on WINAUTO452.
The corporate wallpaper was visible on the endpoint desktop.
```
