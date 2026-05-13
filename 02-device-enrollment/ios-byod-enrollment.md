# iOS BYOD Enrollment

## Lab status

**Status:** In Progress  
**Current stage:** Admin prerequisites completed  
**Pending:** Physical iPhone/iPad enrollment and Intune device validation  
**Lab area:** Device enrollment  
**Platform:** iOS/iPadOS  
**Enrollment scenario:** BYOD / personally owned device enrollment  
**Target group:** `GRP-BYOD-Users`  
**Test user:** `User 04`  
**Planned device name:** `IOS-BYOD-001`

---

## Lab objective

The goal of this lab is to enroll a personally owned iPhone or iPad into Microsoft Intune using the Company Portal app.

At this stage, the admin-side prerequisites have been completed. The actual device enrollment is pending because a physical iPhone/iPad test device is not currently available.

When the device is available, this lab will validate that the iOS/iPadOS BYOD device appears in Intune as:

- Managed by Intune
- Personally owned
- Assigned to the correct primary user
- Enrolled through Company Portal
- Visible under iOS/iPadOS devices
- Compliant or ready for compliance evaluation

---

## Why this lab matters

iOS/iPadOS BYOD enrollment is a common real-world Intune scenario.

In many organizations, users bring their own iPhones or iPads and access company resources such as Outlook, Teams, OneDrive, and SharePoint. Intune allows administrators to manage the work-related side of the device while keeping the user’s personal data separate.

This lab documents the Intune-side preparation required before enrolling a personal iOS/iPadOS device.

---

## Prerequisites completed

| Requirement | Status |
|---|---|
| iOS/iPadOS platform enrollment allowed | Completed |
| Personally owned iOS/iPadOS devices allowed | Completed |
| BYOD user group confirmed | Completed |
| Test user license confirmed | Completed |
| Apple MDM Push Certificate created | Completed |
| Apple MDM Push Certificate uploaded to Intune | Completed |
| Apple MDM Push Certificate active in Intune | Completed |
| Physical iPhone/iPad enrollment | Pending |
| Intune iOS device validation | Pending |

---

## Lab environment

| Item | Value |
|---|---|
| Admin portal | Microsoft Intune admin center |
| Identity portal | Microsoft Entra admin center |
| User portal | Microsoft 365 admin center |
| Platform | iOS/iPadOS |
| Enrollment type | Personally owned / BYOD |
| Target group | `GRP-BYOD-Users` |
| Test user | `User 04` |
| License | Intune |
| Apple service used | Apple Push Certificates Portal |
| Current result | Admin prerequisites completed |

---

## Screenshot evidence

Screenshots for this lab are stored in:

```text
screenshots/sanitized/device-enrollment/
```

| Screenshot | Purpose |
|---|---|
| `ios-byod-platform-restriction-sanitized.png` | Shows iOS/iPadOS enrollment and personally owned devices are allowed |
| `ios-byod-user-byod-group-membership-sanitized.png` | Shows the test user is a member of `GRP-BYOD-Users` |
| `ios-byod-user-license-sanitized.png` | Shows the test user has an Intune license |
| `ios-byod-apple-push-certificate-create-sanitized.png` | Shows Apple Push Certificate creation using the Intune CSR |
| `ios-byod-apple-push-certificate-confirmation-sanitized.png` | Shows Apple Push Certificate creation confirmation |
| `ios-byod-apple-mdm-push-certificate-configure-sanitized.png` | Shows the Intune Apple MDM Push Certificate configuration page |
| `ios-byod-apple-mdm-push-certificate-upload-sanitized.png` | Shows the Apple MDM Push Certificate selected for upload |
| `ios-byod-apple-mdm-push-certificate-active-sanitized.png` | Shows the Apple MDM Push Certificate active in Intune |

---

## Step 1: Confirm iOS/iPadOS enrollment restrictions

Path used:

```text
Microsoft Intune admin center
> Devices
> Enrollment
> Device platform restrictions
> All Users
> Properties
```

The default enrollment restriction was reviewed.

The following settings were confirmed:

| Platform | Platform setting | Personally owned |
|---|---|---|
| iOS/iPadOS | Allow | Allow |

