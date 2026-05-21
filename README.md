# MD-102 Intune Virtual Company Lab

This repository documents a hands-on Microsoft Intune and MD-102 lab environment.

The project simulates a small company using Microsoft Entra ID, Microsoft Intune, Windows device enrollment, Windows Autopilot, BYOD enrollment, configuration profiles, application deployment, endpoint security, compliance policies, Conditional Access, remote actions, monitoring, and troubleshooting.

---

## Project Goal

The goal of this project is to build practical Microsoft Intune administration experience and document each lab in a professional GitHub portfolio format.

This project demonstrates real-world endpoint administration skills, including:

- Creating and managing Microsoft Entra ID users and groups
- Assigning licenses to test users
- Enrolling Windows devices into Microsoft Intune
- Enrolling BYOD Windows and Android devices
- Troubleshooting Intune enrollment issues
- Configuring Windows device configuration profiles
- Deploying corporate device restrictions
- Deploying corporate desktop personalization settings
- Deploying Microsoft Store apps
- Deploying Win32 apps
- Deploying Microsoft 365 Apps
- Deploying Android Managed Google Play apps
- Using Windows Autopilot for corporate provisioning
- Managing endpoint security settings
- Validating Defender Antivirus, Firewall, BitLocker, Attack Surface Reduction, and Windows Security Baseline policies
- Deploying and validating compliance policies and Conditional Access
- Executing and monitoring remote actions
- Reviewing Intune device monitoring reports
- Documenting real troubleshooting case studies

---

## Virtual Company Scenario

The lab company is called **Contoso Startup Lab**.

Contoso Startup Lab represents a small organization with a mixed device environment.

The company includes:

- Corporate-owned Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD devices
- Planned iOS BYOD devices
- Microsoft Entra ID users and groups
- Microsoft Intune device management
- Microsoft 365 Apps
- Configuration profiles
- Endpoint security policies
- Compliance policies for device health validation
- Conditional Access for identity and device-based access control
- Remote actions and monitoring workflows
- Troubleshooting documentation

Detailed scenario documentation:

```text
00-project-overview/company-scenario.md
```

---

## Lab Sections

| Section | Area |
|---|---|
| 00 | Project Overview |
| 01 | Identity and Groups |
| 02 | Device Enrollment |
| 03 | Configuration Profiles |
| 04 | Compliance and Conditional Access |
| 05 | Application Deployment |
| 06 | Endpoint Security |
| 07 | Remote Actions and Monitoring |
| 08 | Troubleshooting |

---

## Repository Structure

```text
md102-intune-virtual-company-lab/
├── README.md
├── 00-project-overview/
│   ├── company-scenario.md
│   ├── device-inventory.md
│   └── lab-implementation-roadmap.md
├── 01-identity-and-groups/
│   └── users-and-groups.md
├── 02-device-enrollment/
│   ├── windows-oobe-enrollment.md
│   ├── windows-autopilot-user-driven-enrollment.md
│   ├── windows-byod-enrollment.md
│   ├── android-byod-enrollment.md
│   └── ios-byod-enrollment.md                          [in progress]
├── 03-configuration-profiles/
│   ├── windows-basic-configuration-profile.md
│   ├── windows-corporate-wallpaper-policy.md
│   └── windows-device-restrictions-profile.md
├── 04-compliance-and-conditional-access/
│   ├── windows-basic-compliance-policy.md
│   ├── conditional-access-compliant-device.md
│   ├── managed-noncompliant-device-test.md
│   └── conditional-access-enforced-mode-test.md
├── 05-application-deployment/
│   ├── microsoft-store-app-deployment.md
│   ├── win32-app-deployment-7zip.md
│   ├── microsoft-365-apps-autopilot-deployment.md
│   └── android-managed-google-play-app-deployment.md
├── 06-endpoint-security/
│   ├── windows-defender-antivirus-policy.md
│   ├── windows-firewall-policy.md
│   ├── bitlocker-encryption-policy.md
│   ├── attack-surface-reduction-policy.md
│   └── windows-security-baseline.md
├── 07-remote-actions-and-monitoring/
│   ├── device-sync-remote-actions.md
│   ├── restart-retire-wipe-actions.md
│   ├── collect-diagnostics.md
│   └── device-monitoring-and-reports.md
└── 08-troubleshooting/
    ├── intune-enrollment-troubleshooting.md
    ├── configuration-policy-conflict-troubleshooting.md
    ├── remote-actions-diagnostics-troubleshooting.md
    └── troubleshooting-summary.md
```

