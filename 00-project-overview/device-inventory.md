# Device Inventory

This file tracks the lab devices used in the MD-102 Intune virtual company environment.

---

## Purpose

The purpose of this device inventory is to document all planned, active, retired, wiped, and optional lab devices used for Microsoft Intune, Microsoft Entra ID, Windows Autopilot, BYOD enrollment, compliance, Conditional Access, application deployment, endpoint security, monitoring, remote actions, and troubleshooting labs.

This file should be updated whenever a device is enrolled, reused, reset, retired, wiped, or removed from active testing.

---

## Device ownership types

This lab includes both corporate-owned and personally owned/BYOD devices.

### Corporate-owned devices

Corporate-owned devices are managed more strictly because they represent company assets.

These devices can be used for:

- Microsoft Entra join
- Microsoft Intune enrollment
- Windows Autopilot
- Compliance policies
- Conditional Access testing
- Configuration profiles
- Required app deployment
- Endpoint security policies
- BitLocker encryption
- Remote actions
- Device monitoring and reporting

### BYOD devices

BYOD devices are personally owned test devices used to simulate employee-owned devices.

BYOD testing helps compare:

```text
Unmanaged personal device
vs
Enrolled personal/BYOD device
vs
Managed but noncompliant BYOD device
vs
Corporate-managed compliant device
```

This project uses BYOD testing to show that a device can be:

```text
Managed by Intune = Yes
Compliant = No
```

This distinction is important because Conditional Access can require a device to be compliant before allowing Microsoft 365 access.

### Autopilot devices

Autopilot devices are corporate Windows devices registered with Windows Autopilot for cloud-based provisioning.

These devices are used to test:

- Hardware hash import
- Autopilot device import
- Deployment profile assignment
- Windows OOBE provisioning
- Microsoft Entra join
- Automatic Intune enrollment
- App and policy deployment after enrollment
- Corporate ownership after provisioning
- Compliance policy validation
- Conditional Access compliant-device validation
- Remote actions and monitoring

---

## Current device inventory

| Device name | Device type | Ownership | OS | Enrollment type | User | Current lifecycle status |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate lab device / Personal in Intune after manual MDM enrollment | Windows 11 | OOBE + Entra joined + manual Intune MDM enrollment | user01 | Wiped during remote actions lab |
| WIN-AUTOPILOT-001 / WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven Microsoft Entra join | user01 | Retired during remote actions lab |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows MDM enrollment from Settings | user03 | Enrolled / Used for BYOD compliance and Conditional Access testing / Temporarily marked Noncompliant for lab validation |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android 15 | Android Enterprise personally owned work profile | user03 | Enrolled / Compliant / Work profile created / Authenticator, Outlook, and Teams deployed |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS/iPadOS | Company Portal enrollment planned | user04 | In Progress / Admin prerequisites completed / Physical enrollment pending |

> [!NOTE]
> `WIN-CORP-001` was successfully enrolled and used for early Windows enrollment and app deployment labs. It was later wiped during the Restart, Retire, and Wipe remote actions lab.

> [!NOTE]
> `WINAUTO452` was successfully provisioned through Windows Autopilot and used for configuration profiles, endpoint security, compliance, Conditional Access, remote actions, diagnostics, and monitoring labs. It was later retired during the Restart, Retire, and Wipe remote actions lab.

> [!NOTE]
> `WIN-BYOD-001` was initially enrolled and shown as compliant after Windows BYOD enrollment. It was later intentionally made noncompliant using a temporary compliance policy so that Conditional Access report-only and enforced-mode behavior could be validated.

---

## Corporate Windows device lifecycle

### WIN-CORP-001

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Laptop |
| Lab ownership | Corporate lab device |
| Intune ownership during enrollment | Personal |
| Operating system | Windows 11 |
| Enrollment method | OOBE + manual MDM trigger |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Initial compliance | Compliant |
| Purpose | Early Windows Intune test device |
| Final lifecycle status | Wiped during remote actions lab |

This device validated:

- Windows OOBE setup
- Device naming during OOBE
- Microsoft Entra join
- Intune enrollment troubleshooting
- Manual MDM enrollment trigger
- Intune device visibility
- Compliance status visibility
- Microsoft Store app deployment
- Required app installation through Intune
- Available app visibility in Company Portal
- Win32 7-Zip app deployment
- Microsoft 365 Apps deployment preparation and validation
- Wipe remote action validation

Final lifecycle result:

```text
WIN-CORP-001 was used successfully for enrollment and app deployment labs.
During the remote actions lab, the device received the Wipe action.
The Device Actions report showed Wipe as Complete.
After the Wipe action completed, the opened device page returned a Not found message.
```

