# Android BYOD Enrollment with Work Profile

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Device enrollment |
| Platform | Android Enterprise |
| Enrollment scenario | Personally owned device with work profile |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Primary test user | user03 |
| Assignment group | GRP-BYOD-Users |
| Test device | ANDROID-BYOD-001 |
| Device model | moto g34 5G |
| Android version | 15 |
| Ownership | Personal / BYOD |
| Compliance result | Compliant |

---

## Lab Objective

Enroll a personally owned Android device into Microsoft Intune using Android Enterprise personally owned work profile enrollment, then validate that a Managed Google Play app deploys successfully to the work profile.

---

## Why This Lab Matters

Android Enterprise personally owned work profile is the recommended approach for employee-owned Android devices. It creates a separate managed work area on the phone without giving IT control over the personal side.

```text
Personal profile = user's own apps and data (unmanaged)
Work profile = company-managed apps and data (Intune managed)
```

This lets the organization deploy work apps, apply compliance policies, and protect corporate data — without touching anything personal on the device.

---

## Prerequisites

| Requirement | Status |
|---|---|
| Managed Google Play connected to Intune | Completed |
| Android Enterprise work profile enrollment allowed | Completed |
| Personally owned Android enrollment allowed | Completed |
| user03 has Intune-capable license | Completed |
| user03 is a member of GRP-BYOD-Users | Completed |
| Android device available for enrollment | Completed |

---

## Configuration Flow

```text
Connect Managed Google Play to Intune
-> Confirm Android Enterprise enrollment restrictions
-> Install/open Company Portal on Android device
-> Sign in as user03 and complete work profile enrollment
-> Verify device in Intune
-> Assign Microsoft Authenticator as Required to GRP-BYOD-Users
-> Confirm Authenticator installs in the Work profile
```

---

## Steps Performed

### Step 1 — Connected Managed Google Play

Navigated to:

```text
Devices -> Enrollment -> Android -> Managed Google Play
```

Connected Managed Google Play to Intune to enable Android Enterprise enrollment and app deployment. The Microsoft Entra-based Google Admin account creation did not complete successfully during setup — the fallback limited account option was used instead. This still allowed Intune to connect to Managed Google Play and proceed with enrollment.

![Managed Google Play connected](../screenshots/sanitized/device-enrollment/android-byod-managed-google-play-connected-sanitized.png)

---

### Step 2 — Verified Android enrollment restrictions

Navigated to:

```text
Devices -> Enrollment -> Device platform restrictions -> Android restrictions -> All Users
```

Confirmed the default Android restriction policy allowed both Android Enterprise work profile enrollment and personally owned devices.

![Android platform restriction](../screenshots/sanitized/device-enrollment/android-byod-platform-restriction-sanitized.png)

---

### Step 3 — Reviewed device details before enrollment

Confirmed device model and Android version on the test phone before starting enrollment.

| Item | Value |
|---|---|
| Model | moto g34 5G |
| Android version | 15 |

![Android device details](../screenshots/sanitized/device-enrollment/android-byod-001-device-details-sanitized.png)

---

### Step 4 — Enrolled through Company Portal

Opened Intune Company Portal on the Android device and signed in as `user03`. Company Portal started the Android Enterprise personally owned work profile enrollment flow. Android created a separate Work profile on the device during this process.

![Company Portal sign-in](../screenshots/sanitized/device-enrollment/android-byod-001-company-portal-signin-sanitized.png)

---

### Step 5 — Confirmed work profile creation

After enrollment, the Android app drawer showed separate Personal and Work areas. Work-badged apps appeared in the Work profile, including Company Portal, Contacts, Files, Play Store, and Microsoft Authenticator.

![Android work profile apps](../screenshots/sanitized/device-enrollment/android-byod-001-work-profile-apps-with-authenticator-sanitized.png)

---

### Step 6 — Verified device in Intune

Navigated to:

```text
Devices -> Android -> Android devices
```

| Field | Result |
|---|---|
| Managed by | Intune |
| Ownership | Personal |
| Compliance | Compliant |
| OS | Android personally owned work profile |
| OS version | 15.0 |
| Primary user | user03 |

![Android devices list](../screenshots/sanitized/device-enrollment/android-byod-001-intune-android-devices-list-sanitized.png)

![Android device overview](../screenshots/sanitized/device-enrollment/android-byod-001-intune-overview-sanitized.png)

---

### Step 7 — Deployed Microsoft Authenticator to the work profile

Navigated to:

```text
Apps -> Android -> Microsoft Authenticator -> Properties -> Assignments
```

| Setting | Value |
|---|---|
| App type | Managed Google Play app |
| Assignment type | Required |
| Included group | GRP-BYOD-Users |

![Microsoft Authenticator required assignment](../screenshots/sanitized/device-enrollment/android-byod-authenticator-required-assignment-sanitized.png)

After sync, Microsoft Authenticator appeared inside the Android Work profile with a work badge, confirming the required app assignment deployed successfully.

![Authenticator installed in work profile](../screenshots/sanitized/device-enrollment/android-byod-001-work-profile-apps-with-authenticator-sanitized.png)

![Android apps assigned list](../screenshots/sanitized/device-enrollment/android-byod-android-apps-assigned-list-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Managed Google Play connected | Passed |
| Android Enterprise work profile enrollment allowed | Passed |
| Personally owned Android enrollment allowed | Passed |
| Android BYOD device enrolled | Passed |
| Work profile created | Passed |
| Device visible in Intune | Passed |
| Ownership shown as Personal | Passed |
| Compliance shown as Compliant | Passed |
| Microsoft Authenticator assigned as Required | Passed |
| Microsoft Authenticator installed in Work profile | Passed |

---

## Troubleshooting Notes

**Managed Google Play setup — fallback account used** — the Microsoft Entra-based Google Admin account creation did not complete. The limited account fallback option was used and still allowed Android Enterprise setup to complete successfully.

**Managed Google Play app picker loaded blank** — when trying to add additional apps, the picker loaded as a blank screen. Microsoft Authenticator was already available as an approved Managed Google Play app and was assigned directly, which allowed app deployment validation to continue.

**App install delay** — Microsoft Authenticator did not appear in the Work profile immediately after assignment. Waiting for Intune sync and Google Play delivery resolved this. Delayed app delivery after assignment is expected behavior.

**Device not appearing in Intune** — confirm Managed Google Play is connected, Android Enterprise work profile enrollment is allowed, the user has an Intune-capable license and is in `GRP-BYOD-Users`, the device has internet access, and Company Portal enrollment completed without errors.

---

## Enterprise Reflection

In production, Android BYOD should be managed with a privacy-aware approach that protects work data without intruding on the employee's personal device.

| Area | Recommendation |
|---|---|
| Enrollment type | Personally owned work profile for Android BYOD |
| Privacy | Manage the work profile only, not the full device |
| Apps | Deploy work apps through Managed Google Play |
| Compliance | Require basic device health and security settings |
| Conditional Access | Require compliant device or app protection policy |
| Pilot rollout | Test with a small BYOD group before broad deployment |
| User communication | Clearly explain what IT can and cannot see |

---

## Key Learning Outcomes

- How to connect Managed Google Play to Microsoft Intune
- How to enable Android Enterprise personally owned work profile enrollment
- How the Android work profile separates personal and work data
- How to validate Android BYOD device status in Intune
- How to assign a Managed Google Play app as Required and confirm it installs in the Work profile