> [!NOTE]
> `ios-byod-enrollment.md` is still in progress because the Intune admin prerequisites are completed, but physical iPhone or iPad enrollment is pending hardware availability. The previous Company Portal self-service app lab was removed from scope.

---

## Current Project Status

| Task | Status |
|---|---|
| GitHub repository created | Completed |
| Project overview documentation | Completed |
| Device inventory documentation | Completed |
| Lab roadmap documentation | Completed |
| Identity and groups lab | Completed |
| Windows OOBE enrollment lab | Completed |
| Windows Autopilot user-driven enrollment lab | Completed |
| Windows BYOD enrollment lab | Completed |
| Android BYOD work profile enrollment lab | Completed |
| iOS BYOD enrollment lab | In Progress, admin prerequisites completed, physical device pending |
| Windows basic configuration profile lab | Completed |
| Corporate wallpaper ADMX configuration profile lab | Completed |
| USB storage block device restrictions lab | Completed |
| Microsoft Store app deployment lab | Completed |
| Win32 7-Zip app deployment lab | Completed |
| Microsoft 365 Apps deployment lab | Completed |
| Android Managed Google Play app deployment lab | Completed |
| Defender Antivirus endpoint security lab | Completed |
| Windows Firewall endpoint security lab | Completed |
| BitLocker encryption endpoint security lab | Completed |
| Attack Surface Reduction policy lab | Completed |
| Windows Security Baseline lab | Completed |
| Windows basic compliance policy lab | Completed |
| Conditional Access compliant device lab | Completed |
| Managed noncompliant device test lab | Completed |
| Conditional Access enforced mode test lab | Completed |
| Device sync remote actions lab | Completed |
| Restart, Retire, and Wipe remote actions lab | Completed |
| Collect diagnostics remote action lab | Completed |
| Device monitoring and reports lab | Completed |
| Intune enrollment troubleshooting case study | Completed |
| Configuration policy conflict troubleshooting case study | Completed |
| Remote actions diagnostics troubleshooting case study | Completed |
| Troubleshooting summary | Completed |

---

## Completed Labs

### 01 - Identity and Groups

Documented in:

```text
01-identity-and-groups/users-and-groups.md
```

Completed work:

- Created lab users
- Created Microsoft Entra ID security groups
- Configured group memberships
- Assigned license to user01
- Created pilot assignment group
- Prepared Autopilot device group
- Prepared BYOD user group
- Used groups for enrollment, application, configuration, compliance, Conditional Access, and endpoint security targeting
- Added sanitized screenshots

Observed result:

```text
Lab users and groups were created and prepared for Intune policy, app, and enrollment testing.
```

---

### 02 - Windows OOBE Enrollment

Documented in:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

Completed work:

- Reimaged a Windows 11 device
- Named the device WIN-CORP-001 during OOBE
- Selected work or school setup
- Signed in as user01
- Verified Microsoft Entra join
- Troubleshot initial MDM status of None
- Triggered manual MDM enrollment
- Verified the device in Microsoft Intune
- Confirmed device compliance visibility
- Added sanitized screenshots

Observed result:

```text
WIN-CORP-001 appeared in Intune as managed by Intune and compliant.
```

Ownership note:

```text
Intune displayed the device ownership as Personal after manual MDM enrollment.
This was later compared with Windows Autopilot corporate ownership behavior.
```

---

### 02 - Windows Autopilot User-Driven Enrollment

Documented in:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

Completed work:

