# BitLocker Encryption Policy

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Endpoint security |
| Policy name | WIN-Autopilot-BitLocker-Encryption-Policy |
| Policy type | Disk encryption — BitLocker |
| Assignment group | GRP-Autopilot-Devices |
| Validation device | WINAUTO452 |
| Final encryption status | Fully Encrypted — Protection On |

---

## Lab Objective

Create a BitLocker disk encryption policy in Microsoft Intune, assign it to the Autopilot device group, and validate that WINAUTO452 transitions from fully decrypted to fully encrypted using `manage-bde -status` before and after the policy applies.

---

## Why This Lab Matters

BitLocker protects data at rest — if a corporate laptop is lost or stolen, an encrypted drive is unreadable without the recovery key. This lab proves that Intune can silently enable BitLocker on an Autopilot-enrolled corporate device and that the local endpoint confirms the encryption state.

> [!IMPORTANT]
> BitLocker changes disk encryption state. In production, confirm recovery key storage, TPM readiness, and device compatibility before assigning broadly.

---

## Prerequisites

- WINAUTO452 enrolled via Autopilot and member of GRP-Autopilot-Devices
- Device has TPM available
- Device uses UEFI with Secure Boot enabled
- Endpoint security policy permissions available in Intune

---

## BitLocker Settings Configured

### General settings

| Setting | Value |
|---|---|
| Require Device Encryption | Enabled |
| Allow Warning For Other Disk Encryption | Disabled |
| Allow Standard User Encryption | Enabled |
| Configure Recovery Password Rotation | Refresh on for Microsoft Entra ID-joined devices |

### OS drive recovery settings

| Setting | Value |
|---|---|
| Choose how BitLocker-protected OS drives can be recovered | Enabled |
| Omit recovery options from BitLocker setup wizard | True |
| Allow data recovery agent | False |
| Do not enable BitLocker until recovery information is stored | True |
| Save BitLocker recovery information | True |
| Storage of BitLocker recovery information | Store recovery passwords only |
| User storage of BitLocker recovery information | Require 48-digit recovery password |
| 256-bit recovery key | Do not allow |

All other settings (drive encryption method, fixed/removable data drives, OS drive PIN/password, pre-boot recovery message) were left Not configured.

---

## Configuration Flow

```text
Check manage-bde status before policy
-> Create BitLocker disk encryption policy
-> Configure encryption and recovery settings
-> Assign to GRP-Autopilot-Devices
-> Sync WINAUTO452
-> Verify Intune policy success
-> Run manage-bde status after policy
-> Confirm Fully Encrypted and Protection On
```

---

## Steps Performed

### Step 1 — Captured BitLocker status before policy

Ran `manage-bde -status` on WINAUTO452 as a baseline before applying the policy.

| Field | Before policy |
|---|---|
| Conversion status | Fully Decrypted |
| Percentage encrypted | 0.0% |
| Encryption method | None |
| Protection status | Protection Off |
| Key protectors | None Found |

![BitLocker before manage-bde status](../screenshots/sanitized/endpoint-security/bitlocker-before-manage-bde-status-sanitized.png)

---

### Step 2 — Created and configured the BitLocker policy

Navigated to:

```text
Endpoint security -> Disk encryption -> Create Policy
```

Selected Windows platform and BitLocker profile. Named the policy `WIN-Autopilot-BitLocker-Encryption-Policy` and configured the settings in the tables above.

![BitLocker profile creation](../screenshots/sanitized/endpoint-security/bitlocker-profile-create-sanitized.png)

![BitLocker policy basics](../screenshots/sanitized/endpoint-security/bitlocker-policy-basics-sanitized.png)

![BitLocker policy settings](../screenshots/sanitized/endpoint-security/bitlocker-policy-settings-sanitized.png)

---

### Step 3 — Assigned to GRP-Autopilot-Devices

![BitLocker policy assignment](../screenshots/sanitized/endpoint-security/bitlocker-policy-assignment-autopilot-devices-sanitized.png)

---

### Step 4 — Verified policy success and confirmed encryption

After device sync, the Intune device status showed Success for WINAUTO452. Ran `manage-bde -status` again to confirm local encryption state.

| Field | After policy |
|---|---|
| BitLocker version | 2.0 |
| Conversion status | Fully Encrypted |
| Percentage encrypted | 100.0% |
| Encryption method | XTS-AES 128 |
| Protection status | Protection On |
| Key protectors | Numerical Password, TPM |

![BitLocker device status success](../screenshots/sanitized/endpoint-security/bitlocker-device-status-winauto452-succeeded-sanitized.png)

![BitLocker after manage-bde status](../screenshots/sanitized/endpoint-security/bitlocker-after-manage-bde-status-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| manage-bde baseline captured (Protection Off) | Completed |
| BitLocker policy created and configured | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| Intune policy status showed Success | Completed |
| OS drive Fully Encrypted at 100.0% | Completed |
| Protection status On | Completed |
| Key protectors: Numerical Password and TPM | Completed |

---

## Troubleshooting Notes

**Policy stays Pending** — sync the device from both Windows Settings and Intune, wait for policy processing, and confirm the device is in `GRP-Autopilot-Devices` and actively checking in.

**Policy shows Success but encryption still in progress** — this is normal. BitLocker encrypts in the background. Keep the device powered on, run `manage-bde -status` periodically, and wait for the percentage to reach 100.0% and Protection status to show On.

**BitLocker does not start** — confirm the device has TPM ready, uses UEFI with Secure Boot, is Microsoft Entra joined, is Intune managed, and is in the assigned group. Also confirm no conflicting BitLocker policies exist and that recovery information storage is configured before encryption starts (covered by the `Do not enable BitLocker until recovery information is stored` setting).

> [!IMPORTANT]
> Never publish BitLocker recovery keys in screenshots, documentation, or GitHub repositories.

---

## Enterprise Reflection

BitLocker is a high-impact control — a misconfigured policy or missing recovery key can lock users out of their devices. Key production considerations:

| Area | Recommendation |
|---|---|
| Recovery keys | Confirm keys are escrowed to Microsoft Entra ID before enabling broadly |
| TPM readiness | Validate TPM availability across the device fleet |
| Pilot rollout | Test with a small Autopilot device group first |
| Help desk | Ensure support teams know the recovery process before enforcement |
| Reporting | Monitor Success, Error, and Conflict counts after rollout |

---

## Key Learning Outcomes

- How to create and configure a BitLocker disk encryption policy in Microsoft Intune
- How `manage-bde -status` validates encryption state locally before and after policy deployment
- What the key BitLocker recovery settings control and why `Do not enable BitLocker until recovery information is stored` matters
- Why TPM + Numerical Password key protectors appear together after Intune-managed BitLocker enrollment
