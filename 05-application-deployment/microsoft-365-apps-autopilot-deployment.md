# Microsoft 365 Apps Deployment After Autopilot Enrollment

This file documents Microsoft 365 Apps deployment using Microsoft Intune and validates the result after Windows Autopilot enrollment.

---

## Objective

Deploy Microsoft 365 Apps to managed Windows devices using Microsoft Intune and confirm that the apps install successfully after Autopilot enrollment.

This lab validates that:

- A test user has the required Microsoft 365 Apps license.
- Microsoft 365 Apps can be added from the Intune admin center.
- Microsoft 365 Apps can be configured for Windows 10 and later / Windows 11 devices.
- Microsoft 365 Apps for business can be configured using XML data.
- Microsoft 365 Apps can be assigned as a **Required** app to a pilot user group.
- A managed Windows device can receive the Microsoft 365 Apps assignment.
- Microsoft 365 Apps install status can be monitored from Intune.
- Microsoft 365 Apps installation can be verified from the device managed apps view.
- Microsoft 365 Apps can install successfully after Windows Autopilot enrollment.
- Company Portal can confirm installed required apps after Autopilot provisioning.

---

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company, **Contoso Startup Lab**, uses Microsoft Intune to deploy required productivity applications to managed Windows devices.

This lab continues the application deployment section after:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

This lab was first used to prepare Microsoft 365 Apps deployment in Intune. It was later validated after a Windows Autopilot user-driven enrollment test.

Completed validation flow:

```text
Microsoft 365 Apps deployment created in Intune
-> App assigned as Required to GRP-Pilot-Users
-> Autopilot device completed OOBE enrollment
-> Device joined Microsoft Entra ID
-> Device enrolled into Microsoft Intune
-> Required apps applied after enrollment
-> Microsoft 365 Apps installed successfully
-> Company Portal showed installed required apps
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

This lab demonstrates that Microsoft 365 Apps can be deployed with Intune and validated after Autopilot enrollment.

This is important because Autopilot is not only about device enrollment. In real environments, the goal is to deliver a ready-to-use device with apps, policies, and security settings.

---

## Relationship to Windows Autopilot

This Microsoft 365 Apps lab and the Windows Autopilot lab are connected.

| Lab | Purpose |
|---|---|
| `microsoft-365-apps-autopilot-deployment.md` | Creates, assigns, and validates Microsoft 365 Apps deployment |
| `windows-autopilot-user-driven-enrollment.md` | Provisions a corporate Windows device using Autopilot |

The validated connection is:

```text
Microsoft 365 Apps deployment was created first
-> Autopilot device enrolled later
-> Intune applied the required app assignment
-> Microsoft 365 Apps installed after enrollment
```

Related Autopilot lab:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

---

## Lab Environment

| Item | Value |
|---|---|
| Initial test device | `WIN-CORP-001` |
| Autopilot validation device | `WIN-AUTOPILOT-001 / WINAUTO452` |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | `user01` |
| Assignment group | `GRP-Pilot-Users` |
| Autopilot device group | `GRP-Autopilot-Devices` |
| App type | Microsoft 365 Apps |
| Assignment type | Required |
| Deployment purpose | Productivity app deployment after Autopilot enrollment |
| Final result | Installed after Autopilot enrollment |

---

## Prerequisites

Before starting this lab, the following items were required:

- Microsoft Intune tenant
- `user01` created in Microsoft Entra ID
- `user01` added to `GRP-Pilot-Users`
- `user01` assigned an Intune-capable license
- `user01` assigned Microsoft 365 Business Premium
- `WIN-CORP-001` enrolled in Intune
- Autopilot test device registered and assigned to an Autopilot profile
- Sanitized screenshots prepared for GitHub upload

Related completed labs:

```text
01-identity-and-groups/users-and-groups.md
02-device-enrollment/windows-oobe-enrollment.md
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
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

Microsoft Entra ID P2 can be useful later for more advanced identity and security labs, such as Conditional Access, identity protection, user risk, sign-in risk, access reviews, or privileged identity management concepts.

---

## Important Concept

Microsoft 365 Apps for business is supported in Intune, but the app suite should be configured using XML data.

For this lab, the XML configuration used the following Product ID:

```text
O365BusinessRetail
```

This represents Microsoft 365 Apps for business.

---

## App Deployment Plan

| Setting | Value |
|---|---|
| App suite | Microsoft 365 Apps |
| Platform | Windows 10 and later / Windows 11 |
| Assignment | Required |
| Target group | `GRP-Pilot-Users` |
| Test user | `user01` |
| Initial test device | `WIN-CORP-001` |
| Autopilot validation device | `WIN-AUTOPILOT-001 / WINAUTO452` |
| Configuration format | XML data |
| Product ID | `O365BusinessRetail` |
| Update channel | Current Channel |
| Architecture | 64-bit |
| Remove MSI versions | Enabled through XML |
| Shared computer activation | Not configured |
| Final result | Installed |

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
| Description | `Deploys Microsoft 365 Apps to pilot users for the MD-102 Intune lab and Autopilot validation.` |
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
user01 is a member of GRP-Pilot-Users and signs in to managed Windows devices for app deployment testing.
```

Assignment logic:

```text
user01 is in GRP-Pilot-Users
-> Microsoft 365 Apps assignment applies
-> Managed Windows device receives required install intent
-> Microsoft 365 Apps installs on the device
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