Related labs:

```text
02-device-enrollment/windows-oobe-enrollment.md
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
07-remote-actions-and-monitoring/restart-retire-wipe-actions.md
08-troubleshooting/intune-enrollment-troubleshooting.md
```

---

## Windows Autopilot device lifecycle

### WIN-AUTOPILOT-001 / WINAUTO452

| Item | Value |
|---|---|
| Original lab device name | WIN-AUTOPILOT-001 |
| Final enrolled device name | WINAUTO452 |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Autopilot user-driven enrollment |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Autopilot group | GRP-Autopilot-Devices |
| Autopilot profile | APUserDrivenEntraJoinPilot |
| Compliance during active testing | Compliant |
| Apps verified | Store apps, Win32 7-Zip, Microsoft 365 Apps |
| Configuration profiles verified | Basic Windows profile, corporate wallpaper, USB storage block |
| Endpoint security verified | Defender Antivirus, Windows Firewall, BitLocker, Attack Surface Reduction, Windows Security Baseline |
| Compliance and Conditional Access verified | Windows compliance policy and report-only compliant-device Conditional Access test |
| Remote actions verified | Sync, Restart, Retire, Collect diagnostics |
| Purpose | Main corporate Windows lab device |
| Final lifecycle status | Retired during remote actions lab |

This device validated:

- Hardware hash collection
- Autopilot device CSV import
- Autopilot device group targeting
- Autopilot deployment profile creation
- Autopilot deployment profile assignment
- Windows OOBE sign-in with user01
- Microsoft Entra join
- Automatic Microsoft Intune enrollment
- Corporate device ownership
- Compliance status after enrollment
- Required app deployment after Autopilot enrollment
- Windows basic configuration profile validation
- Corporate wallpaper ADMX policy validation
- USB/removable storage block validation
- Defender Antivirus endpoint security policy validation
- Windows Firewall endpoint security policy validation
- BitLocker encryption policy validation
- Attack Surface Reduction policy validation in Audit mode
- Windows Security Baseline deployment and troubleshooting
- Windows basic compliance policy validation
- Secure Boot remediation for compliance
- Conditional Access report-only compliant-device validation
- Device sync remote action
- Restart remote action
- Collect diagnostics remote action
- Device monitoring and reports
- Retire remote action validation

Final Autopilot result:

```text
WIN-AUTOPILOT-001 was provisioned with Windows Autopilot and appeared in Intune as WINAUTO452.
The device was managed by Microsoft Intune, marked as Corporate, showed Compliant, received required app deployments, received configuration profiles, received endpoint security policies, passed Windows compliance validation, and satisfied the Conditional Access compliant-device report-only test.

During the final remote actions lab, WINAUTO452 received Restart and Retire remote actions.
The Device Actions report showed Restart and Retire as Complete.
```