- Reviewed automatic MDM enrollment settings
- Reviewed Microsoft Entra device join settings
- Created and validated Autopilot device group targeting
- Collected Windows Autopilot hardware hash from the test device
- Imported the hardware hash CSV into Intune
- Created a Windows Autopilot user-driven deployment profile
- Configured Microsoft Entra joined Autopilot profile settings
- Assigned the Autopilot profile to GRP-Autopilot-Devices
- Completed Autopilot provisioning
- Verified the device in Intune as corporate-owned
- Verified Intune management and compliance status
- Verified required apps installed after Autopilot enrollment
- Added sanitized screenshots

Final enrolled Autopilot device:

```text
WINAUTO452
```

Observed result:

```text
The Autopilot device completed user-driven enrollment, joined Microsoft Entra ID, enrolled into Microsoft Intune, appeared as a corporate device, and received required app deployments.
```

---

### 02 - Windows BYOD Enrollment

Documented in:

```text
02-device-enrollment/windows-byod-enrollment.md
```

Completed work:

- Verified user03 license assignment
- Verified user03 membership in GRP-BYOD-Users
- Configured automatic MDM enrollment scope for GRP-BYOD-Users
- Confirmed Windows personally owned device enrollment was allowed
- Prepared and renamed the test device as WIN-BYOD-001
- Added the work account from Windows Settings
- Completed Windows MDM enrollment from Settings
- Performed manual device sync
- Verified the device in the Intune Windows devices list
- Verified the Intune device overview
- Added sanitized screenshots

Observed result:

```text
WIN-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Windows BYOD device.
The device appeared as managed by Intune, ownership Personal, compliance Compliant, and primary user user03.
```

---

### 02 - Android BYOD Enrollment with Work Profile

Documented in:

```text
02-device-enrollment/android-byod-enrollment.md
```

Completed work:

- Connected Managed Google Play to Intune
- Confirmed Android Enterprise personally owned work profile enrollment was allowed
- Confirmed personally owned Android enrollment was allowed
- Enrolled the Android BYOD test device using Company Portal
- Created a separate Android Work profile
- Verified the Android device in Intune
- Confirmed ownership as Personal
- Confirmed compliance as Compliant
- Assigned Microsoft Authenticator as a required Managed Google Play app
- Confirmed Microsoft Authenticator installed in the Android Work profile
- Added sanitized screenshots

Observed result:

```text
ANDROID-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Android Enterprise work profile device.
Microsoft Authenticator was deployed successfully to the Android Work profile.
```

---

### 03 - Configuration Profiles

Documented in:

```text
03-configuration-profiles/windows-basic-configuration-profile.md
03-configuration-profiles/windows-corporate-wallpaper-policy.md
03-configuration-profiles/windows-device-restrictions-profile.md
```

Completed work:

- Created a Windows basic configuration profile using Settings catalog
- Deployed a corporate wallpaper using PowerShell staging and ADMX-backed policy
- Created a USB/removable storage restriction policy
- Assigned profiles to pilot Windows device groups
- Verified policy deployment and endpoint behavior
- Added sanitized screenshots

Observed result:

```text
Windows configuration profiles applied successfully, the corporate wallpaper was applied, and USB storage access was blocked on the test device.
```

---

### 04 - Compliance and Conditional Access

Documented in:

```text
04-compliance-and-conditional-access/windows-basic-compliance-policy.md
04-compliance-and-conditional-access/conditional-access-compliant-device.md
04-compliance-and-conditional-access/managed-noncompliant-device-test.md
04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md
```

Completed work:

- Created a Windows compliance policy
- Verified compliant state for the corporate Windows device
- Created Conditional Access policy in Report-only mode
- Validated Report-only success for a compliant device
- Created a managed noncompliant BYOD device test
- Validated Report-only failure for a noncompliant device
- Switched Conditional Access to enforced mode
- Confirmed Microsoft 365 access was blocked for the noncompliant BYOD device
- Added sanitized screenshots

Observed result:

```text
The compliance and Conditional Access flow was validated end to end, from compliant device access to noncompliant device blocking.
```

---

### 05 - Application Deployment

Documented in:

```text
05-application-deployment/microsoft-store-app-deployment.md
05-application-deployment/win32-app-deployment-7zip.md
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
05-application-deployment/android-managed-google-play-app-deployment.md
```

Completed work:

- Deployed Microsoft Store apps using Microsoft Store app (new)
- Configured required and available app assignments
- Packaged and deployed 7-Zip as a Win32 app using `.intunewin`
- Deployed Microsoft 365 Apps through Intune
- Approved and deployed Android Managed Google Play apps
- Verified app status in Intune and on endpoints
- Added sanitized screenshots

Observed result:

```text
Required apps installed automatically, available apps appeared in Company Portal, 7-Zip deployed as a Win32 app, Microsoft 365 Apps installed successfully, and Android Work profile apps deployed successfully.
```

---

### 06 - Endpoint Security

Documented in:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```

Completed work:

- Created and validated Microsoft Defender Antivirus policy
- Created and validated Windows Firewall policy
- Created and validated BitLocker encryption policy
- Confirmed OS drive encryption using local validation
- Created an Attack Surface Reduction policy in Audit mode
- Validated ASR rules locally using PowerShell
- Created and troubleshot a Windows Security Baseline
- Resolved Firewall, Defender, Device Guard, and VBS related conflicts/errors
- Verified final policy success states
- Added sanitized screenshots

Observed result:

```text
Endpoint security policies were created, assigned, monitored, troubleshot, and validated successfully on the managed Windows test device.
```

---

### 07 - Remote Actions and Monitoring

Documented in:

```text
07-remote-actions-and-monitoring/device-sync-remote-actions.md
07-remote-actions-and-monitoring/restart-retire-wipe-actions.md
07-remote-actions-and-monitoring/collect-diagnostics.md
07-remote-actions-and-monitoring/device-monitoring-and-reports.md
```

Completed work:

- Triggered remote device Sync from Intune
- Verified remote sync and local Windows sync behavior
- Triggered Restart on WINAUTO452 and monitored status
- Triggered Retire on WINAUTO452 and monitored status
- Triggered Wipe on WIN-CORP-001 and monitored status
- Collected diagnostics from a managed Windows device
- Verified diagnostics action completion from device action status
- Reviewed tenant diagnostics settings
- Reviewed Devices overview, Windows device list, Device Actions report, Noncompliant devices report, and policy assignment reports
- Added sanitized screenshots

Observed result:

```text
Remote actions were executed and validated using device-level and tenant-level monitoring views.
The Device Actions report confirmed Restart, Retire, and Wipe completed.
```

Important lifecycle note:

```text
WINAUTO452 was retired during the final remote actions lab.
WIN-CORP-001 was wiped during the final remote actions lab.
The final device lifecycle state is tracked in 00-project-overview/device-inventory.md.
```

---

### 08 - Troubleshooting

Documented in:

```text
08-troubleshooting/intune-enrollment-troubleshooting.md
08-troubleshooting/configuration-policy-conflict-troubleshooting.md
08-troubleshooting/remote-actions-diagnostics-troubleshooting.md
08-troubleshooting/troubleshooting-summary.md
```

Completed case studies:

| File | Scenario | Status |
|---|---|---|
| `intune-enrollment-troubleshooting.md` | Device joined Microsoft Entra ID but initially showed MDM None | Completed |
| `configuration-policy-conflict-troubleshooting.md` | Windows Security Baseline conflicts and VBS error 65000 | Completed |
| `remote-actions-diagnostics-troubleshooting.md` | Collect Diagnostics completed but expected monitoring path was not visible in the same way | Completed |
| `troubleshooting-summary.md` | Summary of real troubleshooting patterns and evidence handling | Completed |

Observed result:

```text
The troubleshooting section documents real issues encountered during the project and shows how each issue was investigated and resolved or worked around.
```

---

## Completed Modern Endpoint Management Flow

The completed labs demonstrate this full modern endpoint management chain:

```text
Microsoft Entra users and groups
-> Intune license assignment
-> Device enrollment
-> Windows OOBE enrollment
-> Windows Autopilot provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> Configuration profiles
-> App deployment
-> Endpoint security policies
-> Attack Surface Reduction Rules
-> Windows Security Baseline
-> Compliance policy evaluation
-> Conditional Access report-only testing
-> Conditional Access enforced blocking
-> Device sync remote action
-> Restart, Retire, and Wipe remote actions
-> Collect diagnostics remote action
-> Intune monitoring reports
-> Real troubleshooting case studies
```

This creates a strong real-world portfolio scenario for MD-102 preparation.

---

## Skills This Project Demonstrates

This project demonstrates practical skills in:

- Microsoft Intune administration
- Microsoft Entra ID user and group management
- Windows device enrollment
- Windows BYOD enrollment
- Android Enterprise BYOD work profile enrollment
- Intune enrollment troubleshooting
- Automatic MDM enrollment review and configuration
- Windows Autopilot preparation
- Windows Autopilot hardware hash import
- Windows Autopilot deployment profile configuration
- Windows Autopilot user-driven enrollment
- Corporate device provisioning
- Personal device ownership validation in Intune
- Device compliance visibility
- Compliance policy configuration and evaluation
- Conditional Access policy creation
- Conditional Access Report-only testing
- Conditional Access enforced mode testing and validation
- Noncompliant device behavior validation
- Windows configuration profile deployment
- Settings catalog profile configuration
- ADMX-backed policy configuration
- PowerShell platform script deployment
- Corporate wallpaper deployment
- Removable USB storage restriction
- Microsoft Store app deployment
- Required app assignment
- Available app assignment through Company Portal
- Win32 app deployment
- Win32 app packaging with `.intunewin`
- Win32 app install and uninstall command configuration
- Win32 app detection rule configuration
- Microsoft 365 Apps deployment
- Managed Google Play app deployment
- Microsoft Defender Antivirus policy deployment
- Windows Firewall policy deployment
- BitLocker encryption policy deployment
- Attack Surface Reduction policy deployment in Audit mode
- ASR rule endpoint validation using PowerShell
- Windows Security Baseline deployment and troubleshooting
- Security baseline conflict identification and remediation
- Device Guard and VBS error investigation
- Endpoint security policy reporting
- Device sync remote action
- Restart remote action
- Retire remote action
- Wipe remote action
- Remote action status monitoring from device and tenant views
- Collect diagnostics remote action
- Intune device monitoring and reporting
- Device inventory review
- Device Actions report review
- Noncompliant devices report review
- Configuration policy assignment status review
- Real-world troubleshooting case study writing

---

## Lab Documentation Format

Each completed lab document generally follows a consistent structure:

```text
# Lab Title

