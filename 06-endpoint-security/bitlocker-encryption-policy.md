# BitLocker Encryption Policy

This file documents the BitLocker disk encryption policy lab for the MD-102 Intune virtual company project.

## Status

Completed

## Objective

Create and test a BitLocker disk encryption policy using Microsoft Intune Endpoint security.

This lab validates that:

- BitLocker can be enabled on a corporate Windows device using Intune.
- The policy can be assigned safely to a device-only pilot group.
- The Windows operating system drive can be encrypted using BitLocker.
- The device can report successful BitLocker policy deployment in Intune.
- The local device can confirm BitLocker protection using `manage-bde -status`.

## Lab Environment

| Item | Value |
|---|---|
| Test device | `WIN-CORP-001` |
| Operating system | Windows 11 |
| Management | Microsoft Intune |
| Join type | Microsoft Entra joined |
| Policy area | Endpoint security |
| Policy type | Disk encryption |
| Profile | BitLocker |
| Assignment group | `GRP-BitLocker-Pilot-Devices` |
| Assignment type | Device group |
| Policy name | `WIN-CORP-BitLocker-Encryption-Policy` |

## Why a Device Group Was Used

BitLocker encrypts the disk, so this policy was assigned to a dedicated device-only pilot group instead of a user group.

Earlier firewall testing used a user group assignment. Because `user01` was signed in on more than one device, the firewall policy applied to multiple devices. That was acceptable for firewall testing, but BitLocker should be tested more carefully.

For this lab, a dedicated group was created:

```text
GRP-BitLocker-Pilot-Devices
```

Only one device was added:

```text
WIN-CORP-001
```

This prevented accidental BitLocker encryption on other lab devices.

## Before Policy State

Before creating the Intune BitLocker policy, the local BitLocker status was checked on `WIN-CORP-001` using:

```cmd
manage-bde -status
```

Initial result:

| Item | Before policy result |
|---|---|
| BitLocker version | None |
| Conversion status | Fully Decrypted |
| Percentage encrypted | 0.0% |
| Encryption method | None |
| Protection status | Protection Off |
| Lock status | Unlocked |
| Key protectors | None Found |

This confirmed that BitLocker was not enabled before the Intune policy was applied.

## Pilot Device Group

A dedicated security group was created for the BitLocker pilot test.

| Setting | Value |
|---|---|
| Group name | `GRP-BitLocker-Pilot-Devices` |
| Group type | Security |
| Membership type | Assigned |
| Members | `WIN-CORP-001` only |
| Purpose | Safely target BitLocker to one pilot Windows device |

## Policy Details

| Setting | Value |
|---|---|
| Policy name | `WIN-CORP-BitLocker-Encryption-Policy` |
| Platform | Windows |
| Profile | BitLocker |
| Assignment | `GRP-BitLocker-Pilot-Devices` |
| Target device | `WIN-CORP-001` |
| Policy assignment result | Success |

## BitLocker Settings Configured

### General BitLocker Settings

| Setting | Configuration |
|---|---|
| Require device encryption | Enabled |
| Allow warning for other disk encryption | Disabled |
| Allow standard user encryption | Enabled |
| Configure recovery password rotation | Not configured |

### BitLocker Drive Encryption

| Setting | Configuration |
|---|---|
| Choose drive encryption method and cipher strength | Enabled |
| Operating system drive encryption method | XTS-AES 128-bit |
| Fixed data drive encryption method | XTS-AES 128-bit |
| Unique identifiers for organization | Not configured |

### Operating System Drive Settings

| Setting | Configuration |
|---|---|
| Enforce drive encryption type on operating system drives | Enabled |
| Encryption type for operating system drive | Used Space Only encryption |
| Require additional authentication at startup | Disabled |
| Minimum startup PIN length | Not configured |
| Enhanced PINs for startup | Not configured |
| Pre-boot keyboard input on slates | Not configured |
| Operating system drive recovery options | Enabled |
| Omit recovery options from BitLocker setup wizard | True |
| Allow data recovery agent | False |
| 256-bit recovery key | Do not allow |
| 48-digit recovery password | Allow |
| Configure pre-boot recovery message and URL | Not configured |

> [!NOTE]
> The policy was configured and validated for the operating system drive on `WIN-CORP-001`. The final device-side validation confirmed that the OS drive was encrypted with BitLocker.

## Steps Performed

### Step 1: Checked BitLocker Status Before Policy

On `WIN-CORP-001`, Command Prompt was opened as Administrator and the following command was run:

```cmd
manage-bde -status
```

The device showed BitLocker was not enabled.

### Step 2: Created BitLocker Pilot Device Group

A dedicated security group was created:

```text
GRP-BitLocker-Pilot-Devices
```

Only `WIN-CORP-001` was added as a member.

### Step 3: Created BitLocker Disk Encryption Policy

Navigation used:

```text
Intune admin center
→ Endpoint security
→ Disk encryption
→ Create Policy
```

Selections:

```text
Platform: Windows
Profile: BitLocker
```

Policy name:

```text
WIN-CORP-BitLocker-Encryption-Policy
```

### Step 4: Configured BitLocker Settings

The policy was configured to require device encryption and use BitLocker for the Windows operating system drive.

The operating system drive was configured for:

```text
Used Space Only encryption
XTS-AES 128-bit
TPM-based startup without additional PIN requirement
```

### Step 5: Assigned Policy to Device Group

The policy was assigned to:

```text
GRP-BitLocker-Pilot-Devices
```

The group contained only:

```text
WIN-CORP-001
```

### Step 6: Verified Policy Deployment in Intune

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
WIN-CORP-001
```

### Step 7: Verified BitLocker Status on the Device

After the policy applied, the following command was run again on `WIN-CORP-001`:

```cmd
manage-bde -status
```

Final result:

| Item | After policy result |
|---|---|
| BitLocker version | 2.0 |
| Conversion status | Used Space Only Encrypted |
| Percentage encrypted | 100.0% |
| Encryption method | XTS-AES 128 |
| Protection status | Protection On |
| Lock status | Unlocked |
| Key protectors | Numerical Password, TPM |

This confirmed that BitLocker was successfully enabled on the operating system drive.

## Test Result

| Test item | Result |
|---|---|
| BitLocker status checked before policy | Completed |
| Pilot device group created | Completed |
| Only `WIN-CORP-001` added to BitLocker pilot group | Completed |
| BitLocker policy created | Completed |
| Policy assigned to device group | Completed |
| Intune assignment status | Success |
| Device encryption status after policy | Used Space Only Encrypted |
| Percentage encrypted | 100.0% |
| Protection status | Protection On |
| Key protectors present | Numerical Password, TPM |

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/endpoint-security/
```

### BitLocker status before policy

![BitLocker before policy manage-bde status](../../screenshots/sanitized/endpoint-security/bitlocker-before-policy-manage-bde-status-sanitized.png)

### BitLocker pilot device group membership

![BitLocker pilot device group membership](../../screenshots/sanitized/endpoint-security/bitlocker-pilot-device-group-membership-sanitized.png)

### BitLocker policy settings

![BitLocker policy settings](../../screenshots/sanitized/endpoint-security/bitlocker-policy-settings-sanitized.png)

### BitLocker policy assignment

![BitLocker policy assignment](../../screenshots/sanitized/endpoint-security/bitlocker-policy-assignment-sanitized.png)

### BitLocker policy review and create

![BitLocker policy review and create](../../screenshots/sanitized/endpoint-security/bitlocker-policy-review-create-sanitized.png)

### BitLocker policy device status success

![BitLocker policy device status success](../../screenshots/sanitized/endpoint-security/bitlocker-policy-device-status-success-sanitized.png)

### BitLocker status after policy

![BitLocker after policy manage-bde status](../../screenshots/sanitized/endpoint-security/bitlocker-after-policy-manage-bde-status-sanitized.png)

## Screenshot Files

```text
bitlocker-before-policy-manage-bde-status-sanitized.png
bitlocker-pilot-device-group-membership-sanitized.png
bitlocker-policy-settings-sanitized.png
bitlocker-policy-assignment-sanitized.png
bitlocker-policy-review-create-sanitized.png
bitlocker-policy-device-status-success-sanitized.png
bitlocker-after-policy-manage-bde-status-sanitized.png
```

## Security and Privacy Notes

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

For this lab, screenshots should hide:

- Top-right admin account details
- Tenant/domain details
- Object IDs
- Device IDs
- Intune device IDs
- Microsoft Entra device IDs
- Full user email addresses
- Any visible BitLocker recovery key values

## Troubleshooting Notes

### Policy shows success but drive is not encrypted yet

If Intune shows policy success but the device is not encrypted yet:

1. Sync the device from Windows settings.
2. Restart the device.
3. Wait for Intune policy processing.
4. Run `manage-bde -status` again.
5. Check Event Viewer BitLocker logs if needed.

### BitLocker does not start

Check:

- Device has TPM available and ready.
- Device is Microsoft Entra joined / Intune managed.
- Device is included in the assigned device group.
- Policy assignment status is not showing error or conflict.
- No conflicting BitLocker policies exist.

### Recovery key safety

Before using BitLocker in production, always verify that BitLocker recovery information is backed up to the appropriate cloud or directory location before relying on encryption at scale.

## What This Lab Proves

This lab proves that Microsoft Intune can enable and manage BitLocker encryption on a corporate Windows device.

Simple flow:

```text
BitLocker initially off
→ Dedicated pilot device group created
→ WIN-CORP-001 added to pilot group
→ BitLocker policy created in Intune
→ Policy assigned to pilot device group
→ WIN-CORP-001 receives policy successfully
→ OS drive becomes BitLocker encrypted
→ manage-bde confirms Protection On
```

## Current Lab Status

Completed:

- BitLocker before-policy status captured
- BitLocker pilot device group created
- `WIN-CORP-001` added as the only test device
- BitLocker disk encryption policy created
- Policy assigned to the pilot device group
- Policy deployment status showed Success for `WIN-CORP-001`
- Device-side BitLocker status confirmed 100% encrypted
- Protection status confirmed as On
- TPM and Numerical Password key protectors confirmed

Optional follow-up:

- Capture a recovery key escrow screenshot from Intune or Microsoft Entra ID without exposing the actual recovery key.

## Next Step

Continue to the next endpoint security lab:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Suggested next endpoint security sequence:

```text
Attack Surface Reduction policy
Windows Security Baseline
Remote actions and monitoring
```
