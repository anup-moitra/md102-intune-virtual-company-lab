# Microsoft 365 Apps Deployment for Autopilot Readiness

This file documents Microsoft 365 Apps deployment using Microsoft Intune for the MD-102 Intune virtual company project.

---

## Status

In progress / app created / assigned / installation troubleshooting pending

---

## Objective

Deploy Microsoft 365 Apps to a managed Windows device using Microsoft Intune.

This lab validates that:

- A test user has the required Microsoft 365 Apps license.
- Microsoft 365 Apps can be added from the Intune admin center.
- Microsoft 365 Apps can be configured for Windows 10 and later / Windows 11 devices.
- Microsoft 365 Apps for business can be configured using XML data.
- Microsoft 365 Apps can be assigned as a **Required** app to a pilot user group.
- A managed Windows device can receive the assignment.
- App install status can be monitored from Intune.
- Installation issues can be captured and documented for troubleshooting.
- This deployment can later support Windows Autopilot validation.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy required productivity applications to managed Windows devices.

This lab continues the application deployment section after:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

The purpose of this lab is to prepare Microsoft 365 Apps deployment so that a future Windows Autopilot lab can show a realistic provisioning experience:

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

| Item | Value |
|---|---|
| Test device | `WIN-CORP-001` |
| Future Autopilot validation device | `WIN-AUTOPILOT-001` |
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
- `user01` has Microsoft 365 Business Premium assigned.
- Microsoft 365 Apps license is available for the test user.
- `WIN-CORP-001` is enrolled in Intune.
- Screenshots are sanitized before upload.

Related completed labs:

```text
01-identity-and-groups/users-and-groups.md
02-device-enrollment/windows-oobe-enrollment.md
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

---

## License Validation

`user01` was assigned the following licenses:

```text
Intune
Microsoft 365 Business Premium
```

Microsoft Entra ID P2 was not required for this Microsoft 365 Apps deployment lab.

Microsoft Entra ID P2 will be useful later for more advanced identity and security labs, such as Conditional Access, identity protection, user risk, sign-in risk, access reviews, or privileged identity management concepts.

---

## App Deployment Plan

| Setting | Value |
|---|---|
| App suite | Microsoft 365 Apps |
| Platform | Windows 10 and later / Windows 11 |
| Assignment | Required |
| Target group | `GRP-Pilot-Users` |
| Test user | `user01` |
| Test device | `WIN-CORP-001` |
| Future validation device | `WIN-AUTOPILOT-001` |
| Configuration format | XML data |
| Product ID | `O365BusinessRetail` |
| Update channel | Current Channel |
| Architecture | 64-bit |
| Remove MSI versions | Enabled through XML |
| Shared computer activation | Not configured |
| Current result | Assignment reached device; installation troubleshooting pending |

---

## Important Concept

Microsoft 365 Apps for business is supported in Intune, but the app suite should be configured using XML data.

For this lab, the XML configuration used the following Product ID:

```text
O365BusinessRetail
```

This represents Microsoft 365 Apps for business.

---

## Intune Navigation

The app was created from:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
-> Create
```

Selected app type:

```text
Microsoft 365 Apps
-> Windows 10 and later
```

---

## App Suite Information

| Setting | Value |
|---|---|
| Name | `Microsoft 365 Apps - Pilot` |
| Intune displayed app name | `Microsoft 365 Apps for Windows 10 and later` |
| Description | `Deploys Microsoft 365 Apps to pilot users for the MD-102 Intune lab and future Autopilot validation.` |
| Publisher | `Microsoft` |
| Category | Productivity |
| Owner | IT Admin |
| Notes | `Microsoft 365 Apps deployment test for MD-102 Intune lab.` |

> [!NOTE]
> Depending on the Intune portal experience, the app may display as `Microsoft 365 Apps for Windows 10 and later` even if a custom suite name was configured.

---

## Configure App Suite

The app suite was configured using:

```text
Configuration settings format: Enter XML data
```

XML used:

```xml
<Configuration>
  <Add OfficeClientEdition="64" Channel="Current">
    <Product ID="O365BusinessRetail">
      <Language ID="MatchOS" />
      <ExcludeApp ID="Groove" />
      <ExcludeApp ID="Lync" />
    </Product>
  </Add>
  <RemoveMSI />
  <Updates Enabled="TRUE" Channel="Current" />
  <Display Level="None" AcceptEULA="TRUE" />
</Configuration>
```

### XML Explanation

