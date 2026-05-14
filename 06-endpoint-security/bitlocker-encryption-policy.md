# BitLocker Encryption Policy

## Lab status

**Status:** Completed  
**Lab category:** Endpoint security  
**Platform:** Windows  
**Management platform:** Microsoft Intune  
**Policy area:** Endpoint security  
**Policy type:** Disk encryption  
**Profile:** BitLocker  
**Assignment group:** GRP-Autopilot-Devices  
**Validation device:** WINAUTO452  
**Enrollment method:** Windows Autopilot user-driven enrollment  
**Final result:** Operating system drive fully encrypted and protected by BitLocker  

---

## Lab objective

The objective of this lab is to create, assign, and validate a BitLocker disk encryption policy using Microsoft Intune Endpoint security.

This lab validates that:

- BitLocker can be enabled from Microsoft Intune.
- A disk encryption policy can be assigned to Windows Autopilot devices.
- The Autopilot-enrolled device `WINAUTO452` can receive the BitLocker policy successfully.
- The Windows operating system drive can be encrypted with BitLocker.
- Intune can report successful policy assignment status.
- Local device-side encryption status can be verified using `manage-bde -status`.
- BitLocker protection can use TPM and a numerical recovery password protector.

---

## Why this lab matters

BitLocker protects data on Windows devices by encrypting the disk.

In a real organization, BitLocker helps protect company data if a laptop is lost, stolen, or accessed without authorization.

This lab proves that Microsoft Intune can enable BitLocker encryption on a Windows Autopilot-enrolled corporate device and that the local endpoint confirms encryption status.

Simple flow:

```text
BitLocker initially off
-> BitLocker policy created in Intune
-> Policy assigned to GRP-Autopilot-Devices
-> WINAUTO452 receives policy successfully
-> OS drive becomes BitLocker encrypted
-> manage-bde confirms Fully Encrypted and Protection On
```

---

## Lab environment

| Item | Value |
|---|---|
| Test device | WINAUTO452 |
| Device source | Windows Autopilot user-driven enrollment |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Join type | Microsoft Entra joined |
| Ownership | Corporate |
| Policy area | Endpoint security |
| Policy type | Disk encryption |
| Profile | BitLocker |
| Assignment group | GRP-Autopilot-Devices |
| Assignment type | Device group |
| Policy name | WIN-Autopilot-BitLocker-Encryption-Policy |
| Screenshot folder | screenshots/sanitized/endpoint-security/ |
| Final policy status | Success |
| Final encryption status | Fully Encrypted |

---

## Prerequisites

Before starting this lab, the following were required:

- Microsoft Intune tenant available.
- Windows Autopilot device enrolled.
- `WINAUTO452` available in Intune.
- `WINAUTO452` included in `GRP-Autopilot-Devices`.
- Device able to sync with Intune.
- Endpoint security policy permissions available in Intune.
- Device had TPM available and ready.
- Device used a supported Windows edition.
- Recovery key storage behavior understood before broad rollout.
- Sanitized screenshots prepared for GitHub documentation.

> [!IMPORTANT]
> BitLocker changes the disk encryption state. In production, do not broadly assign BitLocker until recovery key storage, device readiness, TPM support, and rollback/recovery processes are understood and tested.

---

## Policy design

This lab targeted the existing Autopilot device group:

```text
GRP-Autopilot-Devices
```

The group contained one Autopilot-enrolled validation device:

```text
WINAUTO452
```

This assignment model proves a realistic enterprise flow:

```text
Windows Autopilot device
-> Microsoft Entra joined
-> Intune managed
-> Endpoint security policies applied
-> BitLocker encryption enabled
```

### Policy details

| Setting | Value |
|---|---|
| Policy name | WIN-Autopilot-BitLocker-Encryption-Policy |
| Platform | Windows |
| Profile | BitLocker |
| Policy location | Endpoint security > Disk encryption |
| Assignment | GRP-Autopilot-Devices |
| Validation device | WINAUTO452 |
| Final Intune assignment result | Success |

---

## Before policy state

Before the Intune BitLocker policy was applied, local BitLocker status was checked on `WINAUTO452` using Command Prompt as Administrator.

