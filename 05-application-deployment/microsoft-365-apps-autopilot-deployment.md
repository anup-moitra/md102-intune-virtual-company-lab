# Microsoft 365 Apps Deployment After Autopilot Enrollment

## Lab status

**Status:** Completed  
**Lab category:** Application deployment  
**Platform:** Windows  
**Management platform:** Microsoft Intune  
**Identity platform:** Microsoft Entra ID  
**Initial test device:** WIN-CORP-001  
**Autopilot validation device:** WINAUTO452  
**Test user:** user01  
**Assignment group:** GRP-Pilot-Users  
**App type:** Microsoft 365 Apps  
**Assignment type:** Required  
**Final result:** Microsoft 365 Apps installed successfully and were validated after Autopilot enrollment  

---

## Lab objective

The objective of this lab is to deploy Microsoft 365 Apps to managed Windows devices using Microsoft Intune and confirm that the apps install successfully after Windows Autopilot enrollment.

This lab validates that:

- A test user has the required Microsoft 365 Apps license.
- Microsoft 365 Apps can be added from the Intune admin center.
- Microsoft 365 Apps can be configured for Windows 10 and later / Windows 11 devices.
- Microsoft 365 Apps for business can be configured using XML data.
- Microsoft 365 Apps can be assigned as a **Required** app to a pilot user group.
- A managed Windows device can receive the Microsoft 365 Apps assignment.
- Microsoft 365 Apps installation status can be monitored from Intune.
- Microsoft 365 Apps can install successfully after Windows Autopilot enrollment.
- Company Portal can confirm installed required apps after Autopilot provisioning.

---

## Why this lab matters

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

## Lab environment

| Item | Value |
|---|---|
| Initial test device | WIN-CORP-001 |
| Autopilot validation device | WINAUTO452 |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | user01 |
| Assignment group | GRP-Pilot-Users |
| Autopilot device group | GRP-Autopilot-Devices |
| App type | Microsoft 365 Apps |
| Assignment type | Required |
| Deployment purpose | Productivity app deployment after enrollment |
| Final lab status | Completed |

---

## Prerequisites

Before starting this lab, the following items were required:

- Microsoft Intune tenant available.
- `user01` created in Microsoft Entra ID.
- `user01` added to `GRP-Pilot-Users`.
- `user01` assigned an Intune-capable license.
- `user01` assigned Microsoft 365 Business Premium.
- `WIN-CORP-001` enrolled in Intune.
- Autopilot test device registered and assigned to an Autopilot profile.
- Device able to sync with Intune.
- Internet access available on the endpoint.

Related completed labs:

```text
01-identity-and-groups/users-and-groups.md
02-device-enrollment/windows-oobe-enrollment.md
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
```

---

## App deployment design

This Microsoft 365 Apps deployment was assigned as a required app to the pilot user group.

| Setting | Value |
|---|---|
| App suite | Microsoft 365 Apps |
| Platform | Windows 10 and later / Windows 11 |
| Assignment | Required |
| Target group | GRP-Pilot-Users |
| Test user | user01 |
| Initial test device | WIN-CORP-001 |
| Autopilot validation device | WINAUTO452 |
| Configuration format | XML data |
| Product ID | O365BusinessRetail |
| Update channel | Current Channel |
| Architecture | 64-bit |
| Remove MSI versions | Enabled through XML |
| Shared computer activation | Not configured |
| Final result | Installed |

### Relationship to Windows Autopilot

This Microsoft 365 Apps lab and the Windows Autopilot lab are connected.

| Lab | Purpose |
|---|---|
| `microsoft-365-apps-autopilot-deployment.md` | Creates, assigns, and validates Microsoft 365 Apps deployment |
| `windows-autopilot-user-driven-enrollment.md` | Provisions a corporate Windows device using Autopilot |

Validated connection:

```text
Microsoft 365 Apps deployment was created first
-> Autopilot device enrolled later
-> Intune applied the required app assignment
-> Microsoft 365 Apps installed after enrollment
```

---

## Configuration flow