| XML setting | Meaning |
|---|---|
| `OfficeClientEdition="64"` | Installs 64-bit Microsoft 365 Apps |
| `Channel="Current"` | Uses Current Channel updates |
| `Product ID="O365BusinessRetail"` | Microsoft 365 Apps for business |
| `Language ID="MatchOS"` | Uses the Windows device language |
| `ExcludeApp ID="Groove"` | Excludes old OneDrive for Business sync client |
| `ExcludeApp ID="Lync"` | Excludes Skype for Business |
| `<RemoveMSI />` | Removes old MSI-based Office versions if present |
| `AcceptEULA="TRUE"` | Accepts the license agreement silently |

---

## Assignments

The app was assigned as:

```text
Required
```

Target group:

```text
GRP-Pilot-Users
```

Reason:

```text
user01 is a member of GRP-Pilot-Users and signs in to WIN-CORP-001 for app deployment testing.
```

Assignment logic:

```text
user01 is in GRP-Pilot-Users
-> Microsoft 365 Apps assignment applies
-> WIN-CORP-001 receives required install intent
```

---

## Steps Performed

### Step 1: Confirmed User License

In the Microsoft 365 admin center, `user01` was checked under:

```text
Users
-> Active users
-> User 01
-> Licenses and apps
```

Confirmed licenses:

```text
Intune
Microsoft 365 Business Premium
```

### Step 2: Opened Windows Apps in Intune

Navigation used:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
-> Create
```

### Step 3: Selected Microsoft 365 Apps App Type

Selected app type:

```text
Microsoft 365 Apps
-> Windows 10 and later
```

### Step 4: Configured App Suite Information

Configured app suite information for the pilot deployment.

Primary intended name:

```text
Microsoft 365 Apps - Pilot
```

Observed Intune app display name:

```text
Microsoft 365 Apps for Windows 10 and later
```

### Step 5: Configured App Suite Using XML

Selected:

```text
Configuration settings format: Enter XML data
```

Used the XML configuration with:

```text
O365BusinessRetail
OfficeClientEdition="64"
Channel="Current"
RemoveMSI
```

### Step 6: Assigned the App

Assigned the app as **Required** to:

```text
GRP-Pilot-Users
```

### Step 7: Created the App

The Microsoft 365 Apps deployment was created in Intune.

### Step 8: Verified Assignment on the Device

The device app list for `WIN-CORP-001` showed:

```text
Microsoft 365 Apps for Windows 10 and later
Resolved intent: Required install
Installation status: Waiting for install status
```

This confirms the required app assignment reached the managed Windows device.

### Step 9: Checked Device Install Status

The app install status page was checked from:

```text
Intune admin center
-> Apps
-> Windows
-> Microsoft 365 Apps for Windows 10 and later
-> Monitor
-> Device install status
```

Latest observed result:

```text
Status: Failed
Status details: Unknown
```

The device was kept powered on and manually synced again for further processing.

---

## Test Result

| Test item | Result |
|---|---|
| Microsoft 365 Apps license confirmed for `user01` | Completed |
| Microsoft 365 Apps app type selected in Intune | Completed |
| App suite information configured | Completed |
| XML configuration used | Completed |
| `O365BusinessRetail` Product ID configured | Completed |
| App assigned as Required to `GRP-Pilot-Users` | Completed |
| App created in Intune | Completed |
| Assignment reached `WIN-CORP-001` | Completed |
| Managed apps page showed Required install intent | Completed |
| Device install status reviewed in Intune | Completed |
| Initial install status | Failed / troubleshooting pending |
| Microsoft 365 Apps installed on endpoint | Pending |
| Word or Excel launched successfully | Pending |
| User sign-in verified | Pending |
| Final lab result | In progress |

---

## Screenshots

Screenshots are stored in:

```text
screenshots/sanitized/application-deployment/
```

### User license assignment

![Microsoft 365 Apps user license assignment](../screenshots/sanitized/application-deployment/m365-user-license-assignment-sanitized.png)

### Microsoft 365 Apps app type selection

![Microsoft 365 Apps app type selection](../screenshots/sanitized/application-deployment/m365-app-type-selection-sanitized.png)

### App suite information

![Microsoft 365 Apps app suite information](../screenshots/sanitized/application-deployment/m365-app-suite-information-sanitized.png)

### App suite XML settings

![Microsoft 365 Apps XML settings](../screenshots/sanitized/application-deployment/m365-app-suite-settings-sanitized.png)

### Required assignment

![Microsoft 365 Apps required assignment](../screenshots/sanitized/application-deployment/m365-required-assignment-sanitized.png)

### Managed apps waiting status

![Microsoft 365 Apps managed apps waiting status](../screenshots/sanitized/application-deployment/m365-managed-apps-waiting-status-sanitized.png)

---

## Screenshot Files Uploaded

| Screenshot file | Status | Purpose |
|---|---|---|
| `m365-user-license-assignment-sanitized.png` | Uploaded | Shows `user01` licensing |
| `m365-app-type-selection-sanitized.png` | Uploaded | Shows Microsoft 365 Apps app type selection |
| `m365-app-suite-information-sanitized.png` | Uploaded | Shows app suite information |
| `m365-app-suite-settings-sanitized.png` | Uploaded | Shows XML configuration |
| `m365-required-assignment-sanitized.png` | Uploaded | Shows Required assignment to `GRP-Pilot-Users` |
| `m365-managed-apps-waiting-status-sanitized.png` | Uploaded | Shows assignment reached `WIN-CORP-001` |

---

## Pending Screenshots

The following screenshots should be added later after troubleshooting or successful installation:

| Screenshot file | Status | Purpose |
|---|---|---|
| `m365-device-install-status-failed-sanitized.png` | Pending / optional | Shows failed install state for troubleshooting evidence |
| `device-sync-after-m365-assignment-sanitized.png` | Optional | Shows manual sync after assignment |
| `device-sync-after-m365-failure-sanitized.png` | Optional | Shows manual sync after failed install |
| `m365-device-install-status-sanitized.png` | Pending | Final success screenshot showing installed status |
| `m365-apps-installed-start-menu-sanitized.png` | Pending | Shows Office apps installed locally |
| `m365-word-launch-signin-sanitized.png` | Pending | Shows Word/Office app launch with sanitized account info |

---

## Troubleshooting Status

Current issue:

```text
Microsoft 365 Apps deployment reached WIN-CORP-001, but the app install status later showed Failed with Unknown status details.
```

Current action taken:

```text
WIN-CORP-001 was kept powered on.
The device was manually synced again.
Further troubleshooting is pending.
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

