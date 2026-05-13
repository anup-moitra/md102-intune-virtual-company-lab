# Windows Basic Configuration Profile

## Lab status

**Status:** Completed  
**Lab area:** Configuration profiles  
**Platform:** Windows 10 and later  
**Profile type:** Settings catalog  
**Profile name:** `CFG-WIN-Basic-Device-Settings`  
**Assignment group:** `GRP-Pilot-Users`  
**Validated devices:** `WIN-CORP-001`, `WINAUTO452`

---

## Lab objective

The goal of this lab was to create a basic Windows configuration profile in Microsoft Intune using the Settings catalog.

The profile was used to configure basic device lock behavior on Windows endpoints. This demonstrates how Intune can centrally manage Windows device settings without using traditional on-premises Group Policy.

---

## Why this lab matters

In a real organization, administrators need to apply standard Windows settings across managed endpoints.

Examples include:

- Requiring a device password
- Locking inactive devices
- Applying security-related device settings
- Standardizing configuration across corporate Windows devices

Traditionally, many of these settings were configured using Group Policy Objects in Active Directory. In a modern cloud-managed environment, Microsoft Intune configuration profiles are used to deliver similar policy settings to Entra joined and Intune-managed devices.

---

## Lab environment

| Item | Value |
|---|---|
| Admin portal | Microsoft Intune admin center |
| Platform | Windows 10 and later |
| Profile type | Settings catalog |
| Profile name | `CFG-WIN-Basic-Device-Settings` |
| Assignment group | `GRP-Pilot-Users` |
| Target users/devices | Pilot Windows users and their enrolled devices |
| Validated devices | `WIN-CORP-001`, `WINAUTO452` |
| Final result | Policy applied successfully |

---

## Configuration summary

| Setting category | Setting | Configured value |
|---|---|---|
| Device Lock | Device Password Enabled | Enabled |
| Device Lock | Max Inactivity Time Device Lock | `5` |

For this lab, the inactivity lock value was set to `5` to allow quick testing. After sync and reboot, both Windows endpoints locked automatically after approximately 5 minutes of inactivity.

---

## Screenshot evidence

Screenshots for this lab are stored in:

```text
screenshots/sanitized/configuration-profiles/
```

| Screenshot | Purpose |
|---|---|
| `windows-basic-config-profile-create-profile-sanitized.png` | Shows the Windows Settings catalog profile type selection |
| `windows-basic-config-profile-basics-sanitized.png` | Shows the profile name and description |
| `windows-basic-config-profile-settings-configured-sanitized.png` | Shows the configured Device Lock settings |
| `windows-basic-config-profile-assignment-sanitized.png` | Shows assignment to `GRP-Pilot-Users` |
| `windows-basic-config-profile-device-status-success-sanitized.png` | Shows successful policy deployment to Windows devices |

---

## Step 1: Create a new Windows configuration profile

Path used:

```text
Microsoft Intune admin center
> Devices
> Windows
> Configuration
> Create
> New policy
```

The following options were selected:

| Field | Value |
|---|---|
| Platform | Windows 10 and later |
| Profile type | Settings catalog |

Screenshot:

![Windows basic configuration profile type](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-create-profile-sanitized.png)

---

## Step 2: Configure profile basics

The profile was created with the following name and description:

```text
Name:
CFG-WIN-Basic-Device-Settings
```

```text
Description:
Configures basic Windows device lock settings for corporate pilot devices.
```

Screenshot:

![Windows basic configuration profile basics](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-basics-sanitized.png)

---

## Step 3: Configure Device Lock settings

The Settings catalog was used to configure the Device Lock category.

Configured settings:

| Setting | Value |
|---|---|
| Device Password Enabled | Enabled |
| Max Inactivity Time Device Lock | `5` |

This setting was used to validate that Intune could apply a basic Windows device lock configuration to managed endpoints.

Screenshot:

![Windows basic configuration profile settings](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-settings-configured-sanitized.png)

