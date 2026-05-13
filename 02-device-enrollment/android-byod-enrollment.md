# Android BYOD Enrollment with Work Profile

## Lab status

**Status:** Completed  
**Lab area:** Device enrollment  
**Platform:** Android Enterprise  
**Enrollment scenario:** Personally owned device with work profile  
**Primary test user:** `user03`  
**Assignment group:** `GRP-BYOD-Users`  
**Test device:** `ANDROID-BYOD-001`  
**Device model:** `moto g34 5G`  
**Android version:** `15`  
**Management:** Microsoft Intune  
**Ownership:** Personal / BYOD  
**Compliance result:** Compliant  

---

## Lab objective

The goal of this lab was to enroll a personally owned Android device into Microsoft Intune using the **Android Enterprise personally owned work profile** method.

This enrollment method separates personal and work data on the same Android device. Intune manages the work profile, while the personal profile remains outside Intune management.

This lab also validates a basic post-enrollment app deployment by assigning **Microsoft Authenticator** as a required Managed Google Play app to the BYOD user group.

---

## Why this lab matters

In a real environment, Android BYOD enrollment is used when employees use their personal Android phones for work access.

This approach helps the organization:

- Manage only the work profile
- Separate work apps and personal apps
- Deploy required work apps through Managed Google Play
- Apply compliance and app policies to work data
- Avoid full control over the user’s personal device

---

## Lab environment

| Item | Value |
|---|---|
| Tenant | HomeLab |
| Admin portal | Microsoft Intune admin center |
| Enrollment type | Android Enterprise personally owned work profile |
| User | `user03` |
| User group | `GRP-BYOD-Users` |
| Device | `ANDROID-BYOD-001` |
| Model | `moto g34 5G` |
| Android version | `15` |
| App deployment test | Microsoft Authenticator |
| App assignment type | Required |
| App target group | `GRP-BYOD-Users` |

---

## Prerequisites validated

Before enrolling the Android BYOD device, the following prerequisites were checked.

| Requirement | Result |
|---|---|
| Managed Google Play connected to Intune | Completed |
| Android Enterprise work profile enrollment allowed | Completed |
| Personally owned Android enrollment allowed | Completed |
| Test user has Intune-capable licensing | Completed |
| Test user is a member of `GRP-BYOD-Users` | Completed |
| Android device available for enrollment | Completed |

---

## Screenshot evidence

All screenshots for this lab are stored in:

```text
screenshots/sanitized/device-enrollment/
```

| Screenshot | Purpose |
|---|---|
| `android-byod-managed-google-play-connected-sanitized.png` | Shows Managed Google Play connected/setup in Intune |
| `android-byod-platform-restriction-sanitized.png` | Shows Android Enterprise work profile and personally owned enrollment allowed |
| `android-byod-001-device-details-sanitized.png` | Shows Android device model and Android version |
| `android-byod-001-company-portal-signin-sanitized.png` | Shows Company Portal app used for enrollment |
| `android-byod-001-intune-android-devices-list-sanitized.png` | Shows enrolled Android device in Intune Android devices list |
| `android-byod-001-intune-overview-sanitized.png` | Shows device overview with Personal, Intune, Compliant, Android work profile |
| `android-byod-authenticator-required-assignment-sanitized.png` | Shows Microsoft Authenticator assigned as Required to `GRP-BYOD-Users` |
| `android-byod-001-work-profile-apps-with-authenticator-sanitized.png` | Shows Authenticator installed inside the Android Work profile |
| `android-byod-android-apps-assigned-list-sanitized.png` | Shows Android app list with assigned app status |

---

## Step 1: Connect Managed Google Play

Path used:

```text
Microsoft Intune admin center
> Devices
> Enrollment
> Android
> Managed Google Play
```

Managed Google Play was connected to Intune so that Android Enterprise enrollment and app deployment could be used.

During setup, the Microsoft Entra-based Google Admin account creation did not complete successfully. The fallback **limited account** option was used to complete Android Enterprise setup.

Final result:

```text
Managed Google Play status: Setup / Connected
Organization: HomeLab
```

Screenshot:

![Managed Google Play connected](../screenshots/sanitized/device-enrollment/android-byod-managed-google-play-connected-sanitized.png)

---

## Step 2: Verify Android enrollment restrictions

Path used:

```text
Microsoft Intune admin center
> Devices
> Enrollment
> Device platform restrictions
> Android restrictions
> All Users
```

The default Android restriction policy was reviewed.

Required settings:

| Setting | Expected | Result |
|---|---|---|
| Android Enterprise work profile platform | Allow | Allow |
| Personally owned devices | Allow | Allow |

Screenshot:

![Android platform restriction](../screenshots/sanitized/device-enrollment/android-byod-platform-restriction-sanitized.png)

---

## Step 3: Review Android device details

On the Android phone, the device details were reviewed before enrollment.

Captured details:

| Item | Value |
|---|---|
| Model | `moto g34 5G` |
| Android version | `15` |

Screenshot:

![Android device details](../screenshots/sanitized/device-enrollment/android-byod-001-device-details-sanitized.png)

---

## Step 4: Install and open Company Portal

On the Android phone, the **Intune Company Portal** app was installed/opened from Google Play.

Company Portal is used for personal Android work profile enrollment.

Screenshot:

![Company Portal sign-in](../screenshots/sanitized/device-enrollment/android-byod-001-company-portal-signin-sanitized.png)

---

## Step 5: Sign in as BYOD test user

The Android phone was enrolled using:

```text
user03
```

Company Portal started the Android Enterprise personally owned work profile enrollment process.