## Lab status
## Lab objective
## Why this lab matters
## Lab environment
## Prerequisites
## Configuration flow
## Steps performed
## Validation
## Final test result
## Screenshots captured
## Troubleshooting notes
## Enterprise reflection
## Security and privacy notes
## Related labs
## Key learning outcomes
## Lab conclusion
```

Some older files may use slightly different section names, but the overall documentation style is consistent.

---

## Screenshot Evidence

Sanitized screenshots are stored under:

```text
screenshots/sanitized/
```

Screenshots are organized by lab area, such as:

```text
identity-and-groups/
device-enrollment/
configuration-profiles/
compliance-and-conditional-access/
application-deployment/
endpoint-security/
remote-actions-and-monitoring/
```

Troubleshooting case studies reuse screenshots from the related source lab folders.

---

## Privacy and Security

This is a public learning and portfolio repository. Screenshots are included to demonstrate hands-on Intune administration work.

All screenshots in this repository are sanitized before upload. Sensitive information has been removed or blurred, including:

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
- IMEI numbers
- Phone numbers
- Unsanitized diagnostic package contents
- Production company data

This keeps the repository safe to share publicly while still showing real lab evidence and practical hands-on experience.

---

## Optional Future Work

The main MD-102 Intune lab project is complete across identity, enrollment, configuration profiles, application deployment, endpoint security, compliance, Conditional Access, remote actions, monitoring, and troubleshooting.

The only optional future expansion is:

| Item | Status |
|---|---|
| iOS/iPadOS BYOD physical enrollment | Pending hardware availability |

The iOS/iPadOS admin prerequisites are already documented. Physical enrollment requires access to an iPhone or iPad.

---

## Notes

This project is for learning, portfolio building, and MD-102 preparation.

The environment, company name, users, devices, and screenshots are fictional, test-only, or sanitized.
