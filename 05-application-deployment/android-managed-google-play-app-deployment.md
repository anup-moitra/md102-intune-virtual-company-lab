# Android Managed Google Play App Deployment

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Application deployment |
| Platform | Android Enterprise |
| App source | Managed Google Play |
| Target group | GRP-BYOD-Users |
| Test user | user03 |
| Test device | ANDROID-BYOD-001 |
| Apps deployed | Microsoft Outlook, Microsoft Teams |
| Assignment type | Required |
| Result | Outlook and Teams installed in Android Work profile |

---

## Lab Objective

Deploy Microsoft Outlook and Teams to an enrolled Android BYOD work profile device using Managed Google Play and Microsoft Intune, and validate installation inside the Android Work profile.

---

## Why This Lab Matters

Android BYOD users need work apps delivered into the managed Work profile — not the personal side of the device. Managed Google Play is the standard delivery mechanism for Android Enterprise. This lab demonstrates the full flow: approving an app, syncing it into Intune, assigning it to a BYOD group, and confirming it appears in the Work profile with a work badge.

---

## Prerequisites

- `02-device-enrollment/android-byod-enrollment.md` completed
- ANDROID-BYOD-001 enrolled with Android Work profile active
- user03 in GRP-BYOD-Users
- Managed Google Play connected to Intune

---

## Configuration Flow

```text
Open Android apps in Intune
-> Add Managed Google Play app (Outlook)
-> Sync apps into Intune
-> Assign Outlook and Teams as Required to GRP-BYOD-Users
-> Confirm apps install in Android Work profile
```

---

## Steps Performed

### Step 1 — Added Microsoft Outlook from Managed Google Play

Navigated to:

```text
Apps -> Android -> Android apps -> Create -> Managed Google Play app
```

Searched for and selected Microsoft Outlook in the Managed Google Play picker. Approved the app so it could sync into Intune.

> [!NOTE]
> During the first attempt, the Managed Google Play picker loaded as a blank screen. Opening the Intune admin center in an InPrivate browser session and repeating the workflow resolved it. The Managed Google Play connector was already active — this was a browser/session cache issue.

![Microsoft Outlook approved in Managed Google Play](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-approved-sanitized.png)

---

### Step 2 — Synced apps and confirmed in Intune

After selecting Outlook, synced apps from the Android apps list. After refresh, both Microsoft Outlook and Microsoft Teams appeared in the Android apps list as Managed Google Play store apps.

![Outlook and Teams added and assigned](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-teams-added-assigned-sanitized.png)

---

### Step 3 — Assigned Outlook as Required

Navigated to:

```text
Apps -> Android -> Microsoft Outlook -> Properties -> Assignments -> Edit
```

| Setting | Value |
|---|---|
| Assignment type | Required |
| Included group | GRP-BYOD-Users |

Applied the same assignment to Microsoft Teams.

![Microsoft Outlook required assignment](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-required-assignment-sanitized.png)

---

### Step 4 — Confirmed installation in Work profile

After device sync, opened the Work profile app drawer on ANDROID-BYOD-001. Microsoft Outlook and Teams appeared with the Android Work profile badge, confirming they were installed in the managed Work profile — not the personal profile.

![Outlook and Teams installed in Android Work profile](../screenshots/sanitized/application-deployment/android-managed-google-play-outlook-teams-installed-work-profile-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| Managed Google Play picker loaded (InPrivate workaround used) | Completed |
| Microsoft Outlook approved from Managed Google Play | Completed |
| Outlook and Teams synced into Intune | Completed |
| Outlook and Teams assigned as Required to GRP-BYOD-Users | Completed |
| Apps installed in Android Work profile with work badge | Completed |

---

## Troubleshooting Notes

**Managed Google Play picker blank screen** — resolved by opening the Intune admin center in an InPrivate browser session. The Managed Google Play connector was already active and Android enrollment was working. This was a browser session/cache issue, not a connector problem.

**App not appearing in Work profile** — confirm the assignment is Required, the user is in `GRP-BYOD-Users`, the device has an active Work profile, and the device has internet access. Wait for Intune and Managed Google Play synchronization to complete before rechecking the Work profile app drawer.

---

## Enterprise Reflection

In production, Managed Google Play is the only approved app delivery mechanism for Android Enterprise work profile devices. Key considerations:

- Use Required only for essential work apps; use Available for optional/self-service apps
- Combine app deployment with app protection policies to protect work data within deployed apps
- Validate installation from the Work profile specifically — apps should not appear in the personal profile
- Explain to users that work-badged apps are managed by IT and kept separate from personal apps

---

## Key Learning Outcomes

- How to add and approve Managed Google Play apps in Microsoft Intune
- How to assign Android work profile apps as Required to a BYOD user group
- How the Android Work profile badge confirms an app is installed in the managed profile
- How to resolve a blank Managed Google Play picker using an InPrivate browser session