During the enrollment flow, Android created a separate **Work profile** on the device.

---

## Step 6: Confirm Android work profile creation

After enrollment, the Android app drawer showed separate Personal and Work areas.

The Work profile included work-badged apps such as:

- Company Portal
- Contacts
- Files
- Play Store
- Microsoft Authenticator

Screenshot:

![Android work profile apps with Authenticator](../screenshots/sanitized/device-enrollment/android-byod-001-work-profile-apps-with-authenticator-sanitized.png)

---

## Step 7: Verify device in Intune

Path used:

```text
Microsoft Intune admin center
> Devices
> Android
> Android devices
```

The enrolled Android device appeared in the Android devices list.

Observed result:

| Field | Result |
|---|---|
| Managed by | Intune |
| Ownership | Personal |
| Compliance | Compliant |
| OS | Android personally owned work profile |
| OS version | 15.0 |
| Primary user | user03 |

Screenshot:

![Android devices list](../screenshots/sanitized/device-enrollment/android-byod-001-intune-android-devices-list-sanitized.png)

---

## Step 8: Verify Android device overview

The Android device record was opened in Intune.

Observed result:

| Field | Result |
|---|---|
| Compliance | Compliant |
| Ownership | Personal |
| Managed by | Intune |
| Primary user | User 03 |
| Model | moto g34 5G |
| Manufacturer | motorola |
| OS | Android personally owned work profile |
| Last check-in | Successful |

Screenshot:

![Android Intune overview](../screenshots/sanitized/device-enrollment/android-byod-001-intune-overview-sanitized.png)

---

## Step 9: Deploy Microsoft Authenticator to the work profile

After enrollment, a post-enrollment app deployment test was completed.

Path used:

```text
Microsoft Intune admin center
> Apps
> Android
> Android apps
> Microsoft Authenticator
> Properties
> Assignments
```

Assignment configured:

| Setting | Value |
|---|---|
| App | Microsoft Authenticator |
| App type | Managed Google Play app |
| Assignment type | Required |
| Included group | `GRP-BYOD-Users` |
| Status | Active |

Screenshot:

![Microsoft Authenticator required assignment](../screenshots/sanitized/device-enrollment/android-byod-authenticator-required-assignment-sanitized.png)

---

## Step 10: Confirm app deployment in the work profile

After policy sync/check-in, Microsoft Authenticator appeared inside the Android Work profile with a work badge.

This confirmed that the required Managed Google Play app assignment successfully installed the app into the managed work profile.

Screenshot:

![Authenticator installed in work profile](../screenshots/sanitized/device-enrollment/android-byod-001-work-profile-apps-with-authenticator-sanitized.png)

---

## Step 11: Review Android app assignment list

The Android apps list showed assigned status for the Android work profile app deployment test.

Screenshot:

![Android apps assigned list](../screenshots/sanitized/device-enrollment/android-byod-android-apps-assigned-list-sanitized.png)

---

## Final validation

| Validation item | Result |
|---|---|
| Managed Google Play connected | Passed |
| Android Enterprise work profile allowed | Passed |
| Personally owned Android enrollment allowed | Passed |
| Android BYOD device enrolled | Passed |
| Work profile created | Passed |
| Device visible in Intune | Passed |
| Device managed by Intune | Passed |
| Device ownership shown as Personal | Passed |
| Device compliance shown as Compliant | Passed |
| Microsoft Authenticator assigned as Required | Passed |
| Microsoft Authenticator installed in Work profile | Passed |

---

## Troubleshooting notes

### Managed Google Play setup

The initial Microsoft Entra-based Google Admin account creation did not complete successfully. The fallback **limited account** option was used to complete Managed Google Play setup.

This still allowed Intune to connect to Managed Google Play and continue Android Enterprise work profile enrollment testing.

### Managed Google Play app picker

The Managed Google Play app picker initially loaded as a blank screen when trying to add additional apps. Instead of blocking the lab, an already available Managed Google Play app, **Microsoft Authenticator**, was assigned as Required to `GRP-BYOD-Users`.

### App install delay

The Microsoft Authenticator app did not appear immediately in the Work profile. After waiting and allowing sync/check-in to complete, the app appeared in the Work profile.

This is expected behavior because app delivery can take time after Intune assignment and Google Play synchronization.

---

## Key learning points

- Android BYOD enrollment should use Android Enterprise personally owned work profile.
- Managed Google Play is required for Android Enterprise app management in Intune.
- Company Portal is used by personal Android users to enroll and create the work profile.
- Intune manages the Work profile, not the full personal device.
- Apps deployed through Managed Google Play install into the Work profile.
- Required assignments can be used to automatically install apps for targeted users.
- `GRP-BYOD-Users` is the correct group for BYOD app assignment in this lab.

---

## Recommended next steps

Possible next labs:

1. Create `ios-byod-enrollment.md`
2. Create `android-managed-google-play-app-deployment.md`
3. Add Outlook, Teams, Edge, and OneDrive as Managed Google Play apps
4. Create Android app configuration policy for a supported app
5. Create Android app protection policy for MAM controls
6. Continue with Attack Surface Reduction policy lab

---

## Microsoft Learn references

- [Android Enterprise work profile management overview](https://learn.microsoft.com/en-us/mem/intune-service/enrollment/android-enterprise-overview)
- [Set up enrollment of Android Enterprise personally owned work profile devices](https://learn.microsoft.com/en-us/intune/device-enrollment/android/setup-personal-work-profile)
- [Add and assign Managed Google Play apps to Android Enterprise devices](https://learn.microsoft.com/en-us/intune/app-management/deployment/add-managed-google-play)
