# Windows Basic Configuration Profile

This file documents the basic Windows configuration profile lab for the MD-102 Intune virtual company project.

## Objective

Create and test a basic Microsoft Intune configuration profile for a corporate Windows device.

This lab validates that:

- Microsoft Intune can push settings to a managed Windows device.
- A Settings catalog profile can configure Microsoft Edge startup behavior.
- WIN-CORP-001 receives the configuration profile after Intune sync.
- Microsoft Edge opens the configured startup website successfully.

## Lab Context

Configuration profiles are used to configure settings on managed devices.

In this lab, a Microsoft Edge startup setting was configured for a corporate Windows device.

Simple flow:

```text
Configuration profile = configures device settings
Compliance policy = checks whether device settings meet requirements
Conditional Access = controls access based on compliance result
```

## Profile Details

| Setting | Value |
|---|---|
| Profile name | WIN-CORP-Basic-Configuration-Profile |
| Platform | Windows 10 and later |
| Profile type | Settings catalog |
| Category | Microsoft Edge |
| Subcategory | Startup, home page and new tab page |
| Assignment | GRP-Pilot-Users |
| Test device | WIN-CORP-001 |
| Test user | user01 |
| Target browser | Microsoft Edge |

## Settings Configured

| Setting | Configuration |
|---|---|
| Action to take on startup (Device) | Open a list of URLs |
| Action to take on Microsoft Edge startup | Enabled |
| Sites to open when the browser starts | Enabled |
| Startup URL | https://anupmoitra.com/ |

## Steps Performed

1. Opened Microsoft Intune admin center.
2. Created a new Settings catalog profile.
3. Selected platform: Windows 10 and later.
4. Selected Microsoft Edge startup settings.
5. Configured startup action to open a list of URLs.
6. Configured startup URL as `https://anupmoitra.com/`.
7. Assigned the profile to GRP-Pilot-Users.
8. Synced WIN-CORP-001 with Intune.
9. Opened Microsoft Edge on WIN-CORP-001.
10. Confirmed Edge opened the configured startup website successfully.

## Test Result

| Item | Result |
|---|---|
| Test device | WIN-CORP-001 |
| Test user | user01 |
| Profile applied | Yes |
| Edge startup URL configured | Yes |
| Startup website opened | Yes |
| Result | Successful |

## What This Proves

This lab proves that Microsoft Intune can apply a Windows configuration profile to a managed corporate Windows device.

Simple explanation:

```text
WIN-CORP-Basic-Configuration-Profile was created in Intune
→ Profile was assigned to GRP-Pilot-Users
→ WIN-CORP-001 synced with Intune
→ Microsoft Edge received the startup settings
→ Edge opened https://anupmoitra.com/
```

## Screenshots

Suggested folder:

```text
screenshots/sanitized/configuration-profiles/
```

Suggested screenshots:

```text
win-corp-basic-config-profile-list-sanitized.jpg
win-corp-basic-config-profile-settings-sanitized.jpg
win-corp-basic-config-profile-assignment-sanitized.jpg
win-corp-edge-startup-page-applied-sanitized.jpg
win-corp-edge-policy-page-sanitized.jpg
```

## Troubleshooting Notes

If Microsoft Edge does not open the configured startup page immediately:

1. Sync the device again from Windows settings.
2. Close all Microsoft Edge windows.
3. End Edge background processes from Task Manager if needed.
4. Open `edge://policy` and reload policies.
5. Confirm user01 is a member of GRP-Pilot-Users.
6. Check Intune profile status for Pending, Error, Conflict, or Not applicable.

## Current Lab Status

| Task | Status |
|---|---|
| Create configuration profiles folder | Completed |
| Add this Markdown file | Completed |
| Create Windows basic configuration profile | Completed |
| Configure Microsoft Edge startup setting | Completed |
| Assign profile to pilot users | Completed |
| Sync WIN-CORP-001 | Completed |
| Confirm Edge opens configured startup page | Completed |
| Add sanitized screenshots | Pending |

## Next Step

Add sanitized screenshots when available and continue with additional configuration/security labs.
