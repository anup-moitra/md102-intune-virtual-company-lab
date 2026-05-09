# Microsoft 365 Apps Deployment for Autopilot Lab

This file documents the Microsoft 365 Apps deployment created in Microsoft Intune for the Windows Autopilot lab.

## Objective

The objective of this lab is to deploy Microsoft 365 Apps to a Windows device during or after Windows Autopilot enrollment.

This lab validates that:

- A Microsoft 365 license can be assigned to a lab user.
- Microsoft 365 Apps can be created as an Intune app deployment.
- Selected Office apps can be assigned as required apps.
- The app deployment can support an Autopilot provisioning scenario.
- Outlook, Excel, and PowerPoint can later be tested after Autopilot enrollment.

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The project is testing a modern endpoint management flow:

```text
Windows Autopilot
→ Microsoft Entra join
→ Intune enrollment
→ Policy assignment
→ App deployment
→ User productivity app sign-in test
```

This app deployment is connected to the Autopilot lab because the user signs in during OOBE, the device enrolls into Intune, and assigned apps can then install automatically.

## Why This Lab Matters

In real organizations, newly provisioned corporate Windows laptops usually need productivity applications installed automatically.

Common required apps include:

- Outlook
- Excel
- PowerPoint
- Word
- Teams
- OneDrive
- Company Portal
- Security tools
- VPN clients
- Business applications

For this lab, the focus is on Microsoft 365 Apps because the future troubleshooting scenario involves Outlook, Excel, and PowerPoint sign-in behavior after Autopilot or hardware changes.

## Licensing Preparation

A Microsoft 365 Business Premium trial was activated for the lab tenant.

The license was assigned to:

```text
user01
```

The purpose of this license is to allow User 01 to use Microsoft 365 desktop apps and test sign-in/activation after Autopilot provisioning.

## License Details

| Item | Value |
|---|---|
| License product | Microsoft 365 Business Premium |
| Assigned user | user01 |
| Purpose | Enable Microsoft 365 Apps and productivity app testing |
| Apps to test | Outlook, Excel, PowerPoint |
| Related lab | Windows Autopilot user-driven enrollment |

## App Deployment Details

| Setting | Value |
|---|---|
| App name | Microsoft 365 Apps for Windows - Autopilot Lab |
| App type | Microsoft 365 Apps |
| Platform | Windows 10 and later |
| Publisher | Microsoft |
| Assignment type | Required |
| Target group | GRP-Pilot-Users |
| Test user | user01 |
| Related device | Autopilot test device |
| Install context | During or after Autopilot enrollment |

## Selected Microsoft 365 Apps

The following Microsoft 365 Apps were selected for this lab:

| App | Purpose |
|---|---|
| Outlook | Email and Microsoft 365 sign-in testing |
| Excel | Office activation and productivity app testing |
| PowerPoint | Office activation and productivity app testing |

> [!NOTE]
> Word, OneNote, Teams, Access, and Publisher were not the main focus of this lab. The selected apps match the future troubleshooting goal around Outlook, Excel, and PowerPoint behavior.

## App Suite Configuration

| Setting | Value |
|---|---|
| Architecture | 64-bit |
| Default file format | Office Open XML Format |
| Update channel | Current Channel |
| Version to install | Latest |
| Remove other versions | Yes |
| Shared computer activation | No |
| Accept Microsoft Software License Terms | Yes |
| Install background service for Microsoft Search in Bing | No / Not required for this lab |

## Assignment

The app was assigned as a required app.

| Assignment setting | Value |
|---|---|
| Assignment type | Required |
| Target group | GRP-Pilot-Users |
| Reason | User 01 is a member of the pilot users group and is used for Autopilot sign-in testing |

## Why Required Assignment Was Used

A required assignment installs the app automatically for targeted users or devices.

This is useful in Autopilot scenarios because a newly provisioned corporate device should receive required business apps without the user manually installing them.

Simple flow:

```text
User 01 signs in during Autopilot
→ Device enrolls into Intune
→ Intune evaluates required app assignments
→ Microsoft 365 Apps deployment applies
→ Outlook, Excel, and PowerPoint install or become available
```

## Steps Performed

### Step 1: Activated Microsoft 365 Business Premium Trial

A Microsoft 365 Business Premium trial was activated in the Microsoft 365 admin center.

This added Microsoft 365 Apps licensing capability to the lab tenant.

### Step 2: Assigned License to User 01

The Microsoft 365 Business Premium license was assigned to:

```text
user01
```

Navigation used:

```text
Microsoft 365 admin center
→ Users
→ Active users
→ user01
→ Licenses and apps
→ Microsoft 365 Business Premium
→ Save changes
```

### Step 3: Created Microsoft 365 Apps Deployment in Intune

Navigation used:

```text
Intune admin center
→ Apps
→ All apps
→ Add
→ Microsoft 365 Apps
→ Windows 10 and later
```

### Step 4: Configured App Information

The app suite was named:

```text
Microsoft 365 Apps for Windows - Autopilot Lab
```

Description used:

```text
Deploys Microsoft 365 Apps to Autopilot-enrolled Windows devices for the MD-102 lab.
```

### Step 5: Selected Office Apps

The following apps were selected:

```text
Outlook
Excel
PowerPoint
```

### Step 6: Configured App Suite Settings

The following settings were selected:

```text
Architecture: 64-bit
Default file format: Office Open XML Format
Update channel: Current Channel
Version to install: Latest
Remove other versions: Yes
Shared computer activation: No
Accept Microsoft Software License Terms: Yes
```

### Step 7: Assigned the App

The app was assigned as:

```text
Required
```

Target group:

```text
GRP-Pilot-Users
```

### Step 8: Connected This App Deployment to Autopilot

The app assignment was created before completing the Autopilot OOBE test.

This allows the app deployment to be evaluated when User 01 signs in and the device enrolls into Intune.

## Test Plan

The following test will be completed after Autopilot OOBE sign-in finishes.

| Test item | Expected result |
|---|---|
| Autopilot device enrolls into Intune | Device appears in Intune |
| User 01 signs in during OOBE | Sign-in succeeds |
| Device becomes Microsoft Entra joined | Join type shows Microsoft Entra joined |
| Device becomes Intune managed | Managed by Intune |
| Microsoft 365 Apps assignment applies | App install begins or completes |
| Outlook opens | User 01 can sign in |
| Excel opens | User 01 can sign in / activate |
| PowerPoint opens | User 01 can sign in / activate |

## Current Lab Status

| Task | Status |
|---|---|
| Microsoft 365 Business Premium trial activated | Completed |
| License assigned to user01 | Completed |
| Microsoft 365 Apps deployment created | Completed |
| Outlook selected | Completed |
| Excel selected | Completed |
| PowerPoint selected | Completed |
| App assigned as Required to GRP-Pilot-Users | Completed |
| Autopilot OOBE sign-in completed | Pending |
| Microsoft 365 Apps install verified | Pending |
| Outlook sign-in tested | Pending |
| Excel sign-in tested | Pending |
| PowerPoint sign-in tested | Pending |
| Screenshots added | Pending |

## Screenshots

The following screenshots should be added after sanitizing sensitive information.

> [!NOTE]
> Screenshots must be sanitized before upload. Hide tenant names, full email addresses, device IDs, serial numbers, object IDs, request IDs, correlation IDs, IP addresses, and any sensitive information.

### Microsoft 365 Business Premium license assigned to User 01

![Microsoft 365 Business Premium license assigned](../screenshots/sanitized/application-deployment/m365-business-premium-license-user01-sanitized.jpg)

### Microsoft 365 Apps app information

![Microsoft 365 Apps app information](../screenshots/sanitized/application-deployment/m365-apps-autopilot-app-info-sanitized.jpg)

### Microsoft 365 Apps selected apps

