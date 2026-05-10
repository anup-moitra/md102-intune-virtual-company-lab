# Microsoft 365 Apps Deployment for Autopilot Readiness

This file documents the planned Microsoft 365 Apps deployment lab using Microsoft Intune for the MD-102 Intune virtual company project.

---

## Status

Planned / documentation template prepared / not yet tested

---

## Objective

Deploy Microsoft 365 Apps for Windows devices using Microsoft Intune.

This lab will validate that:

- Microsoft 365 Apps can be created from the Intune admin center.
- Office applications such as Word, Excel, PowerPoint, Outlook, OneNote, and Teams can be selected for deployment.
- Microsoft 365 Apps can be assigned as a **Required** app to a pilot group.
- A managed Windows device can receive the Microsoft 365 Apps deployment.
- Installation status can be monitored from Intune.
- Office app launch and user sign-in can be verified.
- The app deployment can be used later as part of Windows Autopilot provisioning validation.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy required productivity applications to managed Windows devices.

This lab continues the application deployment section after:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

This lab prepares Microsoft 365 Apps deployment so that future Windows Autopilot testing can show a realistic provisioning experience:

```text
Autopilot enrollment
-> Device joins Microsoft Entra ID
-> Device enrolls into Intune
-> Required apps and policies apply
-> Microsoft 365 Apps install on the device
-> User opens Office apps and signs in
```

---

## Why This Lab Matters

Microsoft 365 Apps deployment is a common real-world Intune administrator task.

In many organizations, users need productivity apps immediately after receiving a new Windows device.

A common modern deployment flow is:

```text
User receives a new Windows laptop
-> Device goes through Windows Autopilot
-> Device enrolls into Intune
-> Required apps install automatically
-> User opens Word, Excel, Outlook, Teams, or OneNote
```

This lab demonstrates how Microsoft 365 Apps can be prepared in Intune before the Autopilot lab is completed.

This is important because Autopilot is not only about enrollment. In real environments, the goal is to deliver a ready-to-use device with apps, policies, and security settings.

---

## Relationship to Windows Autopilot

This lab and the Windows Autopilot lab are connected, but they are separate labs.

| Lab | Purpose |
|---|---|
| `microsoft-365-apps-autopilot-deployment.md` | Creates and assigns Microsoft 365 Apps in Intune |
| `windows-autopilot-user-driven-enrollment.md` | Enrolls/provisions a Windows device using Autopilot |

The connection is:

```text
Microsoft 365 Apps deployment is created first
-> Autopilot device enrolls later
-> Intune applies the required app assignment
-> Microsoft 365 Apps install after enrollment
```

---

## Lab Environment

| Item | Planned value |
|---|---|
| Test device | `WIN-CORP-001` first, then future `WIN-AUTOPILOT-001` |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | `user01` |
| Assignment group | `GRP-Pilot-Users` |
| Future Autopilot group | `GRP-Autopilot-Devices` |
| App type | Microsoft 365 Apps |
| Assignment type | Required |
| Deployment purpose | Productivity app deployment and future Autopilot readiness |

---

## Prerequisites

Before starting this lab, confirm:

- Microsoft Intune tenant is available.
- `user01` exists in Microsoft Entra ID.
- `user01` is a member of `GRP-Pilot-Users`.
- `user01` has an Intune-capable license.
- Microsoft 365 Apps license is available for the test user.
- `WIN-CORP-001` is enrolled in Intune.
- Screenshots will be sanitized before upload.

Related completed labs:

```text
01-identity-and-groups/users-and-groups.md
02-device-enrollment/windows-oobe-enrollment.md
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

---

## App Deployment Plan

| Setting | Planned value |
|---|---|
| App suite | Microsoft 365 Apps |
| Platform | Windows 10 and later / Windows 11 |
| Assignment | Required |
| Target group | `GRP-Pilot-Users` |
| Test user | `user01` |
| Initial test device | `WIN-CORP-001` |
| Future validation device | `WIN-AUTOPILOT-001` |
| Update channel | Current Channel |
| Architecture | 64-bit |
| Remove other versions | Yes, if old Office versions exist |
| Shared computer activation | No |

---

## Planned Microsoft 365 Apps Selection

Recommended apps for the first lab:

| App | Planned selection | Reason |
|---|---|---|
| Word | Selected | Core productivity app |
| Excel | Selected | Core productivity app |
| PowerPoint | Selected | Core productivity app |
| Outlook | Selected | Email/calendar app |
| OneNote | Selected | Notes app |
| Teams | Selected if available in the app suite options | Collaboration app |
| Access | Not selected unless needed | Not required for basic lab |
| Publisher | Not selected unless available/needed | Not required for basic lab |
| Visio | Not selected | Separate license/app |
| Project | Not selected | Separate license/app |

> [!NOTE]
> The exact app selection screen may vary depending on the Microsoft 365 Apps deployment experience available in the tenant.

---

## Intune Navigation

Create the app from:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
-> Create
```

