# MD-102 Intune Virtual Company Lab

This repository documents a hands-on Microsoft Intune and MD-102 lab environment.

The project simulates a small company using Microsoft Entra ID, Microsoft Intune, Windows device enrollment, Windows Autopilot, compliance policies, Conditional Access, application deployment, endpoint security, BYOD enrollment, remote actions, monitoring, and troubleshooting.

---

## Project Goal

The goal of this project is to build practical Microsoft Intune administration experience and document each lab in a professional GitHub portfolio format.

This project is designed to show real-world endpoint administration skills, including:

- Creating and managing Microsoft Entra ID users and groups
- Assigning licenses to test users
- Enrolling Windows devices into Microsoft Intune
- Troubleshooting Intune enrollment issues
- Configuring compliance policies
- Testing Conditional Access
- Deploying applications
- Managing endpoint security settings
- Using Windows Autopilot
- Supporting BYOD scenarios
- Monitoring and troubleshooting devices

---

## Virtual Company Scenario

The lab company is called **Contoso Startup Lab**.

Contoso Startup Lab represents a small organization with a mixed device environment.

The company includes:

- Corporate-owned Windows laptops
- Personal/BYOD Windows laptops
- Android BYOD devices
- iOS BYOD devices
- Microsoft Entra ID users and groups
- Microsoft Intune device management
- Microsoft 365 Apps
- Conditional Access and compliance controls

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
│   └── ios-byod-enrollment.md
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
│   └── company-portal-self-service-apps.md
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
    ├── conditional-access-troubleshooting.md
    ├── office-app-signin-troubleshooting.md
    └── autopilot-motherboard-replacement-troubleshooting.md
