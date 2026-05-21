# Company Scenario

---

## Company Name

**Contoso Startup Lab**

---

## Overview

Contoso Startup Lab is a fictional small business (~15 users) used throughout this MD-102 hands-on lab project. It represents a modern, cloud-first workplace with no on-premises infrastructure — identity and device management run entirely through Microsoft Entra ID and Microsoft Intune.

The company supports a mixed device environment: corporate Windows laptops, personal Windows laptops, and personal Android and iOS mobile devices. This mix drives the need for both corporate provisioning workflows and BYOD enrollment paths, with compliance and Conditional Access enforcing appropriate access controls across all device types.

---

## Technology Stack

| Layer | Technology |
|---|---|
| Identity and access | Microsoft Entra ID |
| Endpoint management | Microsoft Intune |
| Corporate provisioning | Windows Autopilot |
| User app experience | Company Portal |
| Android app management | Managed Google Play |
| iOS/iPadOS enrollment | Apple MDM Push Certificate |
| Security | Defender Antivirus, Firewall, BitLocker, ASR, Security Baseline |
| Access control | Compliance policies, Conditional Access |
| Operations | Remote actions, monitoring, troubleshooting |

---

## Device Environment

| Device | Ownership | Platform | Role |
|---|---|---|---|
| WIN-CORP-001 | Company-owned (displayed as Personal after manual MDM enrollment) | Windows 11 | OOBE enrollment, early testing, Wipe validation |
| WINAUTO452 | Company-owned | Windows 11 | Primary lab device — Autopilot, profiles, apps, security, compliance, CA, remote actions |
| WIN-BYOD-001 | Personally owned | Windows 11 | BYOD enrollment, noncompliance simulation, CA enforced blocking |
| ANDROID-BYOD-001 | Personally owned | Android 15 | Android Enterprise work profile, Managed Google Play app deployment |
| IOS-BYOD-001 | Personally owned | iOS/iPadOS | Admin prerequisites complete; physical enrollment pending |

---

## Users

| Account | Role |
|---|---|
| admin01 | Lab administrator — tenant and Intune administration |
| user01 | Primary test user — Windows, Autopilot, apps, compliance, policy |
| user02 | Additional Windows policy testing |
| user03 | BYOD testing — Windows BYOD, Android BYOD, Conditional Access |
| user04 | iOS/iPadOS BYOD enrollment preparation |
| user05 | Additional policy testing |

---

## Groups

| Group | Purpose |
|---|---|
| GRP-All-Lab-Users | General lab targeting |
| GRP-Pilot-Users | Pilot testing and user-based policy assignments |
| GRP-Windows-Users | Windows user targeting |
| GRP-BYOD-Users | BYOD enrollment, app targeting, Conditional Access testing |
| GRP-Mobile-Users | Mobile device and user targeting |
| GRP-IT-Admins | Lab admin targeting |
| GRP-Autopilot-Devices | Autopilot registration and device-based policy targeting |

---

## Business Goals

Contoso Startup Lab is building its endpoint management practice from zero. The core goals are:

- Enroll and manage corporate Windows devices through Autopilot and OOBE
- Support BYOD enrollment for Windows, Android, and iOS without compromising corporate data
- Deploy required business apps automatically and make optional apps available through Company Portal
- Harden endpoints with Defender, Firewall, BitLocker, ASR rules, and Security Baseline policies
- Enforce device health through compliance policies and block noncompliant devices via Conditional Access
- Operate devices remotely using sync, restart, retire, wipe, and diagnostics actions
- Document real troubleshooting cases to build practical diagnostic experience

---

## Privacy and Lab Safety

This environment is fictional, isolated, and not connected to any production tenant.

All screenshots uploaded to this repository are sanitized before publish. The following are never included in public-facing files:

- Tenant IDs or object IDs
- Real email addresses or passwords
- MFA QR codes
- Device serial numbers, IMEI numbers, or Autopilot hardware hashes
- BitLocker recovery keys
- Internal IP addresses
- Unsanitized diagnostic package contents
- Any production company data