![Microsoft 365 Apps selected apps](../screenshots/sanitized/application-deployment/m365-apps-selected-apps-sanitized.jpg)

### Microsoft 365 Apps assignment

![Microsoft 365 Apps assignment](../screenshots/sanitized/application-deployment/m365-apps-required-assignment-sanitized.jpg)

### Microsoft 365 Apps install status

![Microsoft 365 Apps install status](../screenshots/sanitized/application-deployment/m365-apps-install-status-sanitized.jpg)

### Outlook sign-in test

![Outlook sign-in test](../screenshots/sanitized/application-deployment/outlook-signin-test-sanitized.jpg)

### Excel sign-in test

![Excel sign-in test](../screenshots/sanitized/application-deployment/excel-signin-test-sanitized.jpg)

### PowerPoint sign-in test

![PowerPoint sign-in test](../screenshots/sanitized/application-deployment/powerpoint-signin-test-sanitized.jpg)

## Screenshot Folder Path

Screenshots for this lab should be stored in:

```text
screenshots/sanitized/application-deployment/
```

Suggested screenshot filenames:

```text
m365-business-premium-license-user01-sanitized.jpg
m365-apps-autopilot-app-info-sanitized.jpg
m365-apps-selected-apps-sanitized.jpg
m365-apps-required-assignment-sanitized.jpg
m365-apps-install-status-sanitized.jpg
outlook-signin-test-sanitized.jpg
excel-signin-test-sanitized.jpg
powerpoint-signin-test-sanitized.jpg
```

## Troubleshooting Notes

If Microsoft 365 Apps do not install immediately, check the following:

1. Confirm the app is assigned as Required.
2. Confirm User 01 is a member of GRP-Pilot-Users.
3. Confirm User 01 has a Microsoft 365 Business Premium license.
4. Confirm the Autopilot device is enrolled in Intune.
5. Confirm the device has internet access.
6. Check the app install status in Intune.
7. Sync the device from Windows settings.
8. Restart the device if required.
9. Wait for Intune check-in and Office installation processing.

If Outlook, Excel, or PowerPoint opens but does not activate, check:

1. User 01 license assignment.
2. Office activation status.
3. Internet connectivity.
4. Microsoft 365 service availability.
5. Whether the user is signed in with the correct account.
6. Whether old Office installations exist on the device.

## Security and Privacy Notes

This is a public learning repository.

Do not upload sensitive information, including:

- Full real email addresses
- Tenant IDs
- Device IDs
- Serial numbers
- Autopilot hardware hashes
- Object IDs
- Request IDs
- Correlation IDs
- IP addresses
- Unsanitized screenshots
- Real production company information

## What This Lab Proves

This lab proves that Microsoft Intune can be used to deploy Microsoft 365 Apps to a Windows device as part of a modern Autopilot provisioning workflow.

Simple explanation:

```text
Microsoft 365 Business Premium license assigned to User 01
→ Microsoft 365 Apps deployment created in Intune
→ Outlook, Excel, and PowerPoint selected
→ App assigned as Required to GRP-Pilot-Users
→ User 01 signs in during Autopilot
→ Device enrolls into Intune
→ Apps install or become available
→ User signs in to Office apps
```

## Future Troubleshooting Connection

This lab also supports a future troubleshooting scenario.

Planned future scenario:

```text
Autopilot / Intune-managed laptop after motherboard replacement
→ User signs in
→ Outlook / Excel / PowerPoint sign-in issue occurs
→ Troubleshoot Entra device identity, Intune enrollment, Autopilot record, TPM, and Office activation
```

This will be documented later as a separate troubleshooting lab.

## Next Step

Complete the Autopilot OOBE sign-in with:

```text
user01
```

Then verify:

```text
Device appears in Intune
Device is Microsoft Entra joined
Device is managed by Intune
Microsoft 365 Apps install status
Outlook sign-in
Excel sign-in
PowerPoint sign-in
```