Related labs:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
03-configuration-profiles/windows-basic-configuration-profile.md
03-configuration-profiles/windows-corporate-wallpaper-policy.md
03-configuration-profiles/windows-device-restrictions-profile.md
04-compliance-and-conditional-access/windows-basic-compliance-policy.md
04-compliance-and-conditional-access/conditional-access-compliant-device.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
06-endpoint-security/windows-defender-antivirus-policy.md
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
07-remote-actions-and-monitoring/device-sync-remote-actions.md
07-remote-actions-and-monitoring/restart-retire-wipe-actions.md
07-remote-actions-and-monitoring/collect-diagnostics.md
07-remote-actions-and-monitoring/device-monitoring-and-reports.md
08-troubleshooting/configuration-policy-conflict-troubleshooting.md
08-troubleshooting/remote-actions-diagnostics-troubleshooting.md
```

> [!IMPORTANT]
> Autopilot hardware hashes, serial numbers, and device identifiers must not be uploaded to GitHub.

---

## Windows BYOD device result

### WIN-BYOD-001

| Item | Value |
|---|---|
| Device name | WIN-BYOD-001 |
| Device type | Laptop |
| Ownership | Personal/BYOD |
| Operating system | Windows 11 |
| Enrollment method | Windows MDM enrollment from Settings |
| Management | Microsoft Intune |
| Primary user | user03 |
| BYOD group | GRP-BYOD-Users |
| Initial compliance result | Compliant after Windows BYOD enrollment |
| Later compliance test result | Temporarily marked Noncompliant for lab validation |
| Intune ownership | Personal |
| Purpose | Windows BYOD enrollment, BYOD compliance testing, and Conditional Access blocking validation |
| Current status | Enrolled / Used for BYOD compliance and Conditional Access testing |

Initial Windows BYOD result:

```text
WIN-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Windows BYOD device.
The device appeared in Intune as managed by Intune, ownership Personal, compliance Compliant, and primary user user03.
```

Later compliance and Conditional Access result:

```text
WIN-BYOD-001 was intentionally marked Noncompliant using a temporary Windows compliance policy.
The device was then used to validate both report-only and enforced Conditional Access behavior.
The report-only test showed Failure for the noncompliant BYOD device.
The enforced-mode test blocked Microsoft 365 access because the device did not satisfy the Require compliant device grant control.
```

This device validated:

- Windows BYOD enrollment from Settings
- Personal ownership behavior in Intune
- Intune management for a BYOD Windows device
- Initial compliant BYOD state
- Temporary noncompliance using a high minimum OS version compliance policy
- Conditional Access report-only failure for a managed but noncompliant BYOD device
- Conditional Access enforced blocking for a noncompliant BYOD device

Related labs:

```text
02-device-enrollment/windows-byod-enrollment.md
04-compliance-and-conditional-access/managed-noncompliant-device-test.md
04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md
```

> [!NOTE]
> The noncompliant state for `WIN-BYOD-001` was created intentionally for lab validation. It does not mean the original BYOD enrollment lab failed. The device was first enrolled successfully, then later used as a controlled negative-test device.

---

## Android BYOD device result

### ANDROID-BYOD-001

| Item | Value |
|---|---|
| Device name | ANDROID-BYOD-001 |
| Device type | Mobile |
| Ownership | Personal/BYOD |
| Operating system | Android 15 |
| Device model | moto g34 5G |
| Enrollment method | Android Enterprise personally owned work profile |
| Management | Microsoft Intune |
| Primary user | user03 |
| BYOD group | GRP-BYOD-Users |
| Compliance | Compliant |
| Intune ownership | Personal |
| App deployment tests | Microsoft Authenticator, Outlook, Teams |
| Purpose | Android BYOD work profile enrollment and Managed Google Play app deployment |
| Current status | Enrolled / Intune managed / Personal / Compliant / Work profile created / Authenticator, Outlook, and Teams deployed |

This device validated:

- Managed Google Play connection to Intune
- Android Enterprise work profile enrollment
- Personally owned Android enrollment
- Company Portal sign-in
- Work profile creation
- Intune Android device visibility
- Personal ownership in Intune
- Compliance status in Intune
- Microsoft Authenticator required app assignment
- Microsoft Outlook and Microsoft Teams Managed Google Play app deployment
- Work profile app installation validation

Final Android BYOD result:

```text
ANDROID-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Android Enterprise work profile device.
Microsoft Authenticator, Outlook, and Teams installed successfully inside the Android Work profile.
```

Related labs:

```text
02-device-enrollment/android-byod-enrollment.md
05-application-deployment/android-managed-google-play-app-deployment.md
```

---

## iOS/iPadOS BYOD device result

### IOS-BYOD-001

| Item | Value |
|---|---|
| Device name | IOS-BYOD-001 |
| Device type | Mobile |
| Ownership | Personal/BYOD |
| Operating system | iOS/iPadOS |
| Enrollment method | Company Portal enrollment planned |
| Management | Microsoft Intune |
| Test user | user04 |
| BYOD group | GRP-BYOD-Users |
| Purpose | iOS/iPadOS BYOD enrollment test |
| Current status | In Progress / Admin prerequisites completed / Physical enrollment pending |

Completed admin prerequisites:

- iOS/iPadOS platform enrollment allowed
- Personally owned iOS/iPadOS devices allowed
- BYOD user group confirmed
- Test user license confirmed
- Apple MDM Push Certificate created
- Apple MDM Push Certificate uploaded to Intune
- Apple MDM Push Certificate active in Intune

Pending device-side steps:

- Physical iPhone/iPad enrollment
- Company Portal sign-in
- Management profile installation
- Intune iOS/iPadOS device validation

Related lab:

```text
02-device-enrollment/ios-byod-enrollment.md
```

---

## Device naming convention

| Naming pattern | Meaning |
|---|---|
| WIN-CORP-### | Corporate Windows device |
| WIN-AUTOPILOT-### | Windows Autopilot test device |
| WINAUTO### | Final Autopilot-generated Windows device name |
| WIN-BYOD-### | Personal Windows BYOD test device |
| ANDROID-BYOD-### | Personal Android BYOD test device |
| IOS-BYOD-### | Personal iOS/iPadOS BYOD test device |

---

## Device lifecycle tracking

| Status | Meaning |
|---|---|
| Planned | Device is documented but not tested |
| In progress | Lab work is active |
| Admin prerequisites completed | Portal-side prerequisites are complete, but physical device validation is pending |
| Enrolled | Device enrolled into Intune |
| Compliant | Device meets compliance rules |
| Noncompliant | Device fails compliance rules |
| Temporarily marked Noncompliant | Device was intentionally made noncompliant for controlled lab validation |
| Corporate | Device is treated as a corporate-owned device in Intune |
| Personal | Device is treated as a personally owned/BYOD device in Intune |
| Work profile created | Android Enterprise work profile exists |
| App deployment tested | Device has been used for Intune app deployment validation |
| Configuration profiles tested | Device has received configuration profiles |
| Endpoint security tested | Device has received endpoint security policies |
| Compliance and Conditional Access validated | Device has been used for compliance and Conditional Access testing |
| Autopilot enrolled | Device completed Windows Autopilot provisioning |
| Retired | Device removed from Intune management |
| Wiped | Device reset or removed through wipe action |
| Discarded | Device no longer used |

---

## Remote action lifecycle summary

| Device | Remote action | Result | Related lab |
|---|---|---|---|
| WINAUTO452 | Sync | Completed | `07-remote-actions-and-monitoring/device-sync-remote-actions.md` |
| WINAUTO452 | Restart | Completed | `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` |
| WINAUTO452 | Retire | Completed | `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` |
| WINAUTO452 | Collect diagnostics | Completed | `07-remote-actions-and-monitoring/collect-diagnostics.md` |
| WIN-CORP-001 | Wipe | Completed | `07-remote-actions-and-monitoring/restart-retire-wipe-actions.md` |

---

## Screenshot folder mapping

| Lab area | Screenshot folder |
|---|---|
| Windows enrollment | screenshots/sanitized/device-enrollment/ |
| Autopilot enrollment | screenshots/sanitized/device-enrollment/ |
| BYOD enrollment | screenshots/sanitized/device-enrollment/ |
| Compliance and Conditional Access | screenshots/sanitized/compliance-and-conditional-access/ |
| Application deployment | screenshots/sanitized/application-deployment/ |
| Configuration profiles | screenshots/sanitized/configuration-profiles/ |
| Endpoint security | screenshots/sanitized/endpoint-security/ |
| Remote actions | screenshots/sanitized/remote-actions-and-monitoring/ |
| Troubleshooting | Screenshots reused from the source lab folders |

> [!NOTE]
> The 04 lab screenshots use the combined folder `screenshots/sanitized/compliance-and-conditional-access/` because compliance policy testing and Conditional Access testing are part of the same project section.

---

## Security and privacy notes

This is a public learning repository.

Do not upload:

- Real tenant IDs
- Full real email addresses
- Passwords
- MFA QR codes
- Device serial numbers
- Device IDs
- Object IDs
- Autopilot hardware hashes
- BitLocker recovery keys
- Android IMEI numbers
- iOS serial numbers
- Phone numbers
- Internal IP addresses
- Diagnostic ZIP package contents
- Unsanitized screenshots
- Production company data

---

## Current status

| Task | Status |
|---|---|
| Device inventory file created | Completed |
| WIN-CORP-001 enrollment documented | Completed |
| WIN-CORP-001 app deployment documented | Completed |
| WIN-CORP-001 wipe lifecycle documented | Completed |
| WINAUTO452 Autopilot enrollment documented | Completed |
| WINAUTO452 configuration profiles verified | Completed |
| WINAUTO452 endpoint security policies verified | Completed |
| WINAUTO452 Windows compliance policy verified | Completed |
| WINAUTO452 remote actions lifecycle documented | Completed |
| WINAUTO452 retire lifecycle documented | Completed |
| WIN-BYOD-001 Windows BYOD enrollment documented | Completed |
| WIN-BYOD-001 noncompliant BYOD Conditional Access testing documented | Completed |
| ANDROID-BYOD-001 Android BYOD enrollment documented | Completed |
| ANDROID-BYOD-001 Managed Google Play app deployment documented | Completed |
| IOS-BYOD-001 admin prerequisites documented | In Progress / Admin prerequisites completed |
| iOS/iPadOS physical device enrollment | Pending |

---

## Next step

Recommended next project cleanup task:

```text
Final visual review of README.md, lab-implementation-roadmap.md, and device-inventory.md after upload.
```

Optional future hands-on lab:

```text
02-device-enrollment/ios-byod-enrollment.md
```

This optional lab requires a physical iPhone or iPad.
