# Attack Surface Reduction Policy

This file documents the planned Attack Surface Reduction (ASR) policy lab for the MD-102 Intune virtual company project.

## Status

Planned / documentation template prepared / not yet tested

## Objective

Create a Microsoft Intune Attack Surface Reduction policy and test it safely in **Audit mode** before moving to enforcement.

This lab will validate that:

- ASR policy can be created from Intune Endpoint security.
- ASR rules can be configured safely for pilot testing.
- The policy can be assigned to a limited pilot device group.
- The pilot device can report policy status in Intune.
- ASR evidence can be reviewed without immediately blocking user activity.

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` |
| Platform | Windows |
| Management | Microsoft Intune |
| Join type | Microsoft Entra joined |
| Policy area | Endpoint security |
| Profile | Attack Surface Reduction Rules |
| Assignment group | `GRP-EndpointSecurity-Pilot-Devices` or existing pilot device group |
| Policy name | `WIN-CORP-ASR-Audit-Policy` |

## Important Concept

Attack Surface Reduction rules reduce common malware entry points.

Simple comparison:

```text
Defender Antivirus = detects and removes malware
Windows Firewall = controls network traffic
BitLocker = protects data on disk
Attack Surface Reduction = blocks risky behaviors malware commonly uses
```

For the first lab, use **Audit mode**.

```text
Audit mode = records what would have been blocked
Block mode = actively blocks the behavior
```

Audit mode is safer for learning because it helps identify possible impact before enforcement.

## Prerequisites

Before starting:

- `WIN-CORP-001` should be Intune managed.
- Microsoft Defender Antivirus should be active.
- Windows Firewall and BitLocker labs should already be completed.
- A device-only pilot group should be used if possible.
- Avoid assigning this first ASR policy to all users or all devices.

Recommended pilot group:

```text
GRP-EndpointSecurity-Pilot-Devices
```

If this group does not exist yet, create it and add only:

```text
WIN-CORP-001
```

## Configuration Plan

| Setting | Planned configuration |
|---|---|
| Policy name | `WIN-CORP-ASR-Audit-Policy` |
| Platform | Windows |
| Profile | Attack Surface Reduction Rules |
| Assignment | Device-only pilot group |
| Initial rule action | Audit |
| Enforcement phase | Later lab after audit review |

## Steps to Perform

### Step 1: Create or Confirm Pilot Device Group

Go to:

```text
Microsoft Intune admin center
→ Groups
→ All groups
```

Create or confirm:

```text
GRP-EndpointSecurity-Pilot-Devices
```

Add only:

```text
WIN-CORP-001
```

Do not assign the first ASR policy to:

```text
All users
All devices
GRP-Pilot-Users
```

### Step 2: Create the ASR Policy

Go to:

```text
Intune admin center
→ Endpoint security
→ Attack surface reduction
→ Create Policy
```

Select:

```text
Platform: Windows
Profile: Attack Surface Reduction Rules
```

Policy name:

```text
WIN-CORP-ASR-Audit-Policy
```

Description:

```text
Configures Microsoft Defender Attack Surface Reduction rules in audit mode for pilot testing in the MD-102 Intune lab.
```

### Step 3: Configure ASR Rules in Audit Mode

Start with audit mode for high-value rules.

Recommended initial ASR rules for audit:

| ASR rule area | Planned action |
|---|---|
| Block Office applications from creating child processes | Audit |
| Block Office applications from creating executable content | Audit |
| Block Office applications from injecting code into other processes | Audit |
| Block JavaScript or VBScript from launching downloaded executable content | Audit |
| Block executable content from email client and webmail | Audit |
| Block credential stealing from the Windows local security authority subsystem | Audit |
| Block Adobe Reader from creating child processes | Audit |
| Block persistence through WMI event subscription | Audit |

> If the Intune portal wording is slightly different, choose the matching ASR rule and set it to **Audit**.

### Step 4: Assign the Policy

Assign the policy only to:

```text
GRP-EndpointSecurity-Pilot-Devices
```

or the current pilot device-only group containing only:

```text
WIN-CORP-001
```

### Step 5: Review and Create

Review:

- Policy name
- Platform
- ASR rule actions
- Assignment group

Then select:

```text
Create
```

### Step 6: Sync the Test Device

On `WIN-CORP-001`:

```text
Settings
→ Accounts
→ Access work or school
→ Connected account
→ Info
→ Sync
```

Or from Intune:

```text
Devices
→ Windows
→ WIN-CORP-001
→ Sync
```

### Step 7: Verify Policy Status

Go to:

```text
Intune admin center
→ Endpoint security
→ Attack surface reduction
→ WIN-CORP-ASR-Audit-Policy
→ Monitor
→ Device status
```

Expected result:

```text
WIN-CORP-001 = Success / Succeeded
```

### Step 8: Check Local ASR Evidence

On `WIN-CORP-001`, review Microsoft Defender events if needed:

```text
Event Viewer
→ Applications and Services Logs
→ Microsoft
→ Windows
→ Windows Defender
→ Operational
```

For the first lab, do not intentionally run unsafe content. The goal is to prove policy deployment and document audit configuration.

## Test Result

| Test item | Result |
|---|---|
| ASR pilot device group created/confirmed | Pending |
| ASR policy created | Pending |
| ASR rules configured in Audit mode | Pending |
| Policy assigned to pilot device group | Pending |
| Device sync completed | Pending |
| Intune device status verified | Pending |
| ASR audit evidence reviewed | Pending |


## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/endpoint-security/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `asr-create-profile-sanitized.png` | Pending | Add after lab execution and sanitization |
| `asr-policy-settings-audit-mode-sanitized.png` | Pending | Add after lab execution and sanitization |
| `asr-policy-assignment-sanitized.png` | Pending | Add after lab execution and sanitization |
| `asr-policy-review-create-sanitized.png` | Pending | Add after lab execution and sanitization |
| `asr-policy-device-status-sanitized.png` | Pending | Add after lab execution and sanitization |
| `asr-event-viewer-audit-evidence-sanitized.png` | Pending | Add after lab execution and sanitization |

> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.


## Troubleshooting Notes

If the ASR policy does not apply:

1. Confirm `WIN-CORP-001` is in the assigned group.
2. Confirm the device has checked in recently.
3. Sync from Windows settings and Intune.
4. Check whether another Defender policy is causing conflict.
5. Confirm Microsoft Defender Antivirus is enabled.
6. Review device status and per-setting status in Intune.

## Current Status

Planned.

## Next Step

Perform the ASR policy lab in Audit mode. After successful audit testing, create a later advanced lab to test selected ASR rules in Block mode.


## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Real tenant IDs
- Full real email addresses
- Passwords
- MFA QR codes
- Device serial numbers
- Device IDs
- Object IDs
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Unsanitized screenshots
- Production company data

Before uploading screenshots, blur or hide:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs / object IDs / serial numbers
- Any recovery keys, tokens, or QR codes