Select an app type similar to:

```text
Microsoft 365 Apps
```

or:

```text
Microsoft 365 Apps for Windows 10 and later
```

> [!NOTE]
> The exact app type wording may vary slightly in the Intune admin center.

---

## Configuration Plan

### App Suite Information

| Setting | Planned value |
|---|---|
| Name | `Microsoft 365 Apps - Pilot` |
| Description | `Deploys Microsoft 365 Apps to pilot users for the MD-102 Intune lab.` |
| Publisher | `Microsoft` |
| Category | Productivity |
| Show this as a featured app in Company Portal | No |
| Owner | IT Admin |
| Notes | `Microsoft 365 Apps deployment test for MD-102 Intune lab and future Autopilot validation.` |

### App Suite Settings

| Setting | Planned value |
|---|---|
| Office apps | Word, Excel, PowerPoint, Outlook, OneNote, Teams if available |
| Architecture | 64-bit |
| Update channel | Current Channel |
| Remove other versions | Yes, if prompted |
| Version to install | Latest available |
| Shared computer activation | No |

### Assignments

| Assignment type | Group |
|---|---|
| Required | `GRP-Pilot-Users` |

Do not assign to all users or all devices in the first test.

---

## Steps to Perform

### Step 1: Confirm License Assignment

Confirm that `user01` has a license that includes Microsoft 365 Apps.

Check from:

```text
Microsoft 365 admin center
-> Users
-> Active users
-> user01
-> Licenses and apps
```

Expected result:

```text
user01 has the required license for Microsoft 365 Apps installation and activation.
```

### Step 2: Open Windows Apps in Intune

Go to:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
```

Select:

```text
Create
```

### Step 3: Select Microsoft 365 Apps App Type

Choose the Microsoft 365 Apps app type.

Expected app type:

```text
Microsoft 365 Apps
```

or:

```text
Microsoft 365 Apps for Windows 10 and later
```

### Step 4: Configure App Suite Information

Configure:

```text
Name: Microsoft 365 Apps - Pilot
Publisher: Microsoft
Category: Productivity
Owner: IT Admin
```

Description:

```text
Deploys Microsoft 365 Apps to pilot users for the MD-102 Intune lab.
```

### Step 5: Select Office Apps

Select the required apps:

```text
Word
Excel
PowerPoint
Outlook
OneNote
Teams, if available
```

Leave advanced or unnecessary apps unselected unless needed for the lab.

### Step 6: Configure App Suite Settings

Recommended first test settings:

```text
Architecture: 64-bit
Update channel: Current Channel
Remove other versions: Yes, if prompted
Version: Latest available
Shared computer activation: No
```

### Step 7: Configure Scope Tags

Leave scope tags as default unless a scope tag strategy has been created.

### Step 8: Assign the App

Assign as:

```text
Required
```

Target group:

```text
GRP-Pilot-Users
```

### Step 9: Review and Create

Review the configuration and create the app.

Confirm:

```text
Microsoft 365 Apps - Pilot appears in Windows apps.
```

### Step 10: Sync the Test Device

On `WIN-CORP-001`, trigger a device sync:

```text
Settings
-> Accounts
-> Access work or school
-> Connected work/school account
-> Info
-> Sync
```

### Step 11: Monitor Installation Status in Intune

Check the deployment status from:

```text
Intune admin center
-> Apps
-> Windows
-> Microsoft 365 Apps - Pilot
-> Monitor
-> Device install status
```

Expected result:

```text
WIN-CORP-001 = Installed / Success
```

### Step 12: Verify Microsoft 365 Apps Locally

On `WIN-CORP-001`, verify that Office apps are installed.

Check:

```text
Start menu
-> Word
-> Excel
-> PowerPoint
-> Outlook
```

Open Word or Excel and confirm the app launches.

If prompted, sign in using:

```text
user01
```

### Step 13: Prepare for Future Autopilot Validation

After this lab is completed, this same Microsoft 365 Apps deployment can be observed during or after the future Autopilot lab.

Future validation device:

```text
WIN-AUTOPILOT-001
```

Future related lab:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

---

## Test Result

| Test item | Result |
|---|---|
| Microsoft 365 Apps license confirmed for `user01` | Pending |
| Microsoft 365 Apps app type selected in Intune | Pending |
| App suite information configured | Pending |
| Office apps selected | Pending |
| App suite settings configured | Pending |
| App assigned as Required to `GRP-Pilot-Users` | Pending |
| App created in Intune | Pending |
| `WIN-CORP-001` synced | Pending |
| Install status reviewed in Intune | Pending |
| Microsoft 365 Apps installed on endpoint | Pending |
| Word or Excel launched successfully | Pending |
| User sign-in verified | Pending |
| Screenshots uploaded | Pending |
| Final lab result | Pending |

---

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/application-deployment/
```