```text
Verify user01 license
-> Create Microsoft 365 Apps deployment in Intune
-> Configure app suite information
-> Configure Microsoft 365 Apps using XML
-> Assign app as Required to GRP-Pilot-Users
-> Confirm required install intent reaches WIN-CORP-001
-> Sync and wait for installation
-> Verify installed status
-> Validate installation after Autopilot enrollment on WINAUTO452
```

---

## Steps performed

### Step 1 - Confirmed user license

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

Microsoft Entra ID P2 was not required for this Microsoft 365 Apps deployment lab.

---

### Step 2 - Opened Windows apps in Intune

Navigation used:

```text
Intune admin center
-> Apps
-> Windows
-> Windows apps
-> Create
```

---

### Step 3 - Selected Microsoft 365 Apps app type

Selected app type:

```text
Microsoft 365 Apps
-> Windows 10 and later
```

---

### Step 4 - Configured app suite information

Configured app suite information for the pilot deployment.

Primary intended name:

```text
Microsoft 365 Apps - Pilot
```

Observed Intune app display name:

```text
Microsoft 365 Apps for Windows 10 and later
```

> [!NOTE]
> Depending on the Intune portal experience, the app may display as `Microsoft 365 Apps for Windows 10 and later` even if a custom suite name was configured.

---

### Step 5 - Configured app suite using XML

Selected:

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

### XML explanation

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

### Step 6 - Assigned the app

Assigned the app as **Required** to:

```text
GRP-Pilot-Users
```

Assignment logic:

```text
user01 is in GRP-Pilot-Users
-> Microsoft 365 Apps assignment applies
-> Managed Windows device receives required install intent
-> Microsoft 365 Apps installs on the device
```

---

### Step 7 - Created the app

The Microsoft 365 Apps deployment was created in Intune.

---

### Step 8 - Verified assignment on the initial managed device

The device app list for `WIN-CORP-001` showed:

```text
Microsoft 365 Apps for Windows 10 and later
Resolved intent: Required install
Installation status: Waiting for install status
```

This confirmed the required app assignment reached the managed Windows device.

---

### Step 9 - Synced and waited for processing

`WIN-CORP-001` was kept powered on and connected to the internet.

A manual sync was performed from the Windows device.

---

### Step 10 - Verified final install status from device managed apps view

The device app list for `WIN-CORP-001` later showed:

```text
Microsoft 365 Apps for Windows 10 and later
Resolved intent: Required install
Installation status: Installed
```

This confirmed the Microsoft 365 Apps deployment installed successfully on the managed Windows device.

---

### Step 11 - Validated Microsoft 365 Apps after Autopilot enrollment

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

## Validation

### License validation

Validation confirmed that:

- `user01` had an Intune-capable license.
- `user01` had Microsoft 365 Business Premium.
- `user01` could be targeted for Microsoft 365 Apps deployment.

---

### App configuration validation

Validation confirmed that:

- Microsoft 365 Apps app type was selected in Intune.
- App suite information was configured.
- XML configuration was used.
- `O365BusinessRetail` was configured as the Product ID.
- Current Channel and 64-bit installation were configured.

---

### Assignment validation

Validation confirmed that:

- Microsoft 365 Apps was assigned as **Required**.
- The target assignment group was `GRP-Pilot-Users`.
- The required install intent reached `WIN-CORP-001`.

---

### Installation validation

Validation confirmed that:

- Microsoft 365 Apps changed from waiting status to installed status.
- The managed apps view showed the app as installed.
- Microsoft 365 Apps installed successfully after Autopilot enrollment.
- Company Portal showed required apps installed after Autopilot provisioning.

---

## Final test result

| Validation item | Status |
|---|---|
| Microsoft 365 Apps license confirmed for user01 | Completed |
| Microsoft 365 Apps app type selected in Intune | Completed |
| App suite information configured | Completed |
| XML configuration used | Completed |
| O365BusinessRetail Product ID configured | Completed |
| App assigned as Required to GRP-Pilot-Users | Completed |
| App created in Intune | Completed |
| Assignment reached WIN-CORP-001 | Completed |
| Managed apps page showed Required install intent | Completed |
| Microsoft 365 Apps install status changed to Installed | Completed |
| Microsoft 365 Apps installed on endpoint | Completed |
| Autopilot validation device enrolled | Completed |
| Microsoft 365 Apps installed after Autopilot enrollment | Completed |
| Company Portal showed installed apps after Autopilot | Completed |
| Screenshots uploaded | Completed |
| Final lab result | Completed |

