# Company Scenario

This file describes the virtual company used throughout this MD-102 hands-on lab project.

---

## Company Name

Contoso Startup Lab

---

## Company Size

Contoso Startup Lab is a small company with approximately 15 users and a mixed device fleet covering corporate-owned and personal/BYOD devices across Windows, Android, and iOS platforms.

---

## Device Environment

The lab environment includes both corporate-owned and personal/BYOD devices across multiple platforms.

| Device | Type | Ownership | OS |
|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate | Windows 11 |
| WIN-CORP-002 | Laptop | Corporate | Windows 11 |
| WIN-BYOD-001 | Laptop | BYOD | Windows 11 |
| Android device | Mobile | BYOD | Android |
| iOS device | Mobile | BYOD | iOS |

Corporate Windows devices are enrolled via Windows Out-of-Box Experience (OOBE) and Windows Autopilot. BYOD devices are registered through Entra ID and enrolled via Android Enterprise and Apple MDM.

---

## Identity Environment

Contoso Startup Lab uses Microsoft Entra ID for cloud identity and access management.

The lab identity setup includes:

- Lab admin user
- Standard test users
- Pilot user group
- Windows user group
- BYOD user group
- Mobile user group
- Autopilot device group
- Device-only pilot group for endpoint security policy testing

---

## Management Tools

| Tool | Purpose |
|---|---|
| Microsoft Intune | Device enrollment, configuration, compliance, app deployment, and endpoint security |
| Microsoft Entra ID | Cloud identity, group management, and Conditional Access |
| Windows Autopilot | Zero-touch corporate device provisioning |
| Microsoft 365 Apps | Productivity app deployment and licensing |
| Company Portal | Self-service app access for end users |

---

## Management Goals

This lab demonstrates how an endpoint administrator manages a small company environment end to end, covering:

- Enrolling corporate Windows devices via OOBE and Autopilot
- Registering and managing BYOD devices across Windows, Android, and iOS
- Organising users and devices using Microsoft Entra security groups
- Applying configuration profiles for browser settings, wallpaper, and device restrictions
- Creating and enforcing compliance policies
- Implementing Conditional Access requiring compliant devices
- Testing corporate and BYOD access scenarios in both report-only and enforced modes
- Deploying Microsoft Store apps, Win32 apps, and Microsoft 365 Apps
- Configuring endpoint security policies including Defender Antivirus, Windows Firewall, and BitLocker
- Verifying BitLocker recovery key escrow in Intune
- Performing remote device actions including sync, restart, retire, wipe, and diagnostics collection
- Monitoring device compliance and policy status through Intune reports
- Troubleshooting common Autopilot, enrollment, Office sign-in, and Conditional Access issues

---

## Privacy and Security Note

This is a public learning and portfolio project. All company names, users, devices, groups, screenshots, and lab details are fictional, test-only, or sanitised. No real production data, tenant secrets, passwords, device serial numbers, BitLocker recovery keys, Autopilot hardware hashes, or confidential information is published in this repository.
