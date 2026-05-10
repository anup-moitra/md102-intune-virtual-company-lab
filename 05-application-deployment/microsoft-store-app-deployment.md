# Microsoft Store App Deployment with Intune

This file documents Microsoft Store app deployment using Microsoft Intune for the MD-102 Intune virtual company lab.

---

## Objective

Deploy Microsoft Store apps using **Microsoft Store app (new)** in Microsoft Intune.

This lab validates that:

- Microsoft Store apps can be added to Intune.
- Apps can be assigned as **Required** for automatic installation.
- Apps can be assigned as **Available for enrolled devices** for user self-service installation from Company Portal.
- A managed Windows device can sync with Intune and receive app assignments.
- App deployment status can be monitored from the Intune admin center.
- Required apps can be verified as installed from Company Portal.
- Available apps can be viewed from the Company Portal app with an install option.

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
-> Admin verifies app status in Intune and Company Portal
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

## Apps Deployed

| App | Assignment type | Install behavior | Target group | Result |
|---|---|---|---|---|
| Company Portal | Required | System | `GRP-Pilot-Users` | Installed |
| VLC UWP | Required | System | `GRP-Pilot-Users` | Installed |
| Slack | Required | System | `GRP-Pilot-Users` | Installed |
| ChatGPT | Available for enrolled devices | User | `GRP-Pilot-Users` | Visible in Company Portal with install option |
| WhatsApp | Available for enrolled devices | System | `GRP-Pilot-Users` | Visible in Company Portal with install option |

> [!NOTE]
> Slack was kept as a required app in the final lab configuration. ChatGPT and WhatsApp were configured as available/self-service apps for Company Portal testing.

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
Required apps = Company Portal, VLC UWP, Slack
Available apps = ChatGPT, WhatsApp
```

Another important learning:

```text
Changing an app from Required to Available does not automatically uninstall it from the endpoint.
To remove an already installed app automatically, an Uninstall assignment is required.
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
| Category | Productivity |
| Owner | IT Admin |
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
| Publisher | VideoLAN |
| App type | Microsoft Store app (new) |
| Installer type | UWP |
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
| Publisher | Slack Technologies Inc. |
| App type | Microsoft Store app (new) |
| Installer type | UWP |
| Install behavior | System |
| Assignment type | Required |
| Target group | `GRP-Pilot-Users` |

Slack was assigned as **Required** because it is a common business communication app that organizations may install automatically.

### Step 6: Created ChatGPT App

The Microsoft Store app search was used to find:

```text
ChatGPT
```

Important settings:

| Setting | Value |
|---|---|
| App | ChatGPT |
| Publisher | OpenAI |
| App type | Microsoft Store app (new) |
| Installer type | UWP |
| Install behavior | User |
| Assignment type | Available for enrolled devices |
| Target group | `GRP-Pilot-Users` |

ChatGPT was assigned as **Available for enrolled devices** to demonstrate optional self-service app deployment through Company Portal.

### Step 7: Created WhatsApp App

The Microsoft Store app search was used to find:

```text
WhatsApp
```

Important settings:

| Setting | Value |
|---|---|
| App | WhatsApp |
| Publisher | WhatsApp Inc. |
| App type | Microsoft Store app (new) |
| Installer type | UWP |
| Install behavior | System |
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

The device sync completed successfully.

### Step 10: Reviewed Company Portal Install Status in Intune

Company Portal deployment status was checked from:

```text
Intune admin center
-> Apps
-> Windows
-> Company Portal
-> Monitor
-> Device install status
```

Observed result:

| Device | Status |
|---|---|
| `WIN-CORP-001` | Installed |

This confirms that the required Company Portal deployment succeeded on the managed Windows device.

### Step 11: Verified Required Apps in Company Portal

On `WIN-CORP-001`, Company Portal was opened.

Navigation used:

```text
Company Portal
-> Downloads & updates
```

The following required apps were shown as installed:

```text
Company Portal
Slack
VLC UWP
```

Company Portal showed these apps as required by the organization and installed.

### Step 12: Verified Available Apps in Company Portal

On `WIN-CORP-001`, Company Portal was opened.

Navigation used:

```text
Company Portal
-> Apps
```

The following available apps were visible to the user:

```text
ChatGPT
WhatsApp
```

