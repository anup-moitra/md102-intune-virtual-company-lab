# Android Managed Google Play App Deployment

## Lab status

**Status:** Completed  
**Lab category:** Application deployment  
**Platform:** Android Enterprise  
**Enrollment scenario:** Android BYOD personally owned device with work profile  
**Management platform:** Microsoft Intune  
**App source:** Managed Google Play  
**Target group:** GRP-BYOD-Users  
**Test user:** user03  
**Test device:** ANDROID-BYOD-001  
**Apps deployed:** Microsoft Outlook, Microsoft Teams  
**Assignment type:** Required  
**Final result:** Outlook and Teams installed successfully inside the Android Work profile  

---

## Lab objective

The objective of this lab is to deploy additional work apps to an already enrolled Android BYOD work profile device using Managed Google Play and Microsoft Intune.

This lab validates that Android Enterprise work profile apps can be:

- Added from Managed Google Play.
- Synced into Intune.
- Assigned to a BYOD user group.
- Installed inside the Android Work profile.
- Validated from the endpoint app drawer.

The proof apps for this lab were:

```text
Microsoft Outlook
Microsoft Teams
```

---

## Why this lab matters

In a real organization, Android BYOD users often need work apps such as Outlook, Teams, Edge, OneDrive, and Authenticator inside the managed Work profile.

The Work profile keeps corporate apps and data separate from the user's personal apps and data.

Simple flow:

```text
Admin adds app from Managed Google Play
-> App syncs into Intune
-> App is assigned to BYOD user group
-> Android Work profile receives the app
-> User sees the app with a work badge
```

This lab demonstrates the app deployment flow used by Intune administrators to deliver work apps to personal Android devices.

---

## Lab environment

| Item | Value |
|---|---|
| Admin portal | Microsoft Intune admin center |
| Platform | Android Enterprise |
| Enrollment type | Personally owned device with work profile |
| App source | Managed Google Play |
| Target group | GRP-BYOD-Users |
| Test user | user03 |
| Test device | ANDROID-BYOD-001 |
| Apps deployed | Microsoft Outlook, Microsoft Teams |
| Deployment type | Required assignment |
| Result | Apps installed in Android Work profile |

---

## Prerequisites

The following prerequisite lab was completed first:

```text
02-device-enrollment/android-byod-enrollment.md
```

That lab confirmed:

- Managed Google Play was connected to Intune.
- Android Enterprise personally owned work profile enrollment was enabled.
- `user03` successfully enrolled an Android BYOD device.
- The device appeared in Intune as Personal, Intune managed, and Compliant.
- The Android Work profile was created successfully.

---

## Configuration flow

```text
Open Android apps in Intune
-> Add Managed Google Play app
-> Search/select Microsoft Outlook
-> Approve/sync the app into Intune
-> Confirm Outlook and Teams appear in Android apps
-> Assign app as Required to GRP-BYOD-Users
-> Allow Android Work profile to sync
-> Confirm Outlook and Teams installed in Work profile
```

---

## Steps performed

### Step 1 - Opened Android apps in Intune

Path used:

```text
Microsoft Intune admin center
-> Apps
-> Android
-> Android apps
```

This page shows Android apps that are available in Intune.

Before this lab, default Android Enterprise apps were already available, such as:

- Intune Company Portal
- Microsoft Authenticator
- Microsoft Intune
- Managed Home Screen

---

### Step 2 - Added Microsoft Outlook from Managed Google Play

Path used:

```text
Microsoft Intune admin center
-> Apps
-> Android
-> Android apps
-> Create
-> Managed Google Play app
```

The Managed Google Play picker was opened from Intune.

The following app was searched and selected:

```text
Microsoft Outlook
Publisher: Microsoft Corporation
```

Outlook was approved/selected in Managed Google Play so it could be synced into Intune.

![Microsoft Outlook approved in Managed Google Play](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-approved-sanitized.png)

---

### Step 3 - Troubleshot Managed Google Play picker loading issue

During the first attempt, the Managed Google Play app picker opened as a blank screen.

The issue was resolved by opening the Intune admin center in an InPrivate browser session and repeating the app picker workflow.

This indicated the issue was browser/session related, not a broken Intune or Managed Google Play connector.

Troubleshooting notes:

- Managed Google Play connector status was already `Setup`.
- Android BYOD enrollment was already working.
- Default Managed Google Play apps were already available in Intune.
- The app picker loaded correctly in InPrivate mode.

---

### Step 4 - Synced Managed Google Play apps into Intune

After selecting the app in Managed Google Play, the app was synced into Intune.

Path used:

```text
Apps
-> Android
-> Android apps
-> Refresh
```

After sync and refresh, the following apps appeared in the Android apps list:

- Microsoft Outlook
- Microsoft Teams

Both apps showed as Android Managed Google Play store apps.

![Outlook and Teams added and assigned](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-teams-added-assigned-sanitized.png)

---

### Step 5 - Assigned Microsoft Outlook as a required app

Path used:

```text
Apps
-> Android
-> Android apps
-> Microsoft Outlook
-> Properties
-> Assignments
-> Edit
```

Assignment configured:

| Setting | Value |
|---|---|
| App | Microsoft Outlook |
| App type | Managed Google Play store app |
| Assignment type | Required |
| Included group | GRP-BYOD-Users |
| Status | Active |

![Microsoft Outlook required assignment](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-required-assignment-sanitized.png)