This confirms that personal iOS/iPadOS devices are allowed to enroll into Intune.

Screenshot:

![iOS BYOD platform restriction](../screenshots/sanitized/device-enrollment/ios-byod-platform-restriction-sanitized.png)

---

## Step 2: Confirm BYOD user group membership

Path used:

```text
Microsoft Entra admin center
> Groups
> GRP-BYOD-Users
> Members
```

The BYOD user group was checked to confirm that the test user is included.

Confirmed members included:

- `User 03`
- `User 04`

For this iOS BYOD lab, `User 04` is planned as the test user.

Screenshot:

![iOS BYOD user group membership](../screenshots/sanitized/device-enrollment/ios-byod-user-byod-group-membership-sanitized.png)

---

## Step 3: Confirm Intune license assignment

Path used:

```text
Microsoft 365 admin center
> Users
> Active users
> User 04
> Licenses and apps
```

The test user was checked for Intune licensing.

Confirmed license:

```text
Intune
```

This confirms the test user is eligible for Intune enrollment.

Screenshot:

![iOS BYOD user license](../screenshots/sanitized/device-enrollment/ios-byod-user-license-sanitized.png)

---

## Step 4: Create Apple MDM Push Certificate

Path used:

```text
Microsoft Intune admin center
> Devices
> Enrollment
> Apple
> Apple MDM Push Certificate
```

The Intune certificate signing request was downloaded and uploaded to the Apple Push Certificates Portal.

A new Apple MDM Push Certificate was created using the Apple Push Certificates Portal.

Screenshot:

![Apple Push Certificate creation](../screenshots/sanitized/device-enrollment/ios-byod-apple-push-certificate-create-sanitized.png)

---

## Step 5: Confirm Apple Push Certificate creation

After uploading the Intune CSR in the Apple Push Certificates Portal, Apple confirmed that the new push certificate was created successfully.

The certificate was created for:

```text
Service: Mobile Device Management
Vendor: Microsoft Corporation
```

Screenshot:

![Apple Push Certificate confirmation](../screenshots/sanitized/device-enrollment/ios-byod-apple-push-certificate-confirmation-sanitized.png)

---

## Step 6: Configure Apple MDM Push Certificate in Intune

Path used:

```text
Microsoft Intune admin center
> Devices
> Enrollment
> Apple
> Apple MDM Push Certificate
```

The Apple ID used to create the certificate was entered into Intune.

The downloaded Apple MDM Push Certificate file was selected for upload.

Screenshot:

![Configure Apple MDM Push Certificate](../screenshots/sanitized/device-enrollment/ios-byod-apple-mdm-push-certificate-configure-sanitized.png)

---

## Step 7: Upload Apple MDM Push Certificate

The Apple MDM Push Certificate file was uploaded to Intune.

Screenshot:

![Apple MDM Push Certificate upload](../screenshots/sanitized/device-enrollment/ios-byod-apple-mdm-push-certificate-upload-sanitized.png)

---

## Step 8: Verify Apple MDM Push Certificate status

After upload, the Apple MDM Push Certificate showed as active in Intune.

Confirmed status:

```text
Status: Active
Expiration date: Available
Days until expiration: Available
```

This confirms that Intune is ready to manage Apple devices.

Screenshot:

![Apple MDM Push Certificate active](../screenshots/sanitized/device-enrollment/ios-byod-apple-mdm-push-certificate-active-sanitized.png)

---

## Current result

The admin-side iOS/iPadOS BYOD enrollment prerequisites are complete.

Intune is now prepared for personal iPhone/iPad enrollment because:

- iOS/iPadOS enrollment is allowed
- Personally owned iOS/iPadOS devices are allowed
- The test user is in the BYOD user group
- The test user has an Intune license
- Apple MDM Push Certificate is active

The lab is paused until a physical iPhone/iPad test device is available.

---

## Pending device-side enrollment steps

When an iPhone/iPad is available, continue with the steps below.

### Step 9: Rename the iOS/iPadOS device

On the iPhone/iPad:

```text
Settings
> General
> About
> Name
```

Rename the device to:

```text
IOS-BYOD-001
```