```

> [!NOTE]
> Some files in the structure are planned future labs. They will be added or updated as the hands-on project progresses.

---

## Current Project Status

| Task | Status |
|---|---|
| GitHub repository created | Completed |
| Initial README created | Completed |
| Project overview folder created | Completed |
| Company scenario documented | Completed |
| Device inventory documented | Completed |
| Lab roadmap documented | Completed |
| Identity and groups lab completed | Completed |
| Windows OOBE enrollment lab completed | Completed |
| Microsoft Store app deployment lab completed | Completed |
| Win32 app deployment lab completed | Completed |
| Microsoft 365 Apps deployment lab completed | Completed |
| Windows Autopilot lab completed | Completed |
| Endpoint security policy labs | Next |
| Compliance and Conditional Access labs | Planned |
| BYOD enrollment labs | Planned |
| Remote actions and monitoring labs | Planned |
| Troubleshooting documentation | Planned |

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
- Used GRP-Pilot-Users for app deployment targeting
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

- Reimaged a spare Windows 11 device
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
- Waited for the Autopilot profile status to show Assigned
- Signed in during OOBE as user01
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

### 05 - Microsoft Store App Deployment

Documented in:

```text
05-application-deployment/microsoft-store-app-deployment.md
```

Completed work:

- Created Microsoft Store apps using **Microsoft Store app (new)**
- Assigned required apps to GRP-Pilot-Users
- Assigned available/self-service apps to GRP-Pilot-Users
- Synced WIN-CORP-001 after app assignment
- Verified Company Portal installation status in Intune
- Verified required apps installed in Company Portal
- Verified available apps appeared in Company Portal with an install option
- Added sanitized screenshots

Required apps tested:

```text
Company Portal
VLC UWP
Slack
```

Available apps tested:

```text
ChatGPT
WhatsApp
```

Observed result:

```text
Required apps installed automatically.
Available apps appeared in Company Portal for user self-service installation.
```

---

### 05 - Win32 App Deployment: 7-Zip

Documented in:

```text
05-application-deployment/win32-app-deployment-7zip.md
```

Completed work:

- Prepared 7-Zip Win32 source folder
- Packaged the installer as `.intunewin`
- Uploaded the Win32 app to Microsoft Intune
- Configured install and uninstall commands
- Configured file-based detection rule
- Assigned the app as Required to GRP-Pilot-Users
- Verified install status in Intune
- Verified local endpoint installation
- Added sanitized screenshots

Observed result:

```text
7-Zip was deployed as a Win32 app using Microsoft Intune.
```

---

### 05 - Microsoft 365 Apps Deployment

Documented in:

```text
05-application-deployment/microsoft-365-apps-autopilot-deployment.md
```

Completed work:

- Verified user01 licensing for Microsoft 365 Apps
- Created Microsoft 365 Apps deployment in Intune
- Configured Microsoft 365 Apps using XML data
- Used the Microsoft 365 Apps for business product ID
- Assigned Microsoft 365 Apps as Required to GRP-Pilot-Users
- Verified required install intent reached the managed Windows device
- Verified Microsoft 365 Apps installed status in Intune
- Validated Microsoft 365 Apps deployment after Autopilot enrollment
- Added sanitized screenshots

Observed result:

```text
Microsoft 365 Apps installed successfully through Intune and were validated as part of the post-Autopilot app deployment flow.
```

---

## Completed Modern Endpoint Deployment Flow

The completed labs now demonstrate this full modern endpoint management chain:

```text
Microsoft Entra users and groups
-> Intune enrollment
-> Microsoft Store app deployment
-> Win32 app deployment
-> Microsoft 365 Apps deployment
-> Windows Autopilot registration
-> Autopilot OOBE enrollment
-> Corporate Intune-managed device
-> Required apps installed after enrollment
-> Company Portal validation
```

This creates a strong real-world portfolio scenario for MD-102 preparation.

---

## Skills This Project Demonstrates

This project demonstrates practical skills in:

- Microsoft Intune administration
- Microsoft Entra ID user and group management
- Windows device enrollment
- Intune enrollment troubleshooting
- Automatic MDM enrollment review
- Windows Autopilot preparation
- Windows Autopilot hardware hash import
- Windows Autopilot deployment profile configuration
- Windows Autopilot user-driven enrollment
- Corporate device provisioning
- Device compliance visibility
- Conditional Access planning
- Microsoft Store app deployment
- Required app assignment
- Available app assignment through Company Portal
- Win32 app deployment
- Win32 app packaging with `.intunewin`
- Win32 app install and uninstall command configuration
- Win32 app detection rule configuration
- Microsoft 365 Apps deployment
- Post-Autopilot app deployment validation
- Company Portal app validation
- Microsoft Defender Antivirus policy planning
- Windows Firewall policy planning
- BitLocker encryption policy planning
- Attack Surface Reduction policy planning
- Windows Security Baseline planning
- BYOD management planning
- Device monitoring and reports planning
- Intune troubleshooting documentation

---

## How to Use This Repository

This repository is updated as each lab is completed.

Each lab document includes:

- Objective
- Lab environment
- Why the lab matters
- Prerequisites
- Steps performed
- Test result
- Screenshots
- Troubleshooting notes
- Security and privacy notes

---

## Screenshot Storage

Sanitized screenshots are stored under:

```text
screenshots/sanitized/
```

Example folders:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/application-deployment/
screenshots/sanitized/endpoint-security/
```

---

## Privacy and Security

This is a public learning repository.

Do not upload sensitive information, including:

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

All screenshots must be sanitized before uploading to GitHub.

---

## Next Step

Continue to endpoint security policy labs.

Recommended next lab:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

After Defender Antivirus, continue with:

```text
06-endpoint-security/windows-firewall-policy.md
06-endpoint-security/bitlocker-encryption-policy.md
06-endpoint-security/attack-surface-reduction-policy.md
06-endpoint-security/windows-security-baseline.md
```

These next labs will demonstrate how Intune can enforce endpoint protection, firewall configuration, encryption, attack surface reduction, and security baseline settings on managed Windows devices.

---

## Notes

This project is for learning, portfolio building, and MD-102 preparation.

The environment, company name, users, devices, and screenshots are fictional, test-only, or sanitized.
