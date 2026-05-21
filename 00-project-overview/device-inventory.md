# Device Inventory

This file tracks all lab devices used in the Contoso Startup Lab environment — their configuration, enrollment details, and lifecycle outcomes.

---

## Device Summary

| Device | Type | Ownership | OS | Enrollment | User | Lifecycle |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Personal in Intune (manual MDM) | Windows 11 | OOBE + Entra join + manual MDM | user01 | Wiped |
| WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven | user01 | Retired |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows MDM from Settings | user03 | Active |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android 15 | Android Enterprise work profile | user03 | Active |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS/iPadOS | Company Portal (planned) | user04 | Pending |

---

## WIN-CORP-001

| Field | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Type | Laptop |
| Ownership in Intune | Personal (result of manual MDM enrollment after OOBE) |
| OS | Windows 11 |
| Enrollment | OOBE + Microsoft Entra join + manual Intune MDM trigger |
| Primary user | user01 |
| Initial compliance | Compliant |
| Final lifecycle | Wiped during remote actions lab |

Used for Windows OOBE enrollment, app deployment testing (Store, Win32, Microsoft 365 Apps), and Wipe remote action validation. After the Wipe completed, the device record returned a Not found message in Intune.

**Related labs:**
- `02-device-enrollment/windows-oobe-enrollment.md`
- `05-application-deployment/microsoft-store-app-deployment.md`
- `05-application-deployment/win32-app-deployment-7zip.md`
- `05-application-deployment/microsoft-365-apps-autopilot-deployment.md`
- `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md`
- `08-troubleshooting/intune-enrollment-troubleshooting.md`

---

## WINAUTO452

| Field | Value |
|---|---|
| Original lab name | WIN-AUTOPILOT-001 |
| Final enrolled name | WINAUTO452 (assigned during Autopilot provisioning) |
| Type | Laptop |
| Ownership in Intune | Corporate |
| OS | Windows 11 |
| Enrollment | Windows Autopilot user-driven, Microsoft Entra joined |
| Autopilot group | GRP-Autopilot-Devices |
| Autopilot profile | APUserDrivenEntraJoinPilot |
| Primary user | user01 |
| Compliance during active testing | Compliant |
| Final lifecycle | Retired during remote actions lab |

The primary corporate lab device. Used for configuration profiles, endpoint security (Defender AV, Firewall, BitLocker, ASR, Security Baseline), compliance policy, Conditional Access report-only testing, and remote actions (Sync, Restart, Retire, Collect Diagnostics). Autopilot hardware hashes and serial numbers are not stored in this repository.

**Related labs:**
- `02-device-enrollment/windows-autopilot-user-driven-enrollment.md`
- `03-configuration-profiles/`
- `04-compliance-and-conditional-access/windows-basic-compliance-policy.md`
- `04-compliance-and-conditional-access/conditional-access-compliant-device.md`
- `05-application-deployment/microsoft-365-apps-autopilot-deployment.md`
- `06-endpoint-security/`
- `07-remote-actions-and-monitoring/`
- `08-troubleshooting/configuration-policy-conflict-troubleshooting.md`
- `08-troubleshooting/remote-actions-diagnostics-troubleshooting.md`

---

## WIN-BYOD-001

| Field | Value |
|---|---|
| Device name | WIN-BYOD-001 |
| Type | Laptop |
| Ownership in Intune | Personal |
| OS | Windows 11 |
| Enrollment | Windows MDM from Settings |
| Primary user | user03 |
| BYOD group | GRP-BYOD-Users |
| Initial compliance | Compliant |
| Later compliance state | Temporarily Noncompliant (intentional, for Conditional Access testing) |
| Current lifecycle | Active |

Used for Windows BYOD enrollment validation, then intentionally made noncompliant via a temporary high minimum OS version compliance policy to validate Conditional Access report-only failure and enforced-mode blocking for Microsoft 365.

**Related labs:**
- `02-device-enrollment/windows-byod-enrollment.md`
- `04-compliance-and-conditional-access/managed-noncompliant-device-test.md`
- `04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md`

> [!NOTE]
> The noncompliant state was created intentionally for controlled lab validation. The original BYOD enrollment completed successfully; noncompliance was introduced afterward as a separate test step.

---

## ANDROID-BYOD-001

| Field | Value |
|---|---|
| Device name | ANDROID-BYOD-001 |
| Type | Mobile |
| Model | Motorola Moto G34 5G |
| Ownership in Intune | Personal |
| OS | Android 15 |
| Enrollment | Android Enterprise personally owned work profile |
| Primary user | user03 |
| BYOD group | GRP-BYOD-Users |
| Compliance | Compliant |
| Apps deployed | Microsoft Authenticator, Outlook, Teams (all in Work profile) |
| Current lifecycle | Active |

Used for Android Enterprise work profile enrollment and Managed Google Play app deployment validation.

**Related labs:**
- `02-device-enrollment/android-byod-enrollment.md`
- `05-application-deployment/android-managed-google-play-app-deployment.md`

---

## IOS-BYOD-001

| Field | Value |
|---|---|
| Device name | IOS-BYOD-001 |
| Type | Mobile |
| Ownership in Intune | Personal (planned) |
| OS | iOS/iPadOS |
| Enrollment | Company Portal (planned) |
| Test user | user04 |
| BYOD group | GRP-BYOD-Users |
| Current lifecycle | In Progress — admin prerequisites complete, physical enrollment pending |

Admin prerequisites completed: iOS/iPadOS enrollment allowed, personally owned devices allowed, Apple MDM Push Certificate created and active in Intune. Physical iPhone or iPad required to complete enrollment.

**Related lab:**
- `02-device-enrollment/ios-byod-enrollment.md`

---

## Remote Action Summary

| Device | Action | Result |
|---|---|---|
| WINAUTO452 | Sync | Completed |
| WINAUTO452 | Restart | Completed |
| WINAUTO452 | Retire | Completed |
| WINAUTO452 | Collect Diagnostics | Completed |
| WIN-CORP-001 | Wipe | Completed |

---

## Device Naming Convention

| Pattern | Meaning |
|---|---|
| WIN-CORP-### | Corporate Windows device |
| WIN-AUTOPILOT-### | Windows Autopilot test device (pre-enrollment name) |
| WINAUTO### | Autopilot-assigned device name after provisioning |
| WIN-BYOD-### | Personal Windows BYOD device |
| ANDROID-BYOD-### | Personal Android BYOD device |
| IOS-BYOD-### | Personal iOS/iPadOS BYOD device |

---

## Screenshot Folder Reference

| Lab area | Folder |
|---|---|
| Device enrollment (all types) | `screenshots/sanitized/device-enrollment/` |
| Configuration profiles | `screenshots/sanitized/configuration-profiles/` |
| Application deployment | `screenshots/sanitized/application-deployment/` |
| Compliance and Conditional Access | `screenshots/sanitized/compliance-and-conditional-access/` |
| Endpoint security | `screenshots/sanitized/endpoint-security/` |
| Remote actions and monitoring | `screenshots/sanitized/remote-actions-and-monitoring/` |
| Troubleshooting | Reuses screenshots from the relevant source lab folder |