### Step 8: Verified Assignment on the Initial Managed Device

The device app list for `WIN-CORP-001` showed:

```text
Microsoft 365 Apps for Windows 10 and later
Resolved intent: Required install
Installation status: Waiting for install status
```

This confirmed the required app assignment reached the managed Windows device.

### Step 9: Synced and Waited for Processing

`WIN-CORP-001` was kept powered on and connected to the internet.

A manual sync was performed from the Windows device.

### Step 10: Verified Final Install Status from Device Managed Apps View

The device app list for `WIN-CORP-001` later showed:

```text
Microsoft 365 Apps for Windows 10 and later
Resolved intent: Required install
Installation status: Installed
```

This confirmed the Microsoft 365 Apps deployment installed successfully on the managed Windows device.

### Step 11: Validated Microsoft 365 Apps After Autopilot Enrollment

After the Windows Autopilot lab was completed, the Autopilot-enrolled device `WINAUTO452` was reviewed from Intune.

The managed apps view showed Microsoft 365 Apps installed along with other assigned apps.

Observed post-Autopilot result:

```text
Autopilot enrollment completed
-> Device became Intune managed
-> Required app assignments applied
-> Microsoft 365 Apps installed
-> Company Portal showed required apps installed
```

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
| Microsoft 365 Apps install status changed to Installed | Completed |
| Microsoft 365 Apps installed on endpoint | Completed |
| Autopilot validation device enrolled | Completed |
| Microsoft 365 Apps installed after Autopilot enrollment | Completed |
| Company Portal showed installed apps after Autopilot | Completed |
| Screenshots uploaded | Completed |
| Final lab result | Completed |

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

### Managed apps installed status

![Microsoft 365 Apps managed apps installed status](../screenshots/sanitized/application-deployment/m365-managed-apps-installed-status-sanitized.png)

### Autopilot managed apps installed status

![Autopilot managed apps installed](../screenshots/sanitized/application-deployment/autopilot-managed-apps-installed-sanitized.png)

### Company Portal installed apps after Autopilot

![Company Portal installed apps after Autopilot](../screenshots/sanitized/application-deployment/company-portal-installed-apps-after-autopilot-sanitized.png)

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
| `m365-managed-apps-installed-status-sanitized.png` | Uploaded | Shows installation completed on `WIN-CORP-001` |
| `autopilot-managed-apps-installed-sanitized.png` | Uploaded | Shows required apps installed after Autopilot enrollment |
| `company-portal-installed-apps-after-autopilot-sanitized.png` | Uploaded | Shows Company Portal installed apps after Autopilot |

---

## Optional Future Evidence

The following screenshots can be added later if desired, but they are not required to complete this lab:

| Screenshot file | Status | Purpose |
|---|---|---|
| `m365-device-install-status-sanitized.png` | Optional | App-specific Device install status page showing Installed |
| `m365-apps-installed-start-menu-sanitized.png` | Optional | Shows Office apps installed locally |
| `m365-word-launch-signin-sanitized.png` | Optional | Shows Word/Office app launch with sanitized account info |

---

## Troubleshooting Notes

### Temporary Waiting or Failed Status

During testing, the Microsoft 365 Apps deployment initially showed a waiting or failed state before later showing as installed from the device managed apps view.

This is useful real-world troubleshooting evidence because Microsoft 365 Apps deployments can take longer than small Store apps or Win32 utilities.

Observed troubleshooting approach:

```text
Keep the managed Windows device powered on
Confirm internet connectivity
Manually sync the device
Wait for Intune and Office installation processing
Refresh the device managed apps view
```

Final observed result:

```text
Microsoft 365 Apps for Windows 10 and later = Installed
```

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

### App install shows Failed or Unknown

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

The Windows Autopilot validation has been completed.

Validated flow:

```text
WIN-AUTOPILOT-001 was registered with Windows Autopilot
-> Autopilot profile was assigned
-> Device completed OOBE with user01
-> Device enrolled into Intune as WINAUTO452
-> Required app assignments applied
-> Microsoft 365 Apps installed
-> Company Portal showed installed apps
```

The Autopilot lab is documented here:

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
| Microsoft 365 Apps installed status verified | Completed |
| Autopilot validation completed | Completed |
| Microsoft 365 Apps installed after Autopilot | Completed |
| Company Portal installed apps verified after Autopilot | Completed |
| Screenshots uploaded | Completed |
| Documentation updated with final evidence | Completed |

---

## Next Step

Continue to endpoint security policy labs.

Recommended next lab:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Follow-on endpoint security labs:

```text
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```