Command used:

```cmd
hostname
manage-bde -status
```

Initial result:

| Item | Before policy result |
|---|---|
| Device name | WINAUTO452 |
| BitLocker version | None |
| Conversion status | Fully Decrypted |
| Percentage encrypted | 0.0% |
| Encryption method | None |
| Protection status | Protection Off |
| Lock status | Unlocked |
| Key protectors | None Found |

This confirmed that BitLocker was not enabled before the Intune policy was applied.

---

## BitLocker settings configured

### General BitLocker settings

| Setting | Configuration |
|---|---|
| Require Device Encryption | Enabled |
| Allow Warning For Other Disk Encryption | Disabled |
| Allow Standard User Encryption | Enabled |
| Configure Recovery Password Rotation | Refresh on for Microsoft Entra ID-joined devices |

### BitLocker drive encryption settings

| Setting | Configuration |
|---|---|
| Choose drive encryption method and cipher strength | Not configured |
| Provide unique identifiers for your organization | Not configured |

### Operating system drive settings

| Setting | Configuration |
|---|---|
| Enforce drive encryption type on operating system drives | Not configured |
| Require additional authentication at startup | Not configured |
| Configure minimum PIN length for startup | Not configured |
| Allow enhanced PINs for startup | Not configured |
| Disallow standard users from changing the PIN or password | Not configured |
| Choose how BitLocker-protected operating system drives can be recovered | Enabled |
| Omit recovery options from the BitLocker setup wizard | True |
| Allow data recovery agent | False |
| Do not enable BitLocker until recovery information is stored | True |
| Save BitLocker recovery information | True |
| 256-bit recovery key | Do not allow |
| Storage of BitLocker recovery information | Store recovery passwords only |
| User storage of BitLocker recovery information | Require 48-digit recovery password |
| Configure pre-boot recovery message and URL | Not configured |

### Fixed and removable data drive settings

| Setting | Configuration |
|---|---|
| Fixed data drive encryption type | Not configured |
| Fixed data drive recovery options | Not configured |
| Deny write access to fixed drives not protected by BitLocker | Not configured |
| Removable data drive settings | Not configured |

---

## Configuration flow

```text
Check BitLocker status before policy
-> Create BitLocker disk encryption policy
-> Configure policy basics
-> Configure BitLocker encryption and recovery settings
-> Assign policy to GRP-Autopilot-Devices
-> Sync WINAUTO452
-> Validate Intune policy success
-> Run manage-bde -status after policy
-> Confirm drive is Fully Encrypted and Protection On
```

---

## Steps performed

### Step 1 - Checked BitLocker status before policy

On `WINAUTO452`, Command Prompt was opened as Administrator and the following command was run:

```cmd
manage-bde -status
```

The device showed:

```text
Conversion Status: Fully Decrypted
Percentage Encrypted: 0.0%
Protection Status: Protection Off
Key Protectors: None Found
```

---

### Step 2 - Created the BitLocker policy

Navigation used:

```text
Intune admin center
-> Endpoint security
-> Disk encryption
-> Create Policy
```

Profile selections:

```text
Platform: Windows
Profile: BitLocker
```

---

### Step 3 - Configured policy basics

Policy name:

```text
WIN-Autopilot-BitLocker-Encryption-Policy
```

Description:

```text
BitLocker disk encryption policy for MD-102 Intune lab testing on Windows Autopilot devices.
```

---

### Step 4 - Configured BitLocker settings

The policy was configured to silently enable BitLocker for the Autopilot device.

Key settings:

```text
Require Device Encryption = Enabled
Allow Warning For Other Disk Encryption = Disabled
Allow Standard User Encryption = Enabled
Configure Recovery Password Rotation = Refresh on for Entra ID-joined devices
```

Recovery configuration was also configured to use a required 48-digit recovery password and store recovery passwords only.

---

### Step 5 - Assigned policy to the Autopilot device group

The policy was assigned to:

```text
GRP-Autopilot-Devices
```

This group contained the validation device:

```text
WINAUTO452
```

---

### Step 6 - Synced the device

The device was synced from Windows and Intune policy processing was allowed to complete.