Future screenshot:

```text
ios-byod-001-about-device-sanitized.png
```

Capture:

- Device name
- Model name
- iOS/iPadOS version

Sanitize:

- Serial number
- IMEI
- Phone number
- Wi-Fi address
- Bluetooth address
- EID
- Any other device identifiers

---

### Step 10: Install Company Portal

On the iPhone/iPad:

```text
App Store
> Search: Intune Company Portal
> Install
```

Open Company Portal and sign in with the BYOD test user.

Future screenshot:

```text
ios-byod-001-company-portal-signin-sanitized.png
```

---

### Step 11: Begin Company Portal enrollment

In Company Portal, follow the enrollment prompts.

Expected prompts may include:

- Set up access
- Begin
- Download management profile
- Allow profile download

Future screenshot:

```text
ios-byod-001-company-portal-begin-enrollment-sanitized.png
```

---

### Step 12: Download the management profile

When prompted, download the management profile.

Future screenshot:

```text
ios-byod-001-management-profile-downloaded-sanitized.png
```

---

### Step 13: Install the management profile

On the iPhone/iPad:

```text
Settings
> General
> VPN & Device Management
```

or:

```text
Settings
> Profile Downloaded
```

Install the management profile and trust remote management when prompted.

Future screenshot:

```text
ios-byod-001-management-profile-installed-sanitized.png
```

---

### Step 14: Complete enrollment in Company Portal

Return to Company Portal and allow it to finish checking the device.

Future screenshot:

```text
ios-byod-001-company-portal-enrollment-complete-sanitized.png
```

---

## Pending Intune validation steps

After device enrollment is complete, verify the device in Intune.

Path:

```text
Microsoft Intune admin center
> Devices
> iOS/iPadOS
> iOS/iPadOS devices
```

or:

```text
Devices
> All devices
```

Search for:

```text
IOS-BYOD-001
```

Expected result:

| Field | Expected value |
|---|---|
| Managed by | Intune |
| Ownership | Personal |
| Platform | iOS/iPadOS |
| Primary user | User 04 |
| Compliance | Compliant or evaluating |

Future screenshot:

```text
ios-byod-001-intune-ios-devices-list-sanitized.png
```

Open the device record and capture the overview page.

Future screenshot:

```text
ios-byod-001-intune-overview-sanitized.png
```

---

## Final validation checklist

| Validation item | Current status |
|---|---|
| iOS/iPadOS platform allowed | Completed |
| Personally owned iOS/iPadOS devices allowed | Completed |
| BYOD user group confirmed | Completed |
| Test user license confirmed | Completed |
| Apple MDM Push Certificate created | Completed |
| Apple MDM Push Certificate active in Intune | Completed |
| Company Portal installed on iPhone/iPad | Pending |
| iOS/iPadOS management profile installed | Pending |
| Device visible in Intune | Pending |
| Device ownership shows Personal | Pending |
| Device managed by Intune | Pending |
| Device compliance evaluated | Pending |

---

## Key learning points

- iOS/iPadOS enrollment requires an Apple MDM Push Certificate before Intune can manage Apple devices.
- The Apple MDM Push Certificate must be renewed yearly.
- The same Apple ID should be used when renewing the certificate.
- Device platform restrictions control whether personal iOS/iPadOS devices can enroll.
- A licensed Intune user is required for Company Portal enrollment.
- Physical device validation is required before the lab can be marked as completed.

---

## Result summary

The iOS/iPadOS BYOD enrollment prerequisites were completed successfully.

The lab remains in progress because a physical iPhone or iPad is required to complete Company Portal enrollment and validate the device in Intune.

---

## Related labs

- `02-device-enrollment/windows-byod-enrollment.md`
- `02-device-enrollment/android-byod-enrollment.md`
- `05-application-deployment/android-managed-google-play-app-deployment.md`

---

## Microsoft Learn references

- [Set up enrollment for iOS/iPadOS devices](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/ios-enroll)
- [Get an Apple MDM push certificate for Intune](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/apple-mdm-push-certificate-get)
- [Device platform enrollment restrictions in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/enrollment/enrollment-restrictions-set)