Observed final result:

```text
Microsoft 365 Apps installed successfully through Intune and were validated after Windows Autopilot enrollment.
```

---

## Screenshots captured

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

## Screenshot file list

```text
m365-user-license-assignment-sanitized.png
m365-app-type-selection-sanitized.png
m365-app-suite-information-sanitized.png
m365-app-suite-settings-sanitized.png
m365-required-assignment-sanitized.png
m365-managed-apps-waiting-status-sanitized.png
m365-managed-apps-installed-status-sanitized.png
autopilot-managed-apps-installed-sanitized.png
company-portal-installed-apps-after-autopilot-sanitized.png
```

---

## Troubleshooting notes

### Temporary waiting or failed status

During testing, the Microsoft 365 Apps deployment initially showed a waiting or failed state before later showing as installed from the device managed apps view.

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

---

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

---

### Office apps install but activation fails

If Word, Excel, or Outlook install but activation fails:

1. Confirm `user01` has the correct Microsoft 365 Apps license.
2. Confirm the device has internet access.
3. Confirm the user signs in with the correct work account.
4. Confirm there are no conflicting Office installations.
5. Sign out and sign back in to the Office app.
6. Restart the device and test again.

---

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

---

## Enterprise reflection

Microsoft 365 Apps deployment is a key part of modern Windows provisioning.

In production environments, admins should consider:

| Area | Recommendation |
|---|---|
| Licensing | Confirm users have valid Microsoft 365 Apps licenses |
| App suite configuration | Use XML for consistent app selection |
| Update channel | Match business requirements |
| Architecture | Use 64-bit unless there is a compatibility reason not to |
| Pilot rollout | Test with a small user group first |
| Autopilot integration | Validate apps after provisioning |
| Existing Office versions | Use RemoveMSI when needed |
| Reporting | Allow time for installation and Intune status updates |

A safer deployment model is:

```text
Create Microsoft 365 Apps deployment
-> Assign to pilot users
-> Validate on existing Intune device
-> Validate again after Autopilot enrollment
-> Expand to production users
```

This lab used `GRP-Pilot-Users` to validate the app deployment safely before broader rollout.

---

## Security and privacy notes

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
- Authentication prompts or codes
- Browser bookmarks if visible

---

## Related labs

| Lab file | Relationship |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Provides `user01` and `GRP-Pilot-Users` |
| `02-device-enrollment/windows-oobe-enrollment.md` | Provides the initial managed Windows test device |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Validates Microsoft 365 Apps after Autopilot enrollment |
| `05-application-deployment/microsoft-store-app-deployment.md` | Previous application deployment lab using Store apps |
| `05-application-deployment/win32-app-deployment-7zip.md` | Previous application deployment lab using Win32 app packaging |
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Next endpoint security lab after app deployment |

---

## Key learning outcomes

This lab demonstrated how to:

- Verify Microsoft 365 Apps licensing for a test user.
- Create a Microsoft 365 Apps deployment in Intune.
- Configure Microsoft 365 Apps using XML.
- Use the `O365BusinessRetail` Product ID.
- Assign Microsoft 365 Apps as a required app.
- Validate required app intent on a managed Windows device.
- Wait for and confirm installed status.
- Validate application deployment after Autopilot enrollment.
- Document real-world waiting/status behavior during Office deployment.

---

## Lab conclusion

The Microsoft 365 Apps deployment lab was completed successfully.

Final result:

```text
Microsoft 365 Apps were configured in Intune using XML.
The app was assigned as Required to GRP-Pilot-Users.
The required install intent reached WIN-CORP-001.
Microsoft 365 Apps installed successfully.
The deployment was also validated after Autopilot enrollment on WINAUTO452.
```

This confirms that the lab tenant can deploy productivity apps as part of a modern Intune and Autopilot provisioning workflow.
