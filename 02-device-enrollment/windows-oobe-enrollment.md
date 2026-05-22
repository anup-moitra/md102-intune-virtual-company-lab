# Windows OOBE Enrollment

## Lab Status

| Field | Value |
|---|---|
| Status | Completed |
| Lab category | Device enrollment |
| Platform | Windows 11 |
| Enrollment method | Windows out-of-box experience (OOBE) |
| Join type | Microsoft Entra joined |
| Device name | WIN-CORP-001 |
| Primary test user | user01 |
| Ownership result | Personal |
| Management result | Managed by Intune |
| Compliance result | Compliant |

---

## Lab Objective

Enroll a Windows device into Microsoft Intune during OOBE, identify and resolve an MDM enrollment issue, and validate the final managed state in both the endpoint and the Intune admin center.

---

## Why This Lab Matters

This lab shows the difference between a device that is only Entra joined and one that is fully enrolled into Intune — a distinction that matters in real troubleshooting.

| Scenario | Result |
|---|---|
| Microsoft Entra joined only | Cloud identity joined, but not Intune managed |
| Microsoft Entra joined + MDM enrolled | Joined and managed by Intune |
| Manual Windows enrollment | Useful for testing, results in Personal ownership |
| Windows Autopilot enrollment | Correct method for corporate-owned production devices |

---

## Prerequisites

- user01 created and licensed for Intune
- Automatic MDM enrollment settings reviewed
- Windows test device available for reset or clean setup
- Internet connectivity during OOBE

---

## Configuration Flow

```text
Reset or prepare Windows device
-> Complete OOBE using work or school setup
-> Sign in with user01
-> Verify Microsoft Entra join
-> Identify MDM: None state
-> Complete manual MDM enrollment from Windows Settings
-> Verify device in Intune
-> Document ownership and compliance result
```

---

## Steps Performed

### Step 1 — Completed Windows OOBE

Reset a Windows 11 device and completed OOBE using the work or school setup option. Named the device `WIN-CORP-001` during setup and signed in as `user01` to join the device to Microsoft Entra ID.

![Windows OOBE region selection](../screenshots/sanitized/device-enrollment/windows-oobe-region-selection-sanitized.png)

![Windows OOBE device name](../screenshots/sanitized/device-enrollment/windows-oobe-device-name-sanitized.png)

![Windows OOBE work or school selection](../screenshots/sanitized/device-enrollment/windows-oobe-work-school-selection-sanitized.png)

![Windows OOBE user sign-in](../screenshots/sanitized/device-enrollment/windows-oobe-user01-signin-sanitized.png)

---

### Step 2 — Identified MDM enrollment issue

After OOBE, validated the device state from Windows Settings and the Microsoft Entra device record. The device had joined Microsoft Entra ID successfully, but the MDM state showed:

```text
MDM: None
```

This meant the device was cloud identity joined but not yet enrolled into Intune. A device must be enrolled into MDM — not just Entra joined — to receive Intune policies and app assignments.

![Windows device name verification](../screenshots/sanitized/device-enrollment/win-corp-001-device-name-sanitized.png)

![Access work or school verification](../screenshots/sanitized/device-enrollment/win-corp-001-access-work-school-sanitized.png)

![Entra device record showing MDM: None](../screenshots/sanitized/device-enrollment/win-corp-001-entra-device-mdm-none-sanitized.png)

---

### Step 3 — Completed manual MDM enrollment

Triggered manual MDM enrollment from:

```text
Settings -> Accounts -> Access work or school -> Enroll only in device management
```

After enrollment and sync, validated the device in Intune.

---

### Step 4 — Verified device in Intune

The device appeared in Intune as managed with compliance visible.

| Field | Result |
|---|---|
| Device name | WIN-CORP-001 |
| Managed by | Intune |
| Compliance | Compliant |
| Ownership | Personal |
| Primary user | user01 |

The Personal ownership result was expected for this enrollment path. Manual enrollment does not set corporate ownership — Windows Autopilot is the correct method for that, and was validated in the later Autopilot lab.

![Intune Windows devices list](../screenshots/sanitized/device-enrollment/win-corp-001-intune-windows-devices-list-sanitized.png)

![Intune device overview](../screenshots/sanitized/device-enrollment/win-corp-001-intune-overview-sanitized.png)

---

## Final Test Result

| Validation item | Result |
|---|---|
| OOBE completed with work or school setup | Completed |
| user01 signed in during OOBE | Completed |
| Microsoft Entra join completed | Completed |
| MDM: None issue identified | Completed |
| Manual MDM enrollment triggered | Completed |
| Device appeared in Intune | Completed |
| Managed by Intune confirmed | Completed |
| Compliance visible | Completed |
| Personal ownership documented | Completed |

---

## Troubleshooting Notes

**MDM: None after OOBE** — the device joined Microsoft Entra ID successfully but the MDM state showed None. This means automatic MDM enrollment did not trigger. Manual enrollment from `Settings -> Accounts -> Access work or school -> Enroll only in device management` resolved it. After enrollment and sync, the device appeared in Intune as managed.

**Key distinction:**

| State | Meaning |
|---|---|
| Microsoft Entra joined | Device is in cloud identity |
| MDM: None | Not yet enrolled into any MDM provider |
| Managed by Intune | Device can receive policies and app assignments |

Being Entra joined and being Intune enrolled are related but separate states. Both must be true for full Intune management.

**Ownership shows Personal** — this is expected for manual OOBE enrollment. Corporate ownership requires Windows Autopilot provisioning.

---

## Enterprise Reflection

Manual OOBE enrollment is useful for lab testing and troubleshooting, but it is not the right method for corporate-owned device deployment in production.

| Enrollment method | Best use case |
|---|---|
| Manual Windows enrollment | Small tests, BYOD, lab validation |
| Windows Autopilot | Corporate-owned device provisioning |
| Bulk provisioning package | Shared device or staging scenarios |
| Co-management | Existing Configuration Manager environments moving to cloud |

The key lesson from this lab is that a device must be enrolled into Intune, not just joined to Entra ID, before it can receive policies. This distinction is directly tested in MD-102 and comes up frequently in real Intune troubleshooting.

---

## Key Learning Outcomes

- The difference between Microsoft Entra join and Intune MDM enrollment
- What MDM: None means and how to resolve it manually
- How manual OOBE enrollment results in Personal ownership vs. Autopilot corporate ownership
- Why validating MDM state at both the endpoint and the admin portal matters
