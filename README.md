# Company Scenario

This lab simulates a small virtual company created for MD-102 learning and hands-on Microsoft Intune practice.

## Company Name

Contoso Startup Lab

## Company Size

This virtual company has approximately 15 users and a small mixed device fleet.

## Device Environment

The lab environment includes both corporate-owned and personal/BYOD devices.

Planned device types include:

- Corporate Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD mobile devices
- iPhone/iOS BYOD mobile devices

## Identity Environment

The virtual company uses Microsoft Entra ID for cloud identity and access management.

The lab includes:

- Test users
- Admin users
- Security groups
- Pilot user groups
- Windows user groups
- BYOD user groups
- Mobile user groups
- Autopilot device groups
- Device-only pilot groups for safer endpoint security testing

## Management Goal

The goal is to manage company and personal devices using Microsoft Intune and Microsoft Entra ID.

This project demonstrates how an endpoint administrator can:

- Enroll Windows devices into Intune
- Register and provision Windows devices using Windows Autopilot
- Organize users and devices with Microsoft Entra groups
- Apply configuration profiles
- Create compliance policies
- Use Conditional Access to require compliant devices
- Test corporate and BYOD access scenarios
- Deploy and manage apps
- Deploy Microsoft 365 Apps to Autopilot-enrolled devices
- Configure endpoint security policies
- Configure Windows Firewall and disk encryption policies
- Verify endpoint security results from both Intune and the local device
- Document lab results with sanitized screenshots

## Current Lab Progress

The following hands-on tasks have been completed or started:

- Microsoft Intune tenant verified
- Microsoft Entra users and groups created
- Intune licenses assigned
- Microsoft 365 Business Premium trial activated for Office app testing
- Microsoft 365 Business Premium license assigned to User 01
- Corporate Windows device enrolled
- WIN-CORP-001 confirmed as managed and compliant
- Windows compliance policy created
- Conditional Access policy created in Report-only mode
- Compliant corporate device test completed
- Unmanaged BYOD device Report-only test completed
- Basic Windows configuration profile created and tested
- Corporate wallpaper policy created and tested
- Microsoft Store app deployment completed
- Win32 7-Zip deployment completed
- Defender Antivirus endpoint security policy completed
- Windows Firewall endpoint security policy completed
- Firewall enabled for Domain, Private, and Public network profiles
- Firewall status verified in Intune and on WIN-CORP-001
- BitLocker disk encryption policy completed
- WIN-CORP-001 encrypted successfully with BitLocker
- BitLocker protection confirmed as On
- BitLocker recovery key escrow verified in Intune
- Autopilot device group created
- Autopilot deployment profile created
- Autopilot hardware hash imported
- Autopilot device profile assigned
- Autopilot OOBE enrollment completed with User 01
- Autopilot device appeared in Intune Windows devices
- Autopilot device confirmed as corporate and compliant
- Microsoft 365 Apps deployment created for Autopilot lab
- Microsoft 365 Apps installation verified
- Word sign-in verified with User 01

## Current Endpoint Security Coverage

The current endpoint security coverage includes:

| Endpoint security area | Status |
|---|---|
| Microsoft Defender Antivirus policy | Completed |
| Windows Firewall policy | Completed |
| BitLocker disk encryption policy | Completed |
| BitLocker recovery key escrow verification | Completed |
| Attack Surface Reduction policy | Planned |
| Windows Security Baseline | Planned |

## Learning Purpose

This project is created to demonstrate hands-on learning for **MD-102: Endpoint Administrator**.

The project is designed to show practical experience with Microsoft Intune, Microsoft Entra ID, Windows device management, BYOD scenarios, compliance, Conditional Access, configuration profiles, app deployment, endpoint security, Windows Autopilot, Microsoft 365 Apps deployment, Windows Firewall management, BitLocker disk encryption, recovery key verification, and troubleshooting.

## Privacy and Security Note

This is a public learning project.

All users, devices, groups, screenshots, and company details are fictional or sanitized.

No real production data, tenant secrets, passwords, device serial numbers, BitLocker recovery keys, Autopilot hardware hashes, or confidential information should be published.