### App install shows Failed / Unknown

If the app shows failed with unknown status details:

1. Confirm no Office apps are open on the endpoint.
2. Check whether Microsoft 365 Apps or Office is already installed.
3. Check for old MSI-based Office apps.
4. Confirm that the XML uses the correct Product ID:

   ```text
   O365BusinessRetail
   ```

5. Confirm the device can reach Microsoft Office CDN locations.
6. Restart the device.
7. Sync again.
8. Recheck the device install status.
9. Review Intune Management Extension logs.
10. Review Office setup logs if needed.

Common Intune Management Extension log location:

```text
C:\ProgramData\Microsoft\IntuneManagementExtension\Logs\IntuneManagementExtension.log
```

Possible Office-related folder paths to check:

```text
C:\Program Files\Microsoft Office
C:\Program Files\Microsoft Office 15
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

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Billing screenshots
- Trial subscription screenshots
- Service usage addresses
- Payment information
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
- Browser bookmarks if visible

---

## Current Status

| Task | Status |
|---|---|
| Microsoft 365 Apps lab documentation created | Completed |
| License assignment verified | Completed |
| Microsoft 365 Apps deployment created in Intune | Completed |
| Microsoft 365 Apps configured with XML | Completed |
| Microsoft 365 Apps assigned to pilot group | Completed |
| Required install intent reached `WIN-CORP-001` | Completed |
| Initial install status checked | Completed |
| Endpoint installation verified | Pending |
| Future Autopilot validation prepared | Pending |
| Screenshots uploaded | Partially completed |
| Documentation updated with current evidence | Completed |
| Troubleshooting pending | Yes |

---

## Next Step

Continue troubleshooting the Microsoft 365 Apps deployment.

Recommended next actions:

```text
1. Keep WIN-CORP-001 powered on and connected to the internet.
2. Confirm no Office apps are open.
3. Check whether Office/Microsoft 365 Apps is already installed.
4. Restart WIN-CORP-001.
5. Sync the device again.
6. Refresh Intune device install status.
7. If still failed, review Intune Management Extension logs and Office setup logs.
```

After successful installation, update this file with:

```text
m365-device-install-status-sanitized.png
m365-apps-installed-start-menu-sanitized.png
m365-word-launch-signin-sanitized.png
```
