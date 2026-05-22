# Windows Basic Configuration Profile

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Configuration profiles |
| Platform | Windows 10 and later |
| Profile type | Settings catalog |
| Profile name | CFG-WIN-Basic-Device-Settings |
| Assignment group | GRP-Pilot-Users |
| Validated devices | WIN-CORP-001, WINAUTO452 |

---

## Lab Objective

Create a basic Windows Settings catalog profile in Microsoft Intune, assign it to a pilot user group, and validate that enrolled Windows devices receive and enforce the configured Device Lock settings.

---

## Why This Lab Matters

In a modern cloud-managed environment, Intune configuration profiles replace many traditional Group Policy use cases for Microsoft Entra joined devices. This lab demonstrates how to centrally manage basic Windows device settings — in this case, automatic screen lock — without relying on on-premises Group Policy.

---

## Prerequisites

- GRP-Pilot-Users group available
- WIN-CORP-001 and WINAUTO452 enrolled and able to sync with Intune
- Access to Microsoft Intune admin center

---

## Configuration Summary

| Setting category | Setting | Value |
|---|---|---|
| Device Lock | Device Password Enabled | Enabled |
| Device Lock | Max Inactivity Time Device Lock | 5 |

The inactivity value of 5 was used to allow quick endpoint validation during testing.

---

## Configuration Flow

```text
Create Settings catalog profile
-> Configure Device Lock settings
-> Assign profile to GRP-Pilot-Users
-> Sync Windows endpoints
-> Reboot endpoints
-> Verify device status in Intune
-> Validate endpoint lock behavior
```

---

## Steps Performed

### Step 1 — Created and configured the profile

Navigated to:

```text
Devices -> Windows -> Configuration -> Create -> New policy
```

Selected Windows 10 and later as the platform and Settings catalog as the profile type. Named the profile `CFG-WIN-Basic-Device-Settings` and configured the following settings under Device Lock:

| Setting | Value |
|---|---|
| Device Password Enabled | Enabled |
| Max Inactivity Time Device Lock | 5 |

![Create profile](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-create-profile-sanitized.png)

![Profile basics](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-basics-sanitized.png)

![Device Lock settings configured](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-settings-configured-sanitized.png)

---

### Step 2 — Assigned the profile

Assigned the profile to `GRP-Pilot-Users`. This user-targeted assignment applies the profile to enrolled Windows devices used by pilot group members.

![Profile assignment](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-assignment-sanitized.png)

---

### Step 3 — Synced endpoints and verified status

Synced both devices from Intune and from local Windows Settings. Rebooted both devices after the initial sync — the lock behavior did not apply until after reboot.

Verified policy status in Intune:

```text
Devices -> Windows -> Configuration -> CFG-WIN-Basic-Device-Settings -> Device status
```

| Device | Assignment status |
|---|---|
| WIN-CORP-001 | Success |
| WINAUTO452 | Success |

![Device status success](../screenshots/sanitized/configuration-profiles/windows-basic-config-profile-device-status-success-sanitized.png)

---

### Step 4 — Validated endpoint behavior

After reboot, both devices locked automatically after approximately 5 minutes of inactivity, confirming the profile was enforced.

---

## Final Test Result

| Validation item | Result |
|---|---|
| Settings catalog profile created | Completed |
| Device Lock settings configured | Completed |
| Profile assigned to GRP-Pilot-Users | Completed |
| Devices synced and rebooted | Completed |
| Intune device status showed Success | Completed |
| Both endpoints locked after inactivity period | Completed |

---

## Troubleshooting Notes

**Policy showed Success but endpoint did not immediately lock** — during initial testing, Intune reported the profile as successfully assigned but the devices did not lock after the configured inactivity period. Rebooting both endpoints resolved this. Some configuration settings are not enforced until the device starts a new session.

This is an important validation point: Intune reporting confirms policy delivery, but endpoint behavior testing confirms the user experience. Always test both.

---

## Enterprise Reflection

Basic configuration profiles are usually part of a standard Windows device baseline in production. Key considerations before broad rollout:

| Consideration | Why it matters |
|---|---|
| Pilot testing first | Confirms settings work before affecting all users |
| User impact | Lock settings affect sign-in frequency and workflow |
| Reboot requirement | Some settings need a reboot or new session to take effect |
| Intune reporting | Verify Success status before relying on endpoint behavior |

---

## Key Learning Outcomes

- How to create a Windows Settings catalog profile in Microsoft Intune
- How user-targeted profiles apply to enrolled devices used by the assigned users
- Why some configuration settings require a reboot before taking effect
- How Intune policy reporting and endpoint behavior validation complement each other
- How Intune Settings catalog profiles replace traditional Group Policy for cloud-managed devices