---

### Step 7 - Verified Intune policy deployment status

The BitLocker policy deployment report showed:

| Status | Count |
|---|---:|
| Success | 1 |
| Pending | 0 |
| Error | 0 |
| Conflict | 0 |
| Not applicable | 0 |
| Total | 1 |

The successful device was:

```text
WINAUTO452
```

---

### Step 8 - Verified BitLocker status after policy

After the policy applied, the following command was run again on `WINAUTO452`:

```cmd
manage-bde -status
```

Final result:

| Item | After policy result |
|---|---|
| Device name | WINAUTO452 |
| BitLocker version | 2.0 |
| Conversion status | Fully Encrypted |
| Percentage encrypted | 100.0% |
| Encryption method | XTS-AES 128 |
| Protection status | Protection On |
| Lock status | Unlocked |
| Identification field | Unknown |
| Key protectors | Numerical Password, TPM |

This confirmed that the operating system drive was fully encrypted and protected by BitLocker.

---

## Validation

### Before-state validation

Validation confirmed that:

- The device was named `WINAUTO452`.
- BitLocker was initially off.
- The operating system drive was fully decrypted.
- Protection status was off.
- No key protectors were present.

---

### Policy validation

Validation confirmed that:

- The BitLocker profile was selected.
- The policy basics were configured.
- Silent encryption-related settings were configured.
- Recovery password settings were configured.
- The policy was assigned to `GRP-Autopilot-Devices`.

---

### Intune status validation

Validation confirmed that:

- `WINAUTO452` received the policy.
- Intune reported the policy status as Success.
- There were no pending, error, conflict, or not applicable results.

---

### Endpoint encryption validation

Validation confirmed that:

- The OS drive became fully encrypted.
- Encryption reached 100.0%.
- Protection status changed to Protection On.
- TPM and Numerical Password key protectors were present.

---

## Final test result

| Validation item | Status |
|---|---|
| Before-policy `manage-bde -status` captured | Completed |
| BitLocker policy profile selected | Completed |
| BitLocker policy basics configured | Completed |
| BitLocker settings configured | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| Intune policy status checked | Success |
| Validation device | WINAUTO452 |
| Final encryption status | Fully Encrypted |
| Percentage encrypted | 100.0% |
| Encryption method | XTS-AES 128 |
| Protection status | Protection On |
| Key protectors present | Numerical Password, TPM |
| Screenshots captured and uploaded | Completed |
| Final lab result | Completed |

Observed final result:

```text
BitLocker was enabled successfully on WINAUTO452.
The operating system drive showed Fully Encrypted, 100.0% encrypted, and Protection On.
```

---

## Screenshots captured

Screenshots are stored in:

```text
screenshots/sanitized/endpoint-security/
```

### BitLocker status before policy

![BitLocker before manage-bde status](../screenshots/sanitized/endpoint-security/bitlocker-before-manage-bde-status-sanitized.png)

### BitLocker profile creation

![BitLocker profile creation](../screenshots/sanitized/endpoint-security/bitlocker-profile-create-sanitized.png)

### BitLocker policy basics

![BitLocker policy basics](../screenshots/sanitized/endpoint-security/bitlocker-policy-basics-sanitized.png)

### BitLocker policy settings

![BitLocker policy settings](../screenshots/sanitized/endpoint-security/bitlocker-policy-settings-sanitized.png)

### BitLocker policy assignment to Autopilot devices

![BitLocker policy assignment to Autopilot devices](../screenshots/sanitized/endpoint-security/bitlocker-policy-assignment-autopilot-devices-sanitized.png)

### BitLocker policy device status success

![BitLocker device status success](../screenshots/sanitized/endpoint-security/bitlocker-device-status-winauto452-succeeded-sanitized.png)

### BitLocker status after policy

![BitLocker after manage-bde status](../screenshots/sanitized/endpoint-security/bitlocker-after-manage-bde-status-sanitized.png)

---

## Screenshot file list

