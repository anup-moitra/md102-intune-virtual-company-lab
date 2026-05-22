# Windows Autopilot User-Driven Enrollment

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Device enrollment |
| Enrollment method | Windows Autopilot user-driven enrollment |
| Join type | Microsoft Entra joined |
| Management platform | Microsoft Intune |
| Target user | user01 |
| Autopilot device group | GRP-Autopilot-Devices |
| Final enrolled device | WINAUTO452 |

---

## Lab Objective

Manually register a Windows device with Windows Autopilot, configure a user-driven deployment profile, and complete OOBE enrollment into Microsoft Intune — then validate corporate ownership, compliance, and post-enrollment app delivery.

---

## Why This Lab Matters

Windows Autopilot replaces traditional imaging. Instead of IT manually preparing each device, the device identifies itself at OOBE through its hardware hash, receives a cloud-assigned profile, and self-provisions after the user signs in.

```text
Device starts at Windows OOBE
-> Connects to the internet
-> Identifies itself via hardware hash
-> Downloads assigned Autopilot profile
-> User signs in with Microsoft Entra ID account
-> Device joins Microsoft Entra ID
-> Device enrolls into Microsoft Intune
-> Apps and policies deploy automatically
```

---

## Prerequisites

- Microsoft Intune tenant available
- user01 created and licensed
- Automatic MDM enrollment configured
- Microsoft Entra device join settings allow user-driven provisioning
- GRP-Autopilot-Devices dynamic device group prepared
- Windows test device available for enrollment
- Required app deployments created for post-enrollment validation

---

## Autopilot Design

### Deployment Profile

| Setting | Value |
|---|---|
| Profile name | APUserDrivenEntraJoinPilot |
| Platform | Windows PC |
| Deployment mode | User-driven |
| Join type | Microsoft Entra joined |
| User account type | Standard |
| Microsoft Software License Terms | Hide |
| Privacy settings | Hide |
| Hide change account options | Hide |
| Allow pre-provisioned deployment | No |
| Language / region | Operating system default |
| Automatically configure keyboard | Yes |
| Apply device name template | Yes |
| Device name template | WINAUTO%RAND:3% |
| Assigned group | GRP-Autopilot-Devices |

The name template `WINAUTO%RAND:3%` generated the device name **WINAUTO452** during provisioning.

### Device Group

| Setting | Value |
|---|---|
| Group name | GRP-Autopilot-Devices |
| Group type | Security / dynamic device |
| Purpose | Target Autopilot deployment profile to imported devices |

---

## Configuration Flow

```text
Review automatic MDM enrollment and Entra device join settings
-> Collect hardware hash from Windows OOBE
-> Import hardware hash CSV into Intune
-> Create Autopilot deployment profile
-> Assign profile to GRP-Autopilot-Devices
-> Wait for profile status to show Assigned
-> Complete Windows OOBE as user01
-> Verify enrollment, ownership, compliance, and apps in Intune
```

---

## Steps Performed

### Step 1 — Reviewed tenant prerequisites

Confirmed automatic MDM enrollment was enabled for eligible users and that Microsoft Entra device join settings allowed user01 to join devices. Both are required for Autopilot user-driven enrollment to work — the user signs in at OOBE, the device joins Entra ID, and MDM enrollment triggers automatically.

![Automatic MDM enrollment](../screenshots/sanitized/device-enrollment/autopilot-automatic-mdm-enrollment-sanitized.png)

![Microsoft Entra device join settings](../screenshots/sanitized/device-enrollment/autopilot-entra-device-join-settings-sanitized.png)

---

### Step 2 — Confirmed Autopilot device group

Confirmed `GRP-Autopilot-Devices` was configured as a dynamic device group and ready for Autopilot profile targeting.

![Autopilot dynamic device group rule](../screenshots/sanitized/identity-and-groups/autopilot-device-group-dynamic-rule-sanitized.png)

![Autopilot dynamic group rule validation](../screenshots/sanitized/identity-and-groups/autopilot-device-group-rule-validation-sanitized.png)

![Autopilot device group member](../screenshots/sanitized/identity-and-groups/autopilot-device-group-member-sanitized.png)

---

### Step 3 — Collected the hardware hash