---

### Step 6 - Verified app installation in Android Work profile

After the Android device synced with Intune and Managed Google Play, the Work profile app drawer was checked.

The following additional apps appeared in the Work profile:

- Outlook
- Teams

Both apps were shown with the Android Work profile badge, confirming that they were installed in the managed Work profile rather than the personal profile.

![Outlook and Teams installed in Android Work profile](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-teams-installed-work-profile-sanitized.png)

---

## Validation

Validation confirmed that:

- Managed Google Play picker loaded successfully in InPrivate mode.
- Microsoft Outlook was selected/approved from Managed Google Play.
- Microsoft Outlook synced into Intune.
- Microsoft Teams synced into Intune.
- Outlook assignment was configured as Required.
- The target group was `GRP-BYOD-Users`.
- Outlook installed in the Android Work profile.
- Teams installed in the Android Work profile.
- Work apps showed the Android Work profile badge.

---

## Final test result

| Validation item | Result |
|---|---|
| Managed Google Play picker loaded in InPrivate mode | Passed |
| Microsoft Outlook selected/approved from Managed Google Play | Passed |
| Microsoft Outlook synced into Intune | Passed |
| Microsoft Teams synced into Intune | Passed |
| Outlook assignment configured | Passed |
| Outlook targeted to GRP-BYOD-Users | Passed |
| Outlook installed in Android Work profile | Passed |
| Teams installed in Android Work profile | Passed |
| Work apps show Android Work profile badge | Passed |
| Final lab result | Completed |

Observed final result:

```text
Microsoft Outlook and Microsoft Teams were successfully added from Managed Google Play, synced into Intune, assigned to the Android BYOD user group, and installed inside the Android Work profile.
```

---

## Screenshots captured

Screenshots for this lab are stored in:

```text
screenshots/sanitized/application-deployment/
```

| Screenshot | Purpose |
|---|---|
| `android-managed-google-play-outlook-approved-sanitized.png` | Shows Microsoft Outlook approved/selected from Managed Google Play |
| `android-managed-google-play-outlook-required-assignment-sanitized.png` | Shows Microsoft Outlook assigned as Required to GRP-BYOD-Users |
| `android-managed-google-play-outlook-teams-added-assigned-sanitized.png` | Shows Outlook and Teams added to Intune Android apps and assigned |
| `android-managed-google-play-outlook-teams-installed-work-profile-sanitized.png` | Shows Outlook and Teams installed in the Android Work profile |

---

## Troubleshooting notes

### Managed Google Play picker blank screen

During the first attempt, the Managed Google Play picker loaded as a blank screen.

Resolution:

```text
Opened Intune admin center in an InPrivate browser session.
Repeated the Managed Google Play app picker workflow.
The picker loaded successfully.
```

This appears to have been a browser/session issue.

---

### App installation delay

Android Managed Google Play app installation may not be immediate.

If apps do not appear quickly:

1. Confirm the app is assigned as Required.
2. Confirm the user is in `GRP-BYOD-Users`.
3. Confirm the Android device has a Work profile.
4. Confirm the device has internet connectivity.
5. Wait for Intune and Managed Google Play synchronization.
6. Reopen the Work profile app drawer.

---

## Enterprise reflection

Managed Google Play is the standard app source for Android Enterprise work profile devices.

In production, administrators should:

- Use BYOD groups for personal Android work profile users.
- Deploy required apps only when needed.
- Use available apps for optional/self-service work apps.
- Combine app deployment with compliance and app protection policies.
- Explain to users that work apps are separated from personal apps.
- Validate app installation from the Work profile, not the personal profile.

A good rollout model is:

```text
Android BYOD pilot group
-> Required core work apps
-> Optional productivity apps
-> Compliance policy
-> App protection policy
-> Conditional Access enforcement
```

---

## Security and privacy notes

This is a public learning repository.

Do not upload screenshots showing:

- Full real email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Android IMEI numbers
- Phone numbers
- Personal app data
- Personal notifications
- MFA prompts
- Verification codes
- Unsanitized tenant information
- Production company data

---

## Related labs

| Lab file | Relationship |
|---|---|
| `02-device-enrollment/android-byod-enrollment.md` | Provides the enrolled Android Enterprise work profile device |
| `02-device-enrollment/ios-byod-enrollment.md` | iOS/iPadOS BYOD enrollment comparison lab |
| `05-application-deployment/microsoft-store-app-deployment.md` | Windows app deployment comparison lab |
| `04-compliance-and-conditional-access/conditional-access-compliant-device.md` | Future Conditional Access validation |

---

## Key learning outcomes

This lab demonstrated how to:

- Add Managed Google Play apps to Intune.
- Approve/sync Android work apps.
- Assign Android Managed Google Play apps to a BYOD user group.
- Validate Android Work profile app installation.
- Troubleshoot a blank Managed Google Play picker using InPrivate mode.
- Understand the difference between personal Android apps and Work profile apps.

---

## Lab conclusion

The Android Managed Google Play app deployment lab was completed successfully.

Final result:

```text
Microsoft Outlook and Microsoft Teams were added from Managed Google Play.
The apps synced into Intune.
Outlook was assigned as Required to GRP-BYOD-Users.
Outlook and Teams installed successfully inside the Android Work profile.
```

This confirms that Intune can deploy additional Android work apps to personally owned Android Enterprise work profile devices.