```text
bitlocker-before-manage-bde-status-sanitized.png
bitlocker-profile-create-sanitized.png
bitlocker-policy-basics-sanitized.png
bitlocker-policy-settings-sanitized.png
bitlocker-policy-assignment-autopilot-devices-sanitized.png
bitlocker-device-status-winauto452-succeeded-sanitized.png
bitlocker-after-manage-bde-status-sanitized.png
```

---

## Troubleshooting notes

### Policy shows pending

If the BitLocker policy stays pending:

1. Sync the device from Windows settings.
2. Sync the device from Intune.
3. Wait for device policy processing.
4. Generate the assignment status report again.
5. Confirm the device is in the assigned group.
6. Confirm the device is online and checking in.

---

### Policy shows success but encryption is still in progress

If Intune shows success but local encryption is still in progress:

1. Wait for encryption to complete.
2. Keep the device powered on and connected.
3. Run `manage-bde -status` again later.
4. Confirm the percentage encrypted reaches 100.0%.
5. Confirm protection status becomes `Protection On`.

---

### BitLocker does not start

Check:

- Device has TPM available and ready.
- Device uses UEFI and Secure Boot.
- Device is Microsoft Entra joined or hybrid joined.
- Device is Intune managed.
- Device is included in the assigned group.
- No conflicting BitLocker policies exist.
- Recovery information can be stored before encryption starts.

---

## Enterprise reflection

BitLocker is a high-impact security control because it protects data at rest.

For production environments:

| Area | Recommendation |
|---|---|
| Pilot rollout | Test with a small corporate device group first |
| Recovery keys | Confirm recovery key storage before enabling broadly |
| TPM readiness | Validate TPM and device readiness |
| User impact | Plan communication and support |
| Reporting | Monitor Success, Error, Conflict, and encryption progress |
| Recovery process | Ensure help desk knows how to recover devices |
| Screenshots/logs | Never expose recovery keys in documentation |

A safe rollout model is:

```text
Pilot Autopilot devices
-> Confirm recovery key escrow
-> Confirm encryption status
-> Validate support process
-> Expand to production devices
```

This lab used `GRP-Autopilot-Devices` for a controlled test rollout.

---

## Security and privacy notes

This is a public learning repository.

Do not upload sensitive information, including:

- BitLocker recovery keys
- Tenant IDs
- Device IDs
- Object IDs
- Full real email addresses
- Serial numbers
- Internal IP addresses
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right admin account details
- Tenant/domain details
- Object IDs
- Device IDs
- Intune device IDs
- Microsoft Entra device IDs
- Full user email addresses
- Any visible BitLocker recovery key values

> [!IMPORTANT]
> Do not publish the actual 48-digit BitLocker recovery key in GitHub.

---

## Related labs

| Lab file | Relationship |
|---|---|
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Provides the Autopilot-enrolled corporate device WINAUTO452 |
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Previous endpoint security policy |
| `06-endpoint-security/windows-firewall-policy.md` | Previous endpoint security policy |
| `06-endpoint-security/attack-surface-reduction-policy.md` | Planned advanced endpoint security lab |
| `06-endpoint-security/windows-security-baseline.md` | Planned security baseline lab |
| `07-remote-actions-and-monitoring/device-monitoring-and-reports.md` | Planned future monitoring/reporting lab |

---

## Key learning outcomes

This lab demonstrated how to:

- Check BitLocker status before policy deployment.
- Create a BitLocker disk encryption policy in Intune.
- Configure silent encryption-related settings.
- Configure recovery password storage settings.
- Assign BitLocker policy to a device group.
- Validate policy success in Intune.
- Use `manage-bde -status` to confirm local encryption state.
- Confirm TPM and Numerical Password key protectors.
- Understand why recovery key privacy matters in public documentation.

---

## Lab conclusion

The BitLocker encryption policy lab was completed successfully.

Final result:

```text
Before the policy, WINAUTO452 was fully decrypted.
The BitLocker policy was created in Intune.
The policy was assigned to GRP-Autopilot-Devices.
WINAUTO452 received the policy successfully.
After policy application, the OS drive was Fully Encrypted.
Protection status was On.
TPM and Numerical Password key protectors were present.
```

This confirms that Microsoft Intune can enable and validate BitLocker disk encryption on an Autopilot-enrolled corporate Windows device.
