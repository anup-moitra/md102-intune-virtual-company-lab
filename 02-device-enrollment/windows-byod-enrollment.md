# Windows BYOD Enrollment

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Device enrollment |
| Platform | Windows 11 |
| Management platform | Microsoft Intune |
| BYOD test user | user03 |
| BYOD user group | GRP-BYOD-Users |
| Test device | WIN-BYOD-001 |
| Enrollment method | Windows MDM enrollment from Settings |
| Ownership result | Personal |
| Compliance result | Compliant |

---

## Lab Objective

Enroll a personally owned Windows device into Microsoft Intune using a BYOD user account, validate Personal ownership and Compliant status in Intune, and prepare the device for later compliance and Conditional Access testing.

---

## Why This Lab Matters

Not every Windows device in an organisation is corporate-owned. With Intune, administrators can allow controlled access from personal devices while still applying compliance and security requirements.

```text
User adds work account from Windows Settings
-> Windows enrolls into Intune MDM
-> Intune marks the device as Personal
-> Admin can apply BYOD policies and compliance rules
```

This is distinct from a corporate Autopilot device, which is strictly managed and shows as Corporate in Intune.

---

## Prerequisites

| Requirement | Status |
|---|---|
| user03 created with Intune-capable license | Confirmed |
| user03 member of GRP-BYOD-Users | Confirmed |
| GRP-BYOD-Users scoped for automatic MDM enrollment | Confirmed |
| Windows personally owned enrollment allowed | Confirmed |
| WIN-BYOD-001 prepared and named | Confirmed |
| Device has internet access | Confirmed |

---

## Configuration Flow

```text
Confirm user03 license and group membership
-> Scope automatic MDM enrollment to GRP-BYOD-Users
-> Confirm Windows personally owned enrollment is allowed
-> Add work account from Windows Settings
-> Complete MDM enrollment using Enroll only in device management
-> Sync device
-> Validate device in Intune
```

---

## Steps Performed

### Step 1 — Confirmed user03 prerequisites

Confirmed in Microsoft 365 admin center that user03 had an Intune-capable license assigned and was a member of `GRP-BYOD-Users`.

![User 03 license assignment](../screenshots/sanitized/device-enrollment/windows-byod-user03-license-sanitized.png)

![User 03 BYOD group membership](../screenshots/sanitized/device-enrollment/windows-byod-user03-byod-group-membership-sanitized.png)

---

### Step 2 — Confirmed enrollment settings in Intune

Confirmed automatic MDM enrollment was scoped to `GRP-BYOD-Users`:

```text
Devices -> Windows -> Windows enrollment -> Automatic Enrollment
```

| Setting | Value |
|---|---|
| MDM user scope | Some |
| Selected group | GRP-BYOD-Users |

Confirmed Windows personal enrollment was allowed:

```text
Devices -> Enrollment -> Device platform restrictions -> Windows restrictions -> All Users
```

| Setting | Value |
|---|---|
| Windows (MDM) platform | Allow |
| Windows personally owned | Allow |

![Automatic MDM enrollment scope](../screenshots/sanitized/device-enrollment/windows-byod-automatic-mdm-scope-sanitized.png)

![Windows BYOD platform restriction](../screenshots/sanitized/device-enrollment/windows-byod-platform-restriction-sanitized.png)

---

### Step 3 — Enrolled the device from Windows Settings

On WIN-BYOD-001, navigated to:

```text
Settings -> Accounts -> Access work or school -> Connect
```

Signed in as user03. The account was added, but the full Intune management view was not immediately visible — the page showed only a connected work account without device management options. This was resolved by completing the full MDM enrollment step:

```text
Settings -> Accounts -> Access work or school -> Enroll only in device management
```

After this, the device showed:

```text
Connected to HomeLAB MDM
Managed by HomeLAB
```

![Windows BYOD device name](../screenshots/sanitized/device-enrollment/win-byod-001-device-about-sanitized.png)

![Access work or school before enrollment](../screenshots/sanitized/device-enrollment/win-byod-001-access-work-school-before-sanitized.png)

![Account added to device](../screenshots/sanitized/device-enrollment/win-byod-001-account-added-sanitized.png)

![Work account connected only](../screenshots/sanitized/device-enrollment/win-byod-001-work-account-connected-only-sanitized.png)

![Access work or school after MDM enrollment](../screenshots/sanitized/device-enrollment/win-byod-001-access-work-school-after-sanitized.png)

---

### Step 4 — Synced and verified in Intune

Performed a manual sync from:

```text
Settings -> Accounts -> Access work or school -> Managed by HomeLAB -> Info
```

Then verified the device in Intune:

```text
Devices -> Windows -> Windows devices
```

| Field | Result |
|---|---|
| Device name | WIN-BYOD-001 |
| Managed by | Intune |
| Ownership | Personal |
| Compliance | Compliant |
| Primary user | user03 |

![Manual device sync](../screenshots/sanitized/device-enrollment/win-byod-001-manual-sync-sanitized.png)

![Intune Windows devices list](../screenshots/sanitized/device-enrollment/win-byod-001-intune-windows-devices-list-sanitized.png)

![Intune device overview](../screenshots/sanitized/device-enrollment/win-byod-001-intune-overview-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| user03 licensed and in GRP-BYOD-Users | Completed |
| MDM enrollment scoped to GRP-BYOD-Users | Completed |
| Windows personally owned enrollment allowed | Completed |
| Work account added from Windows Settings | Completed |
| MDM enrollment completed | Completed |
| Device synced | Completed |
| Device appeared in Intune | Completed |
| Ownership shown as Personal | Completed |
| Compliance shown as Compliant | Completed |
| Primary user shown as user03 | Completed |

---

## Troubleshooting Notes

**Work account connected but MDM management not visible** — after adding the work account via Connect, the Access work or school page showed only a basic connected account view without Intune management options. The resolution was to separately complete `Enroll only in device management` from the same Settings page. This triggered the full MDM enrollment and the device then showed as connected to HomeLAB MDM.

**Device not appearing in Intune** — confirm the user has an Intune-capable license, is in the group scoped for automatic MDM enrollment, and that Windows personally owned enrollment is allowed. Complete the `Enroll only in device management` flow and sync from Access work or school before checking the Intune devices list again.

---

## Enterprise Reflection

In production, BYOD Windows devices should be managed differently from corporate devices — lighter on restrictions, careful with remote actions, and transparent to the user about what IT can see.

| Area | BYOD approach |
|---|---|
| Ownership | Personal |
| Enrollment scope | Controlled BYOD user group |
| Apps | Available/self-service preferred over required |
| Compliance | Basic health and security checks |
| Conditional Access | Require compliant device or app protection |
| Remote actions | Use caution with Wipe and Retire on personal devices |

---

## Related Labs

| Lab | Relationship |
|---|---|
| `01-identity-and-groups/users-and-groups.md` | Provides user03 and GRP-BYOD-Users |
| `02-device-enrollment/android-byod-enrollment.md` | Android BYOD comparison — different platform, same BYOD pattern |
| `04-compliance-and-conditional-access/managed-noncompliant-device-test.md` | Uses WIN-BYOD-001 to test noncompliant BYOD behaviour |
| `04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md` | Uses WIN-BYOD-001 to validate CA enforced blocking |

---

## Key Learning Outcomes

- How to scope automatic MDM enrollment to a specific BYOD user group
- Why adding a work account alone is not the same as completing MDM enrollment
- How Personal ownership differs from Corporate in Intune
- How a BYOD device can be compliant while remaining personally owned
