# Company Scenario

This file describes the virtual company used throughout this MD-102 hands-on lab project.

---

## Company Name

Contoso Startup Lab

---

## Company Overview

Contoso Startup Lab is a fictional small business used for Microsoft Intune and MD-102 hands-on practice.

The company represents a modern cloud-managed workplace that uses Microsoft Entra ID for identity and Microsoft Intune for endpoint management.

This lab environment is designed to simulate common endpoint administration tasks such as device enrollment, configuration profiles, compliance policies, Conditional Access, application deployment, endpoint security, monitoring, and troubleshooting.

---

## Company Size

Contoso Startup Lab has approximately 15 users.

The lab includes a small set of test users, a lab administrator account, pilot users, corporate Windows devices, and personally owned BYOD devices.

---

## Device Environment

The company uses a mixed device environment.

| Device Type | Ownership | Platform | Purpose |
|---|---|---|---|
| Corporate laptops | Company-owned | Windows 11 | Managed corporate endpoint testing |
| Autopilot laptops | Company-owned | Windows 11 | Windows Autopilot provisioning testing |
| BYOD laptops | Personally owned | Windows 11 | Personal device access and enrollment testing |
| Mobile devices | Personally owned | Android and iOS | Mobile BYOD enrollment and app protection testing |

---

## Planned Lab Devices

| Device Name | Device Type | Ownership | Operating System | Planned Use |
|---|---|---|---|---|
| WIN-CORP-001 | Laptop | Corporate | Windows 11 | Main corporate Intune-managed device |
| WIN-AUTOPILOT-001 | Laptop | Corporate | Windows 11 | Windows Autopilot user-driven enrollment |
| WIN-BYOD-001 | Laptop | Personal/BYOD | Windows 11 | Unmanaged BYOD browser sign-in test |
| WIN-BYOD-002 | Laptop | Personal/BYOD | Windows 11 | Windows BYOD enrollment test |
| ANDROID-BYOD-001 | Mobile | Personal/BYOD | Android | Android personally owned work profile test |
| IOS-BYOD-001 | Mobile | Personal/BYOD | iOS | iOS BYOD enrollment test |

---

## Identity Environment

Contoso Startup Lab uses Microsoft Entra ID for cloud identity and access management.

The lab identity setup will include:

- Lab administrator account
- Standard test users
- Pilot user group
- Windows user group
- BYOD user group
- Mobile user group
- IT admin group
- Autopilot device group

---

## Planned Lab Users

| User Type | Example Account | Purpose |
|---|---|---|
| Lab administrator | admin01 | Manage the lab tenant and Intune configuration |
| Pilot user | user01 | Main test user for enrollment, apps, compliance, and Conditional Access |
| Standard users | user02, user03, user04, user05 | Additional users for future assignment and policy testing |

---

## Planned Lab Groups

| Group Name | Purpose |
|---|---|
| GRP-All-Lab-Users | General lab user targeting |
| GRP-Pilot-Users | Pilot testing for policies and apps |
| GRP-Windows-Users | Windows user targeting |
| GRP-BYOD-Users | BYOD user targeting |
| GRP-Mobile-Users | Android and iOS user targeting |
| GRP-IT-Admins | Lab administrator targeting |
| GRP-Autopilot-Devices | Windows Autopilot device targeting |

---

## Management Tools

| Tool | Purpose |
|---|---|
| Microsoft Intune | Device enrollment, configuration, compliance, app deployment, endpoint security, monitoring, and remote actions |
| Microsoft Entra ID | Cloud identity, users, groups, device identity, and Conditional Access |
| Windows Autopilot | Cloud-based provisioning for corporate Windows devices |
| Company Portal | User-facing app installation and device setup experience |
| Microsoft 365 Apps | Productivity app deployment and sign-in testing |

---

## Management Goals

This lab project will demonstrate how an endpoint administrator manages a small company environment from zero.

The main goals are to:

- Create Microsoft Entra ID users and groups
- Assign Intune and Microsoft 365 licenses
- Configure automatic MDM enrollment
- Enroll corporate Windows devices into Intune
- Configure Windows Autopilot for corporate device provisioning
- Enroll and compare BYOD devices
- Create Windows configuration profiles
- Create compliance policies
- Test Conditional Access in report-only mode before enforcement
- Deploy Microsoft Store apps
- Deploy Win32 apps
- Deploy Microsoft 365 Apps
- Configure Microsoft Defender Antivirus policy
- Configure Windows Firewall policy
- Configure BitLocker disk encryption policy
- Test Attack Surface Reduction policy
- Test Windows Security Baseline policy
- Use remote actions such as sync, restart, retire, wipe, and collect diagnostics
- Review Intune monitoring and reporting
- Document troubleshooting scenarios

---

## Example Real-World Scenario

Contoso Startup Lab wants to manage corporate and personal devices securely while allowing users to access Microsoft 365 resources.

A typical access flow in this lab will be:

```text
User signs in to Microsoft 365
-> Microsoft Entra ID evaluates the sign-in
-> Conditional Access checks the policy requirements
-> Intune provides device compliance status
-> Access is allowed or blocked based on the policy result
```

This helps demonstrate the relationship between identity, device compliance, and access control.

---

## Lab Safety and Privacy Statement

This project is built for learning and portfolio purposes only.

The lab environment is fictional, isolated, and not connected to any production company environment.

The devices used in this lab are retired lab-only test devices. They do not contain production company data and may be reset, wiped, or discarded after lab completion.

Before uploading screenshots to GitHub, sensitive information must be hidden or removed.

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
- Internal IP addresses
- Unsanitized screenshots
- Production company data

---

## Current Status

| Task | Status |
|---|---|
| Company scenario documented | Completed |
| Device inventory documented | Completed |
| Lab implementation roadmap documented | Planned |
| Identity and groups lab started | Planned |

---

## Next Step

Create the lab roadmap file:

```text
00-project-overview/lab-implementation-roadmap.md
```