| Screenshot file | Status | Notes |
|---|---|---|
| `m365-user-license-assignment-sanitized.png` | Pending | Show `user01` has required license |
| `m365-app-type-selection-sanitized.png` | Pending | Show Microsoft 365 Apps app type selection |
| `m365-app-suite-information-sanitized.png` | Pending | Show name, publisher, description |
| `m365-office-apps-selection-sanitized.png` | Pending | Show selected Office apps |
| `m365-app-suite-settings-sanitized.png` | Pending | Show architecture/update channel/settings |
| `m365-required-assignment-sanitized.png` | Pending | Show Required assignment to `GRP-Pilot-Users` |
| `m365-review-create-sanitized.png` | Pending | Optional review page before app creation |
| `m365-app-created-list-sanitized.png` | Pending | Optional app list after creation |
| `device-sync-after-m365-assignment-sanitized.png` | Pending | Show Windows device sync after assignment |
| `m365-device-install-status-sanitized.png` | Pending | Show Intune device install status |
| `m365-apps-installed-start-menu-sanitized.png` | Pending | Show Office apps installed on endpoint |
| `m365-word-launch-signin-sanitized.png` | Pending | Show Word/Office app launch with sanitized account info |

> [!IMPORTANT]
> Do not add image links until the actual screenshot files exist in the repository. This avoids broken images in GitHub.

---

## Future Screenshot Links

After screenshots are uploaded, add image links in this section.

Example format:

```markdown
![Microsoft 365 Apps required assignment](../screenshots/sanitized/application-deployment/m365-required-assignment-sanitized.png)
```

---

## Autopilot Validation Notes

This lab prepares the Microsoft 365 Apps deployment.

The future Autopilot lab will validate whether apps and policies apply after a device is provisioned.

Expected future flow:

```text
WIN-AUTOPILOT-001 starts OOBE
-> user01 signs in
-> device joins Microsoft Entra ID
-> device enrolls into Intune
-> required app assignments apply
-> Microsoft 365 Apps install
```

The Microsoft 365 Apps deployment can be referenced later from:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

---

## Troubleshooting Notes

### Microsoft 365 Apps does not install

If the app does not install:

1. Confirm the app is assigned as **Required**.
2. Confirm `user01` is a member of `GRP-Pilot-Users`.
3. Confirm `user01` has a Microsoft 365 Apps license.
4. Confirm the device is enrolled in Intune.
5. Trigger a manual sync on the Windows device.
6. Restart the device if needed.
7. Wait for Intune policy and app assignment processing.
8. Review app install status in Intune.

### Office apps install but activation fails

If Word, Excel, or Outlook install but activation fails:

1. Confirm `user01` has the correct Microsoft 365 Apps license.
2. Confirm the device has internet access.
3. Confirm the user signs in with the correct work account.
4. Confirm there are no conflicting Office installations.
5. Sign out and sign back in to the Office app.
6. Restart the device and test again.

### Install status is delayed

Intune reporting can take time.

If the app appears installed locally but Intune has not updated yet:

1. Wait and refresh the Intune app install status.
2. Sync the device.
3. Restart the device if needed.
4. Check again from the app monitor page.

### Autopilot deployment does not immediately install Office

During Autopilot testing, app installation may depend on:

- Assignment targeting
- Device or user group membership
- Enrollment Status Page configuration
- Network speed
- App size
- Intune Management Extension timing
- Microsoft 365 Apps installation time

This should be documented in the future Autopilot lab if observed.

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
- Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Unsanitized screenshots
- Production company data

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device IDs
- Object IDs
- Serial numbers
- License subscription identifiers if sensitive
- Any authentication prompts or codes

---

## Current Status

| Task | Status |
|---|---|
| Microsoft 365 Apps lab documentation created | Completed |
| License assignment verified | Pending |
| Microsoft 365 Apps deployment created in Intune | Pending |
| Microsoft 365 Apps assigned to pilot group | Pending |
| Endpoint installation verified | Pending |
| Future Autopilot validation prepared | Pending |
| Screenshots uploaded | Pending |
| Documentation updated with final evidence | Pending |

---

## Next Step

Start the hands-on Microsoft 365 Apps deployment:

```text
1. Confirm user01 has a Microsoft 365 Apps license.
2. Create Microsoft 365 Apps deployment in Intune.
3. Assign the app as Required to GRP-Pilot-Users.
4. Sync WIN-CORP-001.
5. Verify install status and Office app launch.
```

After this lab is completed, continue to:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```
