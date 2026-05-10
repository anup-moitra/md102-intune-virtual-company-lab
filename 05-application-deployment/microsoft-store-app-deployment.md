# Microsoft Store App Deployment with Intune

This file documents Microsoft Store app deployment using Microsoft Intune for the MD-102 Intune virtual company lab.

---

## Status

In progress

---

## Objective

Deploy Microsoft Store apps using **Microsoft Store app (new)** in Microsoft Intune.

This lab validates that:

- Microsoft Store apps can be added to Intune.
- Apps can be assigned as **Required** for automatic installation.
- Apps can be assigned as **Available for enrolled devices** for user self-service installation from Company Portal.
- A managed Windows device can sync with Intune and receive app assignments.
- App deployment status can be monitored from the Intune admin center.
- Available apps can be viewed from the Company Portal app.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy apps to managed Windows devices.

This lab focuses on Microsoft Store apps before moving into Win32 app deployment and Microsoft 365 Apps deployment.

Simple flow:

```text
Admin creates Microsoft Store app in Intune
-> App is assigned to pilot users
-> Windows device syncs with Intune
-> Required apps install automatically
-> Available apps appear in Company Portal
-> Admin verifies app status in Intune
```

---

## Why This Lab Matters

Application deployment is one of the core tasks of an Intune administrator.

In a real organization, users need common apps such as communication tools, productivity tools, media tools, and company self-service apps.

Microsoft Store app deployment is useful because it allows admins to deploy Store apps without manually packaging installers.

This lab also demonstrates the difference between required and available app assignments.

| Assignment type | Meaning |
|---|---|
| Required | Intune installs the app automatically for the targeted users or devices |
| Available for enrolled devices | The app appears in Company Portal and the user chooses whether to install it |
| Uninstall | Intune removes the app from targeted users or devices |

---

## Lab Environment

| Item | Value |
|---|---|
| Test device | `WIN-CORP-001` |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | `user01` |
| Assignment group | `GRP-Pilot-Users` |
| App type | Microsoft Store app (new) |
| App delivery methods | Required and Available for enrolled devices |

---

## Apps Created

| App | Assignment type | Install behavior | Target group | Status |
|---|---|---|---|---|
| Company Portal | Required | System | `GRP-Pilot-Users` | Created |
| VLC UWP | Required | System | `GRP-Pilot-Users` | Created |
| Slack | Available for enrolled devices | System | `GRP-Pilot-Users` | Created |
| ChatGPT | Available for enrolled devices | User | `GRP-Pilot-Users` | Created |
| WhatsApp | Available for enrolled devices | User/System as configured | `GRP-Pilot-Users` | Created |

> [!NOTE]
> The final install results will be updated after device sync and Company Portal verification are completed.

---

## Key Learning

The most important learning from this lab is the difference between app creation, install behavior, and assignment type.

```text
App creation = adds the app object to Intune
Install behavior = defines user/system install context
Assignment type = controls whether the app installs automatically or appears as optional
```

For this lab:

```text
Required apps = Company Portal and VLC
Available apps = ChatGPT, Slack, and WhatsApp
```

---

## Steps Performed

### Step 1: Opened Windows Apps in Intune