Opened Command Prompt from OOBE using `Shift + F10`, then launched PowerShell and ran the following:

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
New-Item -Type Directory -Path "C:\HWID"
Set-Location -Path "C:\HWID"
$env:Path += ";C:\Program Files\WindowsPowerShell\Scripts"
Set-ExecutionPolicy -Scope Process -ExecutionPolicy RemoteSigned -Force
Install-Script -Name Get-WindowsAutopilotInfo -Force
Get-WindowsAutopilotInfo -OutputFile AutopilotHWID.csv
```

The hardware hash CSV was saved to `C:\HWID\AutopilotHWID.csv`.

> [!IMPORTANT]
> The hardware hash CSV was not uploaded to GitHub. Hardware hashes and serial numbers must never be committed to a public repository.

---

### Step 4 — Imported the hardware hash CSV

Navigated to:

```text
Devices -> Windows -> Device onboarding -> Enrollment -> Windows Autopilot -> Devices -> Import
```

After import and sync, the device appeared in the Windows Autopilot devices list.

| Item | Result |
|---|---|
| Hardware hash imported | Successful |
| Device appeared in Autopilot devices | Successful |
| Manufacturer | Lenovo |
| Initial profile status | Not assigned |
| Final profile status | Assigned |

![Autopilot CSV import](../screenshots/sanitized/device-enrollment/autopilot-device-csv-import-sanitized.png)

![Autopilot device imported](../screenshots/sanitized/device-enrollment/autopilot-device-imported-sanitized.png)

---

### Step 5 — Created and assigned the deployment profile

Created the `APUserDrivenEntraJoinPilot` profile with the settings in the design table above and assigned it to `GRP-Autopilot-Devices`. After group membership processed, the device profile status changed from `Not assigned` to `Assigned`.

![Autopilot profile basics](../screenshots/sanitized/device-enrollment/autopilot-profile-basics-sanitized.png)

![Autopilot OOBE settings](../screenshots/sanitized/device-enrollment/autopilot-profile-oobe-settings-sanitized.png)

![Autopilot profile created](../screenshots/sanitized/device-enrollment/autopilot-profile-created-sanitized.png)

![Autopilot profile assignment](../screenshots/sanitized/device-enrollment/autopilot-profile-assignment-sanitized.png)

![Autopilot profile assigned to device](../screenshots/sanitized/device-enrollment/autopilot-profile-assigned-sanitized.png)

---

### Step 6 — Completed OOBE enrollment

With the profile showing `Assigned`, the device was restarted into OOBE. user01 signed in with the lab Microsoft Entra ID account. The device joined Microsoft Entra ID, enrolled into Intune, and reached the Windows desktop. Apps and policies began processing.

> [!NOTE]
> The OOBE sign-in screen was not captured during this lab run. Enrollment success was confirmed through Intune device records, ownership status, compliance status, and app installation results.

---

### Step 7 — Verified the enrolled device in Intune

Navigated to:

```text
Devices -> Windows -> Windows devices
```

| Field | Result |
|---|---|
| Device name | WINAUTO452 |
| Managed by | Intune |
| Ownership | Corporate |
| Compliance | Compliant |
| Primary user | user01 |

![Autopilot device overview](../screenshots/sanitized/device-enrollment/autopilot-device-overview-sanitized.png)

---

### Step 8 — Verified post-enrollment app deployment

| App | Assignment type | Result |
|---|---|---|
| Company Portal | Required | Installed |
| VLC UWP | Required | Installed |
| Slack | Required | Installed |
| 7-Zip | Required Win32 | Installed |
| Microsoft 365 Apps | Required | Installed |
| ChatGPT | Available | Available in Company Portal |
| WhatsApp | Available | Available in Company Portal |

---

## Final Test Result

| Validation item | Result |
|---|---|
| Automatic MDM enrollment confirmed | Completed |
| Microsoft Entra device join settings confirmed | Completed |
| Hardware hash collected and imported | Completed |
| Device appeared in Autopilot devices list | Completed |
| Deployment profile created and assigned | Completed |
| Profile status changed to Assigned | Completed |
| user01 completed OOBE sign-in | Completed |
| Device joined Microsoft Entra ID | Completed |
| Device enrolled into Intune | Completed |
| Device appeared as WINAUTO452 | Completed |
| Ownership showed Corporate | Completed |
| Compliance showed Compliant | Completed |
| Required apps deployed after Autopilot | Completed |

---

## Troubleshooting Notes

**Profile status stays Not assigned** — confirm the device is a member of `GRP-Autopilot-Devices`, the profile is assigned to that group, and the Autopilot devices list has been synced. Dynamic group membership can take several minutes to process.

**Device not appearing in dynamic group** — confirm the dynamic rule syntax is correct, the device exists in Windows Autopilot devices, and enough time has passed for Microsoft Entra ID group processing to complete.

**Profile assignment takes time** — click Sync, wait 5–15 minutes, and refresh the Autopilot devices page. Assignment processing is not instant.

**OOBE does not show organization setup** — confirm the device has internet access, the hardware hash was imported successfully, the profile status showed `Assigned` before OOBE started, and the device was not already set up before the profile was assigned.

**Device not appearing in Intune after OOBE** — confirm user01 has an Intune license, is in scope for automatic MDM enrollment, and that enrollment restrictions allow Windows enrollment. Confirm the device has internet access and completed OOBE without errors.

**Apps showing Waiting for install** — this is normal shortly after enrollment while Intune reporting catches up. Wait a few minutes, refresh the managed apps page, and confirm apps are installed locally via Company Portal.

---

## Enterprise Reflection

Windows Autopilot reduces the need for traditional imaging and manual device preparation. A production-ready design should include clear device naming standards, separate pilot and production Autopilot groups, required security policies assigned early in enrollment, and a documented troubleshooting process for assignment, OOBE, and app delivery issues.

The pilot-first model used here — validating on a single test device before expanding — is the recommended approach before rolling Autopilot out to the broader organization.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Provides user01 and GRP-Autopilot-Devices |
| `05-application-deployment/microsoft-store-app-deployment.md` | Required Store apps validated after Autopilot enrollment |
| `05-application-deployment/win32-app-deployment-7zip.md` | Required Win32 app validated after Autopilot enrollment |
| `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Microsoft 365 Apps deployment validated after Autopilot enrollment |

---

## Key Learning Outcomes

- How to collect and import a Windows Autopilot hardware hash
- How to create and configure a user-driven Autopilot deployment profile
- How dynamic device groups target Autopilot profiles to imported devices
- How to validate corporate ownership, compliance, and app deployment after Autopilot enrollment
- Why Autopilot profile assignment status must show Assigned before OOBE begins
