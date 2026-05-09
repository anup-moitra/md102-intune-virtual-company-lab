# Lab Implementation Roadmap

This file tracks the planned implementation sequence for the MD-102 Intune virtual company lab.

## Current Status

The project has moved from planning into active hands-on implementation.

Theory chapters have been studied for:

- Active Directory foundations
- Device join types
- Microsoft Intune basics
- Intune enrollment
- Configuration profiles
- Compliance policies
- Conditional Access requiring compliant devices
- Application deployment with Microsoft Intune
- Windows Autopilot basics and provisioning flow
- Microsoft 365 Apps deployment with Intune

Completed hands-on work:

- Microsoft Intune tenant verified
- Microsoft Entra ID lab users created
- Microsoft Entra ID lab groups created
- Intune licenses assigned to lab users
- Microsoft 365 Business Premium license assigned to User 01
- Automatic MDM enrollment configured
- Corporate Windows device enrolled through Windows Out-of-Box Experience
- Device `WIN-CORP-001` enrolled into Microsoft Intune
- Windows compliance policy created
- Device `WIN-CORP-001` reported compliant
- Conditional Access policy created in Report-only mode
- Compliant corporate device access test completed
- Unmanaged BYOD device Report-only failure test completed
- Basic Windows configuration profile created and tested
- Corporate wallpaper configuration profile created and tested
- Microsoft Store app deployment completed
- Win32 7-Zip app deployment completed
- Microsoft Defender Antivirus endpoint security policy completed
- Windows Autopilot deployment profile created
- Autopilot hardware hash imported
- Autopilot profile assigned to imported device
- Autopilot user-driven OOBE enrollment completed
- Autopilot device appeared in Intune Windows devices
- Autopilot device connected to Microsoft Entra ID
- Autopilot device showed corporate ownership and compliant status
- Microsoft 365 Apps deployment completed for Autopilot lab
- Word, Excel, and PowerPoint selected in Microsoft 365 Apps deployment
- Microsoft 365 Apps installation verified in Intune
- Microsoft 365 Apps installation verified in Company Portal
- Word sign-in verified with User 01
- Sanitized screenshots added for Autopilot and Microsoft 365 Apps validation

Current focus:

- Continue with endpoint security labs
- Recommended next lab: Windows Firewall endpoint security policy
- Recommended follow-up lab: BitLocker encryption policy
- Continue updating GitHub documentation with sanitized screenshots as labs are completed

## Implementation Phases

| Phase | Task | Status |
|---|---|---|
| Phase 0 | Create GitHub repository and project documentation | Completed |
| Phase 1 | Verify Microsoft Intune tenant / trial environment | Completed |
| Phase 2 | Create Microsoft Entra ID lab users | Completed |
| Phase 3 | Create Microsoft Entra ID groups | Completed |
| Phase 4 | Assign Intune licenses to lab users | Completed |
| Phase 5 | Configure device enrollment settings | Completed |
| Phase 6 | Enroll corporate Windows device `WIN-CORP-001` | Completed |
| Phase 7 | Test unmanaged BYOD Windows device for Conditional Access | Completed |
| Phase 8 | Create basic Windows configuration profile | Completed |
| Phase 9 | Create corporate wallpaper profile | Completed |
| Phase 10 | Create Windows compliance policy | Completed |
| Phase 11 | Create Conditional Access policy requiring compliant devices | Completed |
| Phase 12 | Test compliant corporate access result | Completed |
| Phase 13 | Test unmanaged BYOD access result | Completed |
| Phase 14 | Microsoft Store app deployment lab | Completed |
| Phase 15 | Win32 7-Zip app deployment lab | Completed |
| Phase 16 | Microsoft Defender Antivirus endpoint security policy | Completed |
| Phase 17 | Create Autopilot device group and deployment profile | Completed |
| Phase 18 | Import Autopilot hardware hash and assign profile | Completed |
| Phase 19 | Microsoft 365 Apps deployment for Autopilot lab | Completed |
| Phase 20 | Complete Autopilot OOBE enrollment verification | Completed |
| Phase 21 | Verify Microsoft 365 Apps install and Word sign-in | Completed |
| Phase 22 | Windows Firewall endpoint security policy | Planned |
| Phase 23 | BitLocker policy | Planned |
| Phase 24 | Attack Surface Reduction policy | Planned |
| Phase 25 | Windows Security Baseline | Planned |
| Phase 26 | Enroll BYOD Windows devices | Planned |
| Phase 27 | Enroll Android BYOD devices | Planned |
| Phase 28 | Enroll iOS BYOD devices | Planned |
| Phase 29 | Remote actions and monitoring | Planned |
| Phase 30 | Troubleshooting labs | Planned |

## Completed Lab Milestones

### Identity and Access Preparation

Completed:

- Lab users created
- Lab groups created
- Standard user accounts prepared
- Lab admin account prepared
- Intune licenses assigned
- Microsoft 365 Business Premium license assigned to User 01 for Office app testing

Main file:

```text
01-identity-and-groups/users-and-groups.md
```

### Windows Enrollment Preparation

Completed:

- Intune tenant access verified
- MDM authority confirmed as Microsoft Intune
- Automatic MDM enrollment configured
- Lab users prepared for enrollment testing

### Corporate Windows Enrollment

| Item | Value |
|---|---|
| Device name | `WIN-CORP-001` |
| Device type | Physical laptop |
| Ownership | Corporate |
| Operating system | Windows 11 |
| Enrollment method | Windows Out-of-Box Experience work or school setup |
| Enrolled by | `user01` |
| Management | Microsoft Intune |
| Result | Successfully enrolled |

Main file:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