Both apps showed an available/install option, confirming that the available assignment worked.

---

## Test Result

| Test item | Result |
|---|---|
| Microsoft Store app type selected | Completed |
| Company Portal created | Completed |
| Company Portal assigned as Required | Completed |
| Company Portal install status on `WIN-CORP-001` | Installed |
| VLC UWP created | Completed |
| VLC UWP assigned as Required | Completed |
| VLC UWP visible as installed in Company Portal | Completed |
| Slack created | Completed |
| Slack assigned as Required | Completed |
| Slack visible as installed in Company Portal | Completed |
| ChatGPT created | Completed |
| ChatGPT assigned as Available | Completed |
| ChatGPT visible in Company Portal | Completed |
| WhatsApp created | Completed |
| WhatsApp assigned as Available | Completed |
| WhatsApp visible in Company Portal | Completed |
| Windows app list reviewed | Completed |
| Device sync triggered | Completed |
| Required app install status verified | Completed |
| Available apps visible in Company Portal | Completed |
| Final lab result | Completed |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/application-deployment/
```

### Company Portal app information

![Company Portal app information](../screenshots/sanitized/application-deployment/company-portal-app-information-sanitized.png)

### Company Portal required assignment

![Company Portal required assignment](../screenshots/sanitized/application-deployment/company-portal-required-assignment-sanitized.png)

### Microsoft Store apps list in Intune

![Microsoft Store apps list](../screenshots/sanitized/application-deployment/store-apps-list-sanitized.png)

### Company Portal device install status

![Company Portal device install status](../screenshots/sanitized/application-deployment/company-portal-device-install-status-sanitized.png)

### Required apps installed in Company Portal

![Required apps installed in Company Portal](../screenshots/sanitized/application-deployment/company-portal-required-apps-installed-sanitized.png)

### Available apps in Company Portal

![Available apps in Company Portal](../screenshots/sanitized/application-deployment/company-portal-available-apps-sanitized.png)

### Device sync after Store app assignment

![Device sync after Store app assignment](../screenshots/sanitized/application-deployment/device-sync-after-store-app-assignment-sanitized.png)

---

## Troubleshooting Notes

### Available app does not show device install status immediately

For available apps, Intune may show no device install status until the user manually starts the installation from Company Portal.

Example:

```text
ChatGPT assigned as Available
-> App appears in Company Portal
-> User has not clicked Install yet
-> Device install status may show 0 items
```

This is expected behavior for optional/self-service apps.

### Required apps do not install

If required apps do not install:

1. Confirm the app is assigned as **Required**.
2. Confirm `user01` is a member of `GRP-Pilot-Users`.
3. Sync the device manually.
4. Restart the device if needed.
5. Check the app device install status in Intune.
6. Confirm the device has internet access.
7. Wait for Intune reporting delay.

### Available apps do not appear in Company Portal

If available apps do not appear in Company Portal:

1. Confirm the app is assigned as **Available for enrolled devices**.
2. Confirm the assignment group is `GRP-Pilot-Users`.
3. Confirm the signed-in Company Portal user is `user01`.
4. Sync the device.
5. Close and reopen Company Portal.
6. Wait for the Company Portal app catalog to refresh.

### App was accidentally assigned as Required

During testing, an optional app may accidentally be assigned as Required.

If this happens:

1. Open the app in Intune.
2. Go to **Properties**.
3. Edit **Assignments**.
4. Remove the group from **Required**.
5. Add the group under **Available for enrolled devices**.
6. Review and save.
7. Sync the endpoint and recheck Company Portal.

Changing an app from Required to Available does not automatically remove the app from the endpoint. To remove an already installed app automatically, configure an **Uninstall** assignment.

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
- Exchange ID
- Any sensitive identifiers

---

## Current Status

| Task | Status |
|---|---|
| Microsoft Store apps created | Completed |
| Required app assignment configured | Completed |
| Available app assignment configured | Completed |
| Device sync performed | Completed |
| Required app install status verified | Completed |
| Available apps checked in Company Portal | Completed |
| Screenshots captured | Completed |
| Screenshots uploaded | Completed |
| Documentation updated | Completed |

---

## Next Step

Continue to the next application deployment lab:

```text
05-application-deployment/win32-app-deployment-7zip.md
```
