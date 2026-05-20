# MD-102 Intune Virtual Company Lab

This repository documents a hands-on Microsoft Intune and MD-102 lab environment.

The project simulates a small company using Microsoft Entra ID, Microsoft Intune, Windows device enrollment, Windows Autopilot, BYOD enrollment, configuration profiles, application deployment, endpoint security, compliance policies, Conditional Access, remote actions, monitoring, and troubleshooting.

---

## Project goal

The goal of this project is to build practical Microsoft Intune administration experience and document each lab in a professional GitHub portfolio format.

This project is designed to show real-world endpoint administration skills, including:

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
- Validating Defender Antivirus, Firewall, and BitLocker policies
- Configuring Attack Surface Reduction Rules in Audit mode
- Deploying and troubleshooting a Windows Security Baseline
- Deploying and validating compliance policies and Conditional Access
- Executing and monitoring remote actions
- Using Intune monitoring reports
- Documenting real troubleshooting case studies

---

## Virtual company scenario

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

## Lab sections

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

## Repository structure

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
│   └── ios-byod-enrollment.md                          [in progress — admin prerequisites completed]
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
> `ios-byod-enrollment.md` is marked in progress because the admin prerequisites are completed but the physical device enrollment step is pending hardware availability. All other files in the repository are completed.

---

## Current project status

| Task | Status |
|---|---|
| GitHub repository created | Completed |
| Initial README created | Completed |
| Project overview folder created | Completed |
| Company scenario documented | Completed |
| Device inventory documented | Completed |
| Lab roadmap documented | Completed |
| Identity and groups lab | Completed |
| Windows OOBE enrollment lab | Completed |
| Windows Autopilot user-driven enrollment lab | Completed |
| Windows BYOD enrollment lab | Completed |
| Android BYOD work profile enrollment lab | Completed |
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
| iOS BYOD enrollment lab | In Progress — admin prerequisites completed, pending physical device |

---

## Completed labs

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
- Used groups for later enrollment, app, configuration, and security policy targeting
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

Final enrolled BYOD device:

```text
WIN-BYOD-001
```

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

Final enrolled Android BYOD device:

```text
ANDROID-BYOD-001
```

Observed result:

```text
ANDROID-BYOD-001 enrolled successfully into Microsoft Intune as a personally owned Android Enterprise work profile device.
Microsoft Authenticator was deployed successfully to the Android Work profile.
```

---

### 03 - Windows Basic Configuration Profile

Documented in:

```text
03-configuration-profiles/windows-basic-configuration-profile.md
```

Completed work:

- Created a Windows configuration profile using the Settings catalog
- Configured basic Windows device settings
- Assigned the profile to the Autopilot device group
- Synced the target Windows device
- Verified policy deployment status in Intune
- Added sanitized screenshots

Observed result:

```text
The Windows basic configuration profile was created, assigned, and validated through Microsoft Intune.
```

---

### 03 - Corporate Wallpaper ADMX Configuration Profile

Documented in:

```text
03-configuration-profiles/windows-corporate-wallpaper-policy.md
```

Completed work:

- Rebuilt the corporate wallpaper lab after the earlier Desktop Image Url approach failed
- Created a PowerShell platform script to stage the wallpaper file locally
- Downloaded the wallpaper from the GitHub raw image URL
- Saved the wallpaper under C:\ProgramData\HomeLab\Wallpapers
- Created an ADMX-backed Desktop Wallpaper user configuration profile
- Configured the wallpaper path using a normal local Windows file path
- Assigned the script to GRP-Autopilot-Devices
- Assigned the wallpaper policy to GRP-Pilot-Users
- Verified script status as Succeeded on WINAUTO452
- Verified ADMX wallpaper policy status as Success
- Confirmed the corporate wallpaper applied on the endpoint
- Added sanitized screenshots

Observed result:

```text
The corporate wallpaper was staged locally and applied successfully on WINAUTO452 using an ADMX-backed Desktop Wallpaper user policy.
```

---

### 03 - Windows Device Restrictions: Block USB Storage

Documented in:

```text
03-configuration-profiles/windows-device-restrictions-profile.md
```

Completed work:

- Created a Windows Settings catalog configuration profile
- Configured the removable storage access setting
- Enabled "All Removable Storage classes: Deny all access"
- Assigned the policy to GRP-Autopilot-Devices
- Verified the target device reported policy success
- Tested USB/removable storage access on WINAUTO452
- Confirmed Windows blocked access to the removable drive
- Added sanitized screenshots

Observed result:

```text
WINAUTO452 received the policy successfully, and removable USB storage access was blocked with an "Access is denied" message.
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

### 05 - Android Managed Google Play App Deployment

Documented in:

```text
05-application-deployment/android-managed-google-play-app-deployment.md
```

Completed work:

- Connected Managed Google Play to the Intune tenant
- Approved Microsoft Outlook and Microsoft Teams in Managed Google Play
- Assigned Outlook as Required to GRP-BYOD-Users
- Assigned Teams as Required to GRP-BYOD-Users
- Verified the Android BYOD device received the required app assignments
- Confirmed Outlook and Teams installed into the Android Work profile
- Added sanitized screenshots

Observed result:

```text
Microsoft Outlook and Microsoft Teams were deployed successfully through Managed Google Play
to the Android Enterprise work profile on ANDROID-BYOD-001.
```

---

### 06 - Microsoft Defender Antivirus Policy

Documented in:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Completed work:

- Created a Microsoft Defender Antivirus endpoint security policy
- Selected Windows as the platform
- Selected Microsoft Defender Antivirus as the profile
- Configured core Defender Antivirus settings
- Enabled PUA protection
- Configured threat remediation actions
- Assigned the policy to GRP-Autopilot-Devices
- Verified WINAUTO452 reported policy status as Success
- Added sanitized screenshots

Observed result:

```text
The Defender Antivirus policy applied successfully to the Autopilot-enrolled corporate Windows device WINAUTO452.
```

---

### 06 - Windows Firewall Policy

Documented in:

```text
06-endpoint-security/windows-firewall-policy.md
```

Completed work:

- Created a Windows Firewall endpoint security policy
- Selected Windows as the platform
- Selected Windows Firewall as the profile
- Enabled Firewall for Domain, Private, and Public profiles
- Assigned the policy to GRP-Autopilot-Devices
- Verified WINAUTO452 reported policy status as Success
- Added sanitized screenshots

Observed result:

```text
The Windows Firewall policy applied successfully to WINAUTO452 through Microsoft Intune Endpoint security.
```

---

### 06 - BitLocker Encryption Policy

Documented in:

```text
06-endpoint-security/bitlocker-encryption-policy.md
```

Completed work:

- Checked local BitLocker status before policy deployment
- Created a BitLocker disk encryption policy in Intune
- Configured silent BitLocker encryption settings
- Configured recovery password storage settings
- Assigned the policy to GRP-Autopilot-Devices
- Verified WINAUTO452 reported policy status as Success
- Verified local encryption status using manage-bde
- Confirmed the OS drive was fully encrypted and protection was on
- Added sanitized screenshots

Observed result:

```text
BitLocker was enabled successfully on WINAUTO452.
The operating system drive showed Fully Encrypted, 100.0% encrypted, and Protection On.
```

---

### 06 - Attack Surface Reduction Policy

Documented in:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

Completed work:

- Created an Attack Surface Reduction endpoint security policy
- Selected Windows as the platform and Attack Surface Reduction Rules as the profile
- Named the policy ASR-WIN-Audit-Mode-Pilot
- Configured selected ASR rules in Audit mode
- Assigned the policy to GRP-Autopilot-Devices
- Verified WINAUTO452 reported policy assignment status as Success
- Validated ASR rule configuration locally using PowerShell Get-MpPreference
- Added sanitized screenshots

ASR rules configured in Audit mode:

```text
Block Office applications from creating executable content
Block credential stealing from the Windows local security authority subsystem
Block JavaScript or VBScript from launching downloaded executable content
Block executable content from email client and webmail
Block abuse of exploited vulnerable signed drivers
Use advanced protection against ransomware
Block all Office applications from creating child processes
```

Observed result:

```text
The ASR policy deployed successfully to WINAUTO452 in Audit mode.
PowerShell confirmed ASR rule IDs and action values were present on the endpoint.
```

---

### 06 - Windows Security Baseline

Documented in:

```text
06-endpoint-security/windows-security-baseline.md
```

Completed work:

- Created a Windows Security Baseline profile named WIN-Security-Baseline-Pilot
- Reviewed baseline configuration sections
- Assigned the baseline to GRP-Autopilot-Devices
- Monitored initial Pending and Conflict reporting
- Identified Firewall and Defender conflicts with existing dedicated endpoint security policies
- Remediated overlapping settings by setting them to Not configured
- Identified a Device Guard and VBS error (error code 65000)
- Remediated Device Guard and virtualization-based security settings to Not configured
- Synced the device and regenerated the baseline report
- Verified final device assignment status as Success
- Added sanitized screenshots

Observed result:

```text
WIN-Security-Baseline-Pilot applied successfully to WINAUTO452 after conflict and error remediation.
The final baseline device assignment status showed Success.
```

---

### 04 - Windows Basic Compliance Policy

Documented in:

```text
04-compliance-and-conditional-access/windows-basic-compliance-policy.md
```

Completed work:

- Created a Windows compliance policy in Microsoft Intune
- Configured compliance settings including BitLocker, Secure Boot, Code Integrity, Firewall, TPM, Antivirus, Antispyware, and Real-time protection
- Assigned the policy to GRP-Autopilot-Devices
- Triggered a device sync on WINAUTO452
- Verified per-setting compliance status in Intune
- Troubleshot Secure Boot compliance using PowerShell
- Confirmed WINAUTO452 reported as Compliant
- Added sanitized screenshots

Observed result:

```text
WINAUTO452 evaluated the compliance policy and reported as Compliant in Microsoft Intune.
```

---

### 04 - Conditional Access: Compliant Device Policy (Report-Only)

Documented in:

```text
04-compliance-and-conditional-access/conditional-access-compliant-device.md
```

Completed work:

- Created a Conditional Access policy requiring a compliant device for Microsoft 365 access
- Targeted GRP-Pilot-Users and Microsoft 365 / Office 365 cloud apps
- Scoped the policy to the Windows device platform
- Set the policy to Report-only mode for safe testing
- Signed in to a Microsoft 365 app from WINAUTO452
- Verified the sign-in succeeded in Report-only mode
- Reviewed the sign-in log and confirmed the CA policy reported a success result
- Added sanitized screenshots

Observed result:

```text
The Conditional Access compliant device policy evaluated successfully in Report-only mode.
Access was not blocked. The sign-in log confirmed the policy would have been satisfied.
```

---

### 04 - Managed Noncompliant Device Test

Documented in:

```text
04-compliance-and-conditional-access/managed-noncompliant-device-test.md
```

Completed work:

- Confirmed WIN-BYOD-001 initial compliance state
- Created a test compliance policy with an impossible minimum OS version requirement
- Assigned the test policy to GRP-BYOD-Users
- Verified WIN-BYOD-001 became noncompliant in Intune
- Confirmed the Conditional Access Report-only policy captured the noncompliant state
- Verified the sign-in log showed the CA policy would have failed for the noncompliant BYOD device
- Added sanitized screenshots

Observed result:

```text
WIN-BYOD-001 became noncompliant after receiving the test compliance policy.
The Conditional Access Report-only log confirmed the policy would have blocked access
due to the noncompliant device state.
```

---

### 04 - Conditional Access: Enforced Mode Test

Documented in:

```text
04-compliance-and-conditional-access/conditional-access-enforced-mode-test.md
```

Completed work:

- Verified WIN-BYOD-001 noncompliant state before testing
- Created a Conditional Access policy requiring a compliant device in Report-only mode
- Disabled Security Defaults to allow Conditional Access enforcement
- Switched the Conditional Access policy from Report-only to On (enforced mode)
- Attempted to sign in to Microsoft 365 from the noncompliant WIN-BYOD-001 device as user03
- Confirmed access was blocked with a Conditional Access error
- Reviewed the sign-in logs and verified the CA policy blocked the authentication
- Added sanitized screenshots

Observed result:

```text
Access to Microsoft 365 was blocked for user03 on the noncompliant WIN-BYOD-001 device.
The sign-in log confirmed the Conditional Access policy enforced the compliant device requirement
and blocked the sign-in attempt.
```

---

### 07 - Device Sync Remote Actions

Documented in:

```text
07-remote-actions-and-monitoring/device-sync-remote-actions.md
```

Completed work:

- Opened WINAUTO452 from the Intune admin center
- Verified device compliance, ownership, and management state
- Triggered the Sync remote action from the device overview page
- Confirmed the sync initiated notification in Intune
- Verified the device last check-in time updated after sync
- Performed a local sync from Windows Settings
- Confirmed local sync success on the endpoint
- Added sanitized screenshots

Observed result:

```text
The Intune Sync remote action was initiated successfully.
The device last check-in time updated after the remote sync.
Local Windows sync from Settings completed successfully.
```

---

### 07 - Restart, Retire, and Wipe Remote Actions

Documented in:

```text
07-remote-actions-and-monitoring/restart-retire-wipe-actions.md
```

Completed work:

- Opened WINAUTO452 from the Intune admin center
- Located the Restart action under the Remote actions menu
- Triggered Restart on WINAUTO452 and monitored action status from Pending to Complete
- Reviewed the Remove data menu including Retire, Wipe, Fresh start, and Autopilot reset
- Initiated Retire on WINAUTO452 and reviewed the confirmation dialog
- Initiated Wipe on WIN-CORP-001 and reviewed the confirmation dialog
- Verified all action notifications in Intune
- Confirmed final action results from the Device Actions report
- Observed WIN-CORP-001 device page showed Not found after Wipe completed
- Added sanitized screenshots

Devices used:

```text
WINAUTO452 — Restart and Retire actions
WIN-CORP-001 — Wipe action
```

Observed result:

```text
Restart, Retire, and Wipe actions were all initiated and confirmed.
The Device Actions report showed all three actions as Complete.
WIN-CORP-001 was no longer accessible after the Wipe action completed.
```

---

### 07 - Collect Diagnostics Remote Action

Documented in:

```text
07-remote-actions-and-monitoring/collect-diagnostics.md
```

Completed work:

- Opened WINAUTO452 from the Intune admin center
- Selected the Collect diagnostics remote action from the device overview
- Confirmed the diagnostics collection request
- Monitored the action result from the device-level Device action status tab
- Verified Collect diagnostics showed as Complete
- Reviewed tenant device diagnostics settings under Tenant administration
- Confirmed diagnostic ZIP was excluded from GitHub as sensitive data
- Added sanitized screenshots

Observed result:

```text
Collect diagnostics completed successfully for WINAUTO452.
The device-level Device action status confirmed the action as Complete.
Tenant device diagnostics settings were confirmed as enabled.
```

---

### 07 - Device Monitoring and Reports

Documented in:

```text
07-remote-actions-and-monitoring/device-monitoring-and-reports.md
```

Completed work:

- Reviewed the Devices overview dashboard
- Reviewed the Windows devices inventory list
- Opened the WINAUTO452 device overview page and reviewed compliance, ownership, and management state
- Reviewed the device-level Device action status tab
- Navigated to the Devices Monitor report list
- Reviewed the Device Actions monitoring report at the tenant level
- Reviewed the Noncompliant devices report
- Reviewed configuration policy assignment status for a selected Defender Antivirus policy
- Added sanitized screenshots

Reports reviewed:

```text
Devices overview
Windows devices list
Device overview
Device action status
Devices Monitor report list
Device Actions report
Noncompliant devices report
Configuration policy assignment status
```

Observed result:

```text
WINAUTO452 appeared as Intune-managed, corporate-owned, and compliant.
Device action history, noncompliant device reports, and policy assignment status were all validated from Intune monitoring views.
```

---

### 08 - Intune Enrollment Troubleshooting

Documented in:

```text
08-troubleshooting/intune-enrollment-troubleshooting.md
```

Issue observed:

```text
WIN-CORP-001 joined Microsoft Entra ID during OOBE.
The Microsoft Entra device record initially showed MDM: None.
The device was not immediately visible as managed by Intune.
```

Resolution:

```text
Manual MDM enrollment was completed from Windows Settings.
The device appeared in Intune as managed by Intune and compliant.
```

Key learning:

```text
Microsoft Entra joined does not automatically mean Intune managed.
Both identity join state and MDM management state must be validated separately.
```

---

### 08 - Configuration Policy Conflict Troubleshooting

Documented in:

```text
08-troubleshooting/configuration-policy-conflict-troubleshooting.md
```

Issue observed:

```text
The Windows Security Baseline initially reported Conflict and Error states on WINAUTO452.
Firewall and Defender related settings conflicted with existing dedicated endpoint security policies.
Enable Virtualization Based Security showed Error code 65000.
```

Resolution:

```text
Overlapping Firewall and Defender baseline settings were changed to Not configured.
Device Guard and VBS related settings were changed to Not configured.
After device sync, the final baseline assignment status showed Success.
```

Key learning:

```text
Security baselines are broad policy packages and can overlap with dedicated endpoint security policies.
The administrator must decide which policy owns each setting and resolve conflicts intentionally.
```

---

### 08 - Remote Actions Diagnostics Troubleshooting

Documented in:

```text
08-troubleshooting/remote-actions-diagnostics-troubleshooting.md
```

Issue observed:

```text
During the Collect Diagnostics lab, the expected Device diagnostics report path referenced in Microsoft documentation was not visible in the same way in the lab tenant.
```

Resolution:

```text
The action was validated using the device-level Device action status tab.
Tenant diagnostics settings were also reviewed under Tenant administration.
```

Key learning:

```text
Cloud admin portal layouts can vary across tenants and over time.
Validate remote action results using available device-level and tenant-level evidence when a specific report view is not visible.
```

---

### 08 - Troubleshooting Summary

Documented in:

```text
08-troubleshooting/troubleshooting-summary.md
```

This file summarizes all real troubleshooting scenarios documented during the project, including the common troubleshooting pattern used across all labs, evidence handling rules, and privacy notes.

---

## Completed modern endpoint deployment flow

The completed labs demonstrate this full modern endpoint management chain:

```text
Microsoft Entra users and groups
-> Intune enrollment
-> Windows OOBE enrollment
-> Windows Autopilot registration and provisioning
-> Windows BYOD enrollment
-> Android BYOD work profile enrollment
-> Microsoft Store app deployment
-> Win32 app deployment
-> Microsoft 365 Apps deployment
-> Android Managed Google Play app deployment
-> Configuration profiles applied
-> Corporate wallpaper deployed
-> USB storage restriction validated
-> Endpoint security policies applied
-> Defender Antivirus, Firewall, and BitLocker validated
-> Attack Surface Reduction Rules deployed in Audit mode
-> Windows Security Baseline deployed and troubleshot to Success
-> Windows compliance policy deployed and evaluated
-> Conditional Access report-only mode tested
-> Managed noncompliant device behaviour validated
-> Conditional Access enforced mode tested and access blocked
-> Device sync remote action executed and validated
-> Restart, Retire, and Wipe remote actions executed and confirmed
-> Collect diagnostics remote action completed
-> Intune monitoring reports reviewed
-> Real troubleshooting case studies documented
```

This creates a strong real-world portfolio scenario for MD-102 preparation.

---

## Skills this project demonstrates

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
- Conditional Access report-only mode testing
- Conditional Access enforced mode testing and validation
- Noncompliant device behaviour validation
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
- Post-Autopilot app deployment validation
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
- Intune troubleshooting documentation
- Real-world troubleshooting case study writing

---

## How to use this repository

Each completed lab document follows this standard format:

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

Some files may use slight variations of this structure based on the lab type. Troubleshooting files use a case study format instead.

---

## Screenshot storage

Sanitized screenshots are stored under:

```text
screenshots/sanitized/
```

Folders:

```text
screenshots/sanitized/identity-and-groups/
screenshots/sanitized/device-enrollment/
screenshots/sanitized/configuration-profiles/
screenshots/sanitized/application-deployment/
screenshots/sanitized/compliance-and-conditional-access/
screenshots/sanitized/endpoint-security/
screenshots/sanitized/remote-actions-and-monitoring/
```

---

## Privacy and security

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
- IMEI numbers
- Phone numbers
- Diagnostic ZIP packages
- Unsanitized screenshots
- Production company data

All screenshots must be sanitized before uploading to GitHub.

---

## Notes

This project is for learning, portfolio building, and MD-102 preparation.

The environment, company name, users, devices, and screenshots are fictional, test-only, or sanitized.

The one remaining in-progress item is:

```text
02-device-enrollment/ios-byod-enrollment.md
```

Admin prerequisites for iOS BYOD enrollment are completed. The physical device enrollment step is pending hardware availability.