### Windows Compliance Policy

| Item | Value |
|---|---|
| Policy name | Windows 11 Basic Compliance |
| Platform | Windows 10 and later |
| Assignment | All devices |
| Test device | `WIN-CORP-001` |
| Compliance result | Compliant |

Main file:

```text
04-compliance-and-conditional-access/windows-basic-compliance-policy.md
```

### Conditional Access Requiring Compliant Devices

| Item | Value |
|---|---|
| Policy name | CA001 - Require compliant device for pilot users |
| Policy state | Report-only |
| Target resource | Office 365 |
| Grant control | Require device to be marked as compliant |
| Compliant test device | WIN-CORP-001 |
| BYOD test device | WIN-BYOD-001 |
| Compliant device result | Report-only: Success |
| Unmanaged BYOD result | Report-only: Failure |

Main file:

```text
04-compliance-and-conditional-access/conditional-access-compliant-device.md
```

### Configuration Profiles

Completed:

- Basic Microsoft Edge startup configuration profile completed
- Corporate wallpaper configuration profile completed

Main files:

```text
03-configuration-profiles/windows-basic-configuration-profile.md
03-configuration-profiles/windows-corporate-wallpaper-policy.md
```

### Application Deployment

Completed:

- Microsoft Store app deployment completed
- Win32 7-Zip app deployment completed
- Microsoft 365 Apps deployment completed for Autopilot testing
- Word, Excel, and PowerPoint selected
- Microsoft 365 Apps install status verified in Intune
- Microsoft 365 Apps install status verified in Company Portal
- Word sign-in verified with User 01

Main files:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

### Endpoint Security

Completed:

- Microsoft Defender Antivirus endpoint security policy completed

Main file:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Planned endpoint security labs:

```text
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```

### Windows Autopilot

Completed:

- Autopilot device group created
- Autopilot deployment profile created
- Hardware hash collected from OOBE device
- Hardware hash CSV imported into Intune
- Autopilot device added to group
- Profile status changed from Not assigned to Assigned
- OOBE sign-in completed with User 01
- Device connected to Microsoft Entra ID
- Device appeared in Intune Windows devices
- Device ownership displayed as Corporate
- Device compliance displayed as Compliant
- Sanitized screenshots added

Main file:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

## Recently Completed Milestone

The most recent completed milestone was:

```text
Windows Autopilot user-driven enrollment
+
Microsoft 365 Apps deployment validation
```

This validates the following end-to-end flow:

```text
Autopilot hardware hash imported
→ Autopilot profile assigned
→ User 01 signs in during OOBE
→ Device joins Microsoft Entra ID
→ Device enrolls into Microsoft Intune
→ Device appears as corporate and compliant
→ Microsoft 365 Apps install successfully
→ Word opens and signs in with User 01
```

## Next Planned Work

The next planned project task is to continue endpoint security configuration.

Recommended next sequence:

1. Create Windows Firewall endpoint security policy.
2. Assign the policy to the pilot group.
3. Sync the test device from Intune / Windows settings.
4. Verify firewall policy status in Intune.
5. Capture sanitized screenshots.
6. Update `06-endpoint-security/windows-firewall-policy.md`.
7. Continue with BitLocker encryption policy.
8. Continue with Attack Surface Reduction policy.
9. Continue with Windows Security Baseline.
10. Continue BYOD enrollment labs later.

## BYOD Status

BYOD enrollment has not started yet.

However, unmanaged BYOD Conditional Access testing has been completed using WIN-BYOD-001.

WIN-BYOD-001 was intentionally left unenrolled to confirm that an unmanaged device does not satisfy the compliant device requirement in the CA001 Report-only policy.

Planned BYOD scenarios:

- Windows BYOD enrollment
- Android personally owned work profile enrollment
- iOS user enrollment / Company Portal enrollment
- BYOD app protection and lighter management testing

## Screenshot Documentation Status

Screenshots are sanitized before being uploaded to GitHub.

Current screenshot status:

| Area | Status |
|---|---|
| Conditional Access screenshots | Added as available |
| Configuration profile screenshots | Added as available |
| Application deployment screenshots | Added as available |
| Endpoint security screenshots | Added as available |
| Autopilot screenshots | Added |
| Microsoft 365 Apps Autopilot screenshots | Added |
| BYOD screenshots | Pending future labs |
| Remote actions screenshots | Pending future labs |
| Troubleshooting screenshots | Pending future labs |

Suggested screenshot folder paths:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/compliance/
screenshots/sanitized/conditional-access/
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/endpoint-security/
screenshots/sanitized/remote-actions-and-monitoring/
screenshots/sanitized/troubleshooting/
```

## Documentation Update Rules

Any completed configuration should only be marked completed after it has been tested in the lab tenant.

Each completed lab should include:

- Objective
- Lab context
- Steps performed
- Test result
- Screenshots
- Troubleshooting notes
- Security/privacy notes
- Current status
- Next step

## Security and Privacy Notes

Screenshots must be sanitized before being uploaded.

Do not upload sensitive tenant or device information, including:

- Passwords
- MFA QR codes
- Tenant IDs
- Full real email addresses
- Device serial numbers
- Device IDs
- BitLocker recovery keys
- Autopilot hardware hashes
- Internal IP addresses
- Unsanitized screenshots
- Production company data

## Notes

This repository documents both planning and hands-on implementation.

The project currently has a strong completed foundation covering:

```text
Identity
Enrollment
Compliance
Conditional Access
Configuration profiles
Application deployment
Endpoint security basics
Windows Autopilot
Microsoft 365 Apps deployment
```

The next focus is to expand endpoint security and management depth.
