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

Completed hands-on work:

- Microsoft Intune tenant verified
- Microsoft Entra ID lab users created
- Microsoft Entra ID lab groups created
- Intune licenses assigned to lab users
- Microsoft 365 Business Premium license assigned to user01
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
- Microsoft 365 Apps deployment created for Autopilot lab

Current focus:

- Complete Autopilot OOBE sign-in with user01
- Confirm Autopilot device appears in Intune
- Confirm Microsoft Entra join and Intune enrollment
- Confirm Microsoft 365 Apps install status
- Test Outlook, Excel, and PowerPoint sign-in
- Upload remaining sanitized screenshots as available

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
| Phase 19 | Microsoft 365 Apps deployment for Autopilot lab | Created / In progress |
| Phase 20 | Complete Autopilot OOBE enrollment verification | In progress |
| Phase 21 | Verify Microsoft 365 Apps install and sign-in | In progress |
| Phase 22 | Enroll BYOD Windows devices | Planned |
| Phase 23 | Enroll Android BYOD devices | Planned |
| Phase 24 | Enroll iOS BYOD devices | Planned |
| Phase 25 | Windows Firewall endpoint security policy | Planned |
| Phase 26 | BitLocker policy | Planned |
| Phase 27 | Attack Surface Reduction policy | Planned |
| Phase 28 | Remote actions and monitoring | Planned |
| Phase 29 | Troubleshooting labs | Planned |

## Completed Lab Milestones

### Identity and Access Preparation

- Lab users created
- Lab groups created
- Standard user accounts prepared
- Lab admin account prepared
- Intune licenses assigned
- Microsoft 365 Business Premium license assigned to user01 for Office app testing

### Windows Enrollment Preparation

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

### Windows Compliance Policy

| Item | Value |
|---|---|
| Policy name | Windows 11 Basic Compliance |
| Platform | Windows 10 and later |
| Assignment | All devices |
| Test device | `WIN-CORP-001` |
| Compliance result | Compliant |

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

### Configuration Profiles

- Basic Microsoft Edge startup configuration profile completed
- Corporate wallpaper configuration profile completed

### Application Deployment

- Microsoft Store app deployment completed
- Win32 7-Zip app deployment completed
- Microsoft 365 Apps deployment created for Autopilot testing

### Endpoint Security

- Microsoft Defender Antivirus endpoint security policy completed

### Autopilot

- Autopilot device group created
- Autopilot deployment profile created
- Hardware hash imported
- Autopilot device added to group
- Profile status changed to Assigned
- OOBE verification still in progress

## Next Planned Work

The next planned project task is to complete Autopilot and Microsoft 365 Apps validation.

Planned next sequence:

1. Complete OOBE sign-in as user01.
2. Confirm Autopilot device appears under Windows devices in Intune.
3. Confirm Microsoft Entra joined status.
4. Confirm device is managed by Intune.
5. Confirm Microsoft 365 Apps install status.
6. Test Outlook, Excel, and PowerPoint sign-in.
7. Update Autopilot and Microsoft 365 Apps documentation from In progress to Completed.
8. Add sanitized screenshots when available.
9. Continue BYOD enrollment labs later.
10. Continue endpoint security labs later.

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

## Notes

This repository documents both planning and hands-on implementation.

Any completed configuration should only be marked completed after it has been tested in the lab tenant.

Screenshots must be sanitized before being uploaded.

Do not upload sensitive tenant or device information, including:

- Passwords
- MFA QR codes
- Tenant IDs
- Full real email addresses
- Device serial numbers
- BitLocker recovery keys
- Autopilot hardware hashes
- Internal IP addresses
- Unsanitized screenshots