Navigation used:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
```

The **Create** button was used to start adding Windows apps.

### Step 2: Selected Microsoft Store App Type

App type selected:

```text
Microsoft Store app (new)
```

This app type was used for all Store apps in this lab.

### Step 3: Created Company Portal App

The Microsoft Store app search was used to find:

```text
Company Portal
```

App information was automatically populated by Intune.

Important settings:

| Setting | Value |
|---|---|
| Name | Company Portal |
| Publisher | Microsoft Corporation |
| Installer type | UWP |
| Install behavior | System |
| Assignment type | Required |
| Target group | `GRP-Pilot-Users` |

Company Portal was assigned as **Required** because it is the main self-service app users need to view available apps.

### Step 4: Created VLC UWP App

The Microsoft Store app search was used to find:

```text
VLC UWP
```

Important settings:

| Setting | Value |
|---|---|
| App | VLC UWP |
| App type | Microsoft Store app (new) |
| Install behavior | System |
| Assignment type | Required |
| Target group | `GRP-Pilot-Users` |

VLC was assigned as **Required** to test automatic app installation.

### Step 5: Created Slack App

The Microsoft Store app search was used to find:

```text
Slack
```

Important settings:

| Setting | Value |
|---|---|
| App | Slack |
| App type | Microsoft Store app (new) |
| Install behavior | System |
| Assignment type | Available for enrolled devices |
| Target group | `GRP-Pilot-Users` |

Slack was assigned as **Available for enrolled devices** so the user can install it manually from Company Portal.

### Step 6: Created ChatGPT App

The Microsoft Store app search was used to find:

```text
ChatGPT
```

Important settings:

| Setting | Value |
|---|---|
| App | ChatGPT |
| App type | Microsoft Store app (new) |
| Install behavior | User |
| Assignment type | Available for enrolled devices |
| Target group | `GRP-Pilot-Users` |

ChatGPT was assigned as **Available for enrolled devices** to demonstrate optional self-service app deployment.

### Step 7: Created WhatsApp App

The Microsoft Store app search was used to find:

```text
WhatsApp
```

Important settings:

| Setting | Value |
|---|---|
| App | WhatsApp |
| App type | Microsoft Store app (new) |
| Assignment type | Available for enrolled devices |
| Target group | `GRP-Pilot-Users` |

WhatsApp was added as another optional Store app for Company Portal testing.

### Step 8: Verified App List in Intune

After the apps were created, the Windows apps list showed the Store apps.

Observed apps included:

```text
ChatGPT
Company Portal
Slack
VLC UWP
WhatsApp
```

### Step 9: Synced the Windows Test Device

On `WIN-CORP-001`, a manual sync was started from Windows settings:

```text
Settings
-> Accounts
-> Access work or school
-> Select connected work/school account
-> Info
-> Sync
```

This forces the device to check in with Intune and receive the latest app assignments.

### Step 10: Review App Install Status

App deployment status will be checked from:

```text
Intune admin center
-> Apps
-> Windows
-> Select app
-> Monitor
-> Device install status
```

Expected result for required apps:

```text
Installed
```

or temporarily:

```text
Pending / Waiting for install status
```

### Step 11: Verify Available Apps in Company Portal

On `WIN-CORP-001`, open:

```text
Company Portal
```

Confirm that optional apps appear for the user.

Expected available apps:

```text
ChatGPT
Slack
WhatsApp
```

---

## Test Result

| Test item | Result |
|---|---|
| Microsoft Store app type selected | Completed |
| Company Portal created | Completed |
| Company Portal assigned as Required | Completed |
| VLC UWP created | Completed |
| VLC UWP assigned as Required | Completed |
| Slack created | Completed |
| Slack assigned as Available | Completed |
| ChatGPT created | Completed |
| ChatGPT assigned as Available | Completed |
| WhatsApp created | Completed |
| Windows app list reviewed | Completed |
| Device sync triggered | Pending |
| Required app install status verified | Pending |
| Available apps visible in Company Portal | Pending |
| Final lab result | In progress |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/application-deployment/
```

> [!NOTE]
> Do not add image links until the actual screenshot files exist in the repository. If a screenshot has not been uploaded yet, keep the filename listed under Pending Screenshots instead of using a broken image link.

---

## Pending Screenshots

The following screenshots should be added or confirmed after lab validation:

```text
company-portal-app-information-sanitized.png
company-portal-required-assignment-sanitized.png
chatgpt-available-assignment-sanitized.png
store-apps-list-sanitized.png
device-sync-after-store-app-assignment-sanitized.png
store-apps-device-install-status-sanitized.png
company-portal-available-apps-sanitized.png
```

---

## Troubleshooting Notes

If required apps do not install:

1. Confirm the app is assigned as **Required**.
2. Confirm `user01` is a member of `GRP-Pilot-Users`.
3. Sync the device manually.
4. Restart the device if needed.
5. Check the app device install status in Intune.
6. Confirm the device has internet access.
7. Wait for Intune reporting delay.

If available apps do not appear in Company Portal:

1. Confirm the app is assigned as **Available for enrolled devices**.
2. Confirm the assignment group is `GRP-Pilot-Users`.
3. Confirm the signed-in Company Portal user is `user01`.
4. Sync the device.
5. Close and reopen Company Portal.
6. Wait for the Company Portal app catalog to refresh.

If install status remains pending:

1. Check last check-in time for the device.
2. Trigger another sync.
3. Review app assignment status.
4. Review device install status.
5. Confirm the Store app is available for the device platform.

---

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
- Internal IP addresses
- Unsanitized screenshots
- Production company data

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs / object IDs
- Any sensitive identifiers

---

## Current Status

| Task | Status |
|---|---|
| Microsoft Store apps created | Completed |
| Required app assignment configured | Completed |
| Available app assignment configured | Completed |
| Device sync performed | Pending |
| Required app install status verified | Pending |
| Available apps checked in Company Portal | Pending |
| Screenshots uploaded | Pending |
| Documentation updated | In progress |

---

## Next Step

Sync `WIN-CORP-001`, then verify app deployment status in Intune and available app visibility in Company Portal.

After validation, update this lab from:

```text
Status: In progress
```

to:

```text
Status: Completed
```