---

## Step 4: Assign the profile

The profile was assigned to the pilot user group:

```text
GRP-Pilot-Users
```

This user-targeted assignment allowed the configuration profile to apply to enrolled Windows devices used by the pilot user.

Screenshot:

![Windows basic configuration profile assignment](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-assignment-sanitized.png)

---

## Step 5: Sync Windows endpoints

After the policy was created, Windows endpoints were synced with Intune.

Sync can be triggered from either Intune or the local Windows device.

### Intune sync path

```text
Microsoft Intune admin center
> Devices
> Windows
> Windows devices
> Select device
> Sync
```

### Local Windows sync path

```text
Settings
> Accounts
> Access work or school
> Connected work or school account
> Info
> Sync
```

The devices were rebooted after sync because the lock behavior did not apply during the first validation attempt.

---

## Step 6: Validate Intune deployment status

Path used:

```text
Microsoft Intune admin center
> Devices
> Windows
> Configuration
> CFG-WIN-Basic-Device-Settings
> Device status
```

The policy deployment report showed both Windows devices with a successful assignment status.

Validated devices:

| Device | Assignment status |
|---|---|
| `WIN-CORP-001` | Success |
| `WINAUTO452` | Success |

Screenshot:

![Windows basic configuration profile device status success](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-device-status-success-sanitized.png)

---

## Step 7: Validate endpoint behavior

After Intune reported success, the policy was tested on the Windows endpoints.

Initial testing did not immediately lock the endpoints after the configured inactivity period. After rebooting the machines, the setting applied successfully.

Final endpoint validation:

| Device | Validation result |
|---|---|
| `WIN-CORP-001` | Locked automatically after approximately 5 minutes |
| `WINAUTO452` | Locked automatically after approximately 5 minutes |

This confirmed that the configuration profile was successfully applied and enforced on the endpoints.

---

## Troubleshooting note

During testing, Intune showed the profile assignment as successful, but the endpoint did not immediately lock during the first test.

After rebooting the Windows devices, both endpoints locked automatically after the configured inactivity period.

This is an important real-world observation:

```text
Intune policy success confirms policy delivery, but some endpoint behaviors may require a reboot or new sign-in session before the setting is fully enforced.
```

---

## Final validation checklist

| Validation item | Status |
|---|---|
| Windows Settings catalog profile created | Completed |
| Device Lock settings configured | Completed |
| Profile assigned to pilot users | Completed |
| Devices synced with Intune | Completed |
| Device status showed Success | Completed |
| Endpoint behavior tested | Completed |
| Devices locked after configured inactivity period | Completed |

---

## Result summary

The Windows basic configuration profile was successfully created and deployed using Microsoft Intune.

The profile configured basic Device Lock settings and was assigned to the pilot user group. After device sync and reboot, both Windows endpoints reported successful policy deployment and locked automatically after approximately 5 minutes of inactivity.

---

## Key learning points

- Settings catalog profiles are used to configure Windows settings from Intune.
- Intune configuration profiles are a modern cloud-based alternative to many traditional Group Policy settings.
- User-targeted policies can apply to enrolled devices used by the assigned user.
- A policy may show success in Intune before the endpoint behavior is visible.
- Some settings may require a reboot or new sign-in session before validation is successful.

---

## Related labs

- `02-device-enrollment/windows-autopilot-user-driven-enrollment.md`
- `02-device-enrollment/windows-byod-enrollment.md`
- `06-endpoint-security/windows-defender-antivirus-policy.md`
- `06-endpoint-security/windows-firewall-policy.md`
- `06-endpoint-security/bitlocker-encryption-policy.md`

---

## Microsoft Learn references

- [Create a device configuration profile in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/configuration/device-profile-create)
- [Use the Settings catalog to configure settings on Windows devices](https://learn.microsoft.com/en-us/intune/intune-service/configuration/settings-catalog)
- [Device configuration profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/configuration/device-profiles)
