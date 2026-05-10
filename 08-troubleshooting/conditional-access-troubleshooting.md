# Intune Enrollment Troubleshooting

This file documents common Microsoft Intune Windows enrollment troubleshooting steps for the MD-102 lab.

## Status

Documentation template prepared / use during troubleshooting

## Objective

Create a repeatable checklist for troubleshooting Intune enrollment issues.

This guide helps troubleshoot:

- Windows OOBE enrollment failures
- Access work or school enrollment issues
- Autopilot enrollment issues
- Device not appearing in Intune
- Device not checking in
- License or MDM scope problems

## Common Symptoms

| Symptom | Possible cause |
|---|---|
| User cannot enroll device | Missing license, enrollment restriction, MDM scope issue |
| Device does not appear in Intune | Enrollment failed, sync delay, wrong account used |
| Device appears but not compliant | Compliance policy issue or evaluation delay |
| Autopilot profile not applied | Device not imported, group membership delay, profile not assigned |
| Company Portal setup stuck | Network, license, enrollment restriction, stale registration |

## Basic Troubleshooting Flow

```text
Check user license
→ Check MDM user scope
→ Check enrollment restrictions
→ Check device join state
→ Check Intune device record
→ Sync/restart device
→ Review logs
```

## Step 1: Check User License

Go to:

```text
Microsoft 365 admin center
→ Users
→ Active users
→ user01
→ Licenses and apps
```

Confirm:

- Intune license assigned
- Microsoft 365 Business Premium or equivalent assigned if needed

## Step 2: Check MDM User Scope

Go to:

```text
Microsoft Entra admin center
→ Mobility (MDM and WIP)
→ Microsoft Intune
```

Confirm MDM user scope includes the test user.

## Step 3: Check Enrollment Restrictions

Go to:

```text
Intune admin center
→ Devices
→ Enrollment
→ Enrollment device platform restrictions
```

Confirm the platform and ownership type are allowed.

## Step 4: Check Device Join State

On Windows, open Command Prompt and run:

```cmd
dsregcmd /status
```

Review:

```text
AzureAdJoined
EnterpriseJoined
DomainJoined
WorkplaceJoined
TenantName
MdmUrl
```

Do not upload screenshots that show tenant IDs or full user details.

## Step 5: Check Work or School Account

On Windows:

```text
Settings
→ Accounts
→ Access work or school
```

Confirm the correct work account is connected.

## Step 6: Check Intune Device Record

Go to:

```text
Intune admin center
→ Devices
→ Windows devices
```

Search for the device name.

Review:

- Compliance
- Ownership
- Last check-in
- Primary user
- Enrollment profile

## Step 7: Review Event Logs

On the Windows device:

```text
Event Viewer
→ Applications and Services Logs
→ Microsoft
→ Windows
→ DeviceManagement-Enterprise-Diagnostics-Provider
→ Admin
```

Look for enrollment or policy errors.

## Step 8: Sync and Retry

Try:

```text
Settings
→ Accounts
→ Access work or school
→ Info
→ Sync
```

Then restart the device if needed.

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/troubleshooting/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `intune-enrollment-license-check-sanitized.png` | Pending | Hide full email and tenant details |
| `intune-enrollment-mdm-scope-sanitized.png` | Pending | Hide tenant details |
| `intune-enrollment-restrictions-sanitized.png` | Pending | Hide tenant details |
| `intune-enrollment-dsregcmd-status-sanitized.png` | Pending | Hide tenant ID and full UPN |
| `intune-enrollment-event-log-sanitized.png` | Pending | Hide IDs and sensitive event details |

## Troubleshooting Result Template

| Item | Result |
|---|---|
| User license verified | Pending |
| MDM scope checked | Pending |
| Enrollment restrictions checked | Pending |
| Device join state checked | Pending |
| Intune device record checked | Pending |
| Event logs reviewed | Pending |
| Issue resolved | Pending |

## Current Status

Ready for future troubleshooting use.


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
