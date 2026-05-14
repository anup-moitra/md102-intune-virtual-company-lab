# Device Inventory

This file tracks the lab devices used in the MD-102 Intune virtual company environment.

---

## Purpose

The purpose of this device inventory is to document all planned and active lab devices used for Microsoft Intune, Microsoft Entra ID, Windows Autopilot, BYOD enrollment, compliance, Conditional Access, application deployment, endpoint security, monitoring, and troubleshooting labs.

This file is updated as devices are enrolled, tested, reset, retired, wiped, or reused for future labs.

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
- Configuration profiles
- Required app deployment
- Endpoint security policies
- BitLocker encryption
- Remote actions

### BYOD devices

BYOD devices are personally owned test devices used to simulate employee-owned devices.

These devices should receive lighter, privacy-aware management.

BYOD testing helps compare:

```text
Unmanaged personal device
vs
Enrolled personal/BYOD device
vs
Corporate-managed device
```

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

---

## Device inventory

| Device name | Device type | Ownership | OS | Enrollment type | User | Status |
|---|---|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate lab device / Personal in Intune after manual MDM enrollment | Windows 11 | OOBE + Entra joined + Intune | user01 | Enrolled / Compliant / App deployment tested |
| WIN-AUTOPILOT-001 / WINAUTO452 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven Entra join | user01 | Autopilot enrolled / Intune managed / Corporate / Compliant / Apps installed / Configuration profiles tested / Endpoint security tested |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Windows MDM enrollment from Settings | user03 | Enrolled / Intune managed / Personal / Compliant |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android 15 | Android Enterprise personally owned work profile | user03 | Enrolled / Intune managed / Personal / Compliant / Work profile created / Authenticator, Outlook, and Teams deployed |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS/iPadOS | Company Portal enrollment planned | user04 | In Progress / Admin prerequisites completed / Physical enrollment pending |

> [!NOTE]
> During the Windows OOBE lab, Intune displayed `WIN-CORP-001` ownership as `Personal` after manual MDM enrollment. This is documented in the Windows OOBE enrollment lab and was later compared with Windows Autopilot corporate ownership behavior.

---

## Corporate Windows device result

### WIN-CORP-001

| Item | Value |
|---|---|
| Device name | WIN-CORP-001 |
| Device type | Laptop |
| Lab ownership | Corporate lab device |
| Intune ownership | Personal |
| Operating system | Windows 11 |
| Enrollment method | OOBE + manual MDM trigger |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Compliance | Compliant |
| Purpose | Main early Windows Intune test device |
| Current status | Enrolled / Compliant / Microsoft Store apps tested / Win32 7-Zip tested / Microsoft 365 Apps tested |

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

Related labs:

```text
02-device-enrollment/windows-oobe-enrollment.md
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

---

## Windows Autopilot device result

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
| Compliance | Compliant |
| Apps verified | Store apps, Win32 7-Zip, Microsoft 365 Apps |
| Configuration profiles verified | Basic Windows profile, corporate wallpaper, USB storage block |
| Endpoint security verified | Defender Antivirus, Windows Firewall, BitLocker |
| Purpose | Windows Autopilot provisioning, configuration profile, app deployment, and endpoint security test |
| Current status | Autopilot enrolled / Intune managed / Corporate / Compliant / Apps installed / Configuration profiles tested / Endpoint security tested |

This device validated:

- Hardware hash collection
- Autopilot device CSV import
- Autopilot device group targeting
- Autopilot deployment profile creation
- Autopilot deployment profile assignment
- Windows OOBE sign-in with `user01`
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

Final Autopilot result:

```text
WIN-AUTOPILOT-001 was provisioned with Windows Autopilot and appeared in Intune as WINAUTO452.
The device was managed by Microsoft Intune, marked as Corporate, showed Compliant, received required app deployments, received configuration profiles, and successfully received endpoint security policies.
```

Related labs:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
03-configuration-profiles/windows-basic-configuration-profile.md
03-configuration-profiles/windows-corporate-wallpaper-policy.md
03-configuration-profiles/windows-device-restrictions-profile.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
06-endpoint-security/windows-defender-antivirus-policy.md
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
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
| Compliance | Compliant |
| Intune ownership | Personal |
| Purpose | Windows BYOD enrollment test |
| Current status | Enrolled / Intune managed / Personal / Compliant |

Final Windows BYOD result:

```text
WIN-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Windows BYOD device.
The device appeared in Intune as managed by Intune, ownership Personal, compliance Compliant, and primary user user03.
```

Related lab:

```text
02-device-enrollment/windows-byod-enrollment.md
```

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
| Corporate | Device is treated as a corporate-owned device in Intune |
| Personal | Device is treated as a personally owned/BYOD device in Intune |
| Work profile created | Android Enterprise work profile exists |
| App deployment tested | Device has been used for Intune app deployment validation |
| Configuration profiles tested | Device has received configuration profiles |
| Endpoint security tested | Device has received endpoint security policies |
| Autopilot enrolled | Device completed Windows Autopilot provisioning |
| Noncompliant | Device fails compliance rules |
| Retired | Device removed from Intune |
| Wiped | Device reset |
| Discarded | Device no longer used |

---

## Screenshot folder mapping

| Lab area | Screenshot folder |
|---|---|
| Windows enrollment | screenshots/sanitized/device-enrollment/ |
| Autopilot enrollment | screenshots/sanitized/device-enrollment/ |
| BYOD enrollment | screenshots/sanitized/device-enrollment/ |
| Compliance testing | screenshots/sanitized/compliance/ |
| Conditional Access testing | screenshots/sanitized/conditional-access/ |
| Application deployment | screenshots/sanitized/application-deployment/ |
| Configuration profiles | screenshots/sanitized/configuration-profiles/ |
| Endpoint security | screenshots/sanitized/endpoint-security/ |
| Remote actions | screenshots/sanitized/remote-actions-and-monitoring/ |
| Troubleshooting | screenshots/sanitized/troubleshooting/ |

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
- Unsanitized screenshots
- Production company data

---

## Current status

| Task | Status |
|---|---|
| Device inventory file created | Completed |
| WIN-CORP-001 enrollment documented | Completed |
| WINAUTO452 Autopilot enrollment documented | Completed |
| WIN-BYOD-001 Windows BYOD enrollment documented | Completed |
| ANDROID-BYOD-001 Android BYOD enrollment documented | Completed |
| ANDROID-BYOD-001 Managed Google Play app deployment documented | Completed |
| IOS-BYOD-001 admin prerequisites documented | In Progress / Admin prerequisites completed |
| iOS/iPadOS physical device enrollment | Pending |
| WINAUTO452 configuration profiles verified | Completed |
| WINAUTO452 endpoint security policies verified | Completed |

---

## Next step

Recommended next endpoint security lab:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Alternative BYOD continuation:

```text
02-device-enrollment/ios-byod-enrollment.md
```
