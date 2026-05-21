# MD-102 Intune Virtual Company Lab

A hands-on Microsoft Intune and MD-102 exam preparation project simulating a real small-business endpoint management environment from the ground up.

---

## Company Scenario

The lab company is **Contoso Startup Lab** — a small organization with a mixed device fleet managed entirely through Microsoft Entra ID and Microsoft Intune.

| Category | Details |
|---|---|
| Corporate devices | Windows laptops (OOBE and Autopilot enrolled) |
| Personal devices | Windows BYOD, Android BYOD (work profile) |
| Planned | iOS/iPadOS BYOD (admin prerequisites complete, hardware pending) |
| Identity | Microsoft Entra ID users, security groups, license assignment |
| Management | Microsoft Intune — configuration, security, compliance, apps |

Full scenario: [`00-project-overview/company-scenario.md`](00-project-overview/company-scenario.md)

---

## Lab Coverage

| # | Section | Topics |
|---|---|---|
| 00 | Project Overview | Scenario, device inventory, roadmap |
| 01 | Identity and Groups | Users, groups, licensing, targeting |
| 02 | Device Enrollment | OOBE, Autopilot, Windows BYOD, Android BYOD |
| 03 | Configuration Profiles | Settings catalog, ADMX-backed, device restrictions |
| 04 | Compliance and Conditional Access | Compliance policy, CA report-only, CA enforced |
| 05 | Application Deployment | Store apps, Win32, Microsoft 365 Apps, Android apps |
| 06 | Endpoint Security | Defender AV, Firewall, BitLocker, ASR, Security Baseline |
| 07 | Remote Actions and Monitoring | Sync, Restart, Retire, Wipe, Diagnostics, Reports |
| 08 | Troubleshooting | Enrollment, policy conflict, remote action case studies |

---

## Project Status

| Lab | Status |
|---|---|
| Project overview and documentation | Completed |
| Identity and groups | Completed |
| Windows OOBE enrollment | Completed |
| Windows Autopilot user-driven enrollment | Completed |
| Windows BYOD enrollment | Completed |
| Android BYOD work profile enrollment | Completed |
| iOS BYOD enrollment | In Progress — admin prerequisites done, physical device pending |
| Windows configuration profiles | Completed |
| Microsoft Store app deployment | Completed |
| Win32 app deployment (7-Zip) | Completed |
| Microsoft 365 Apps deployment | Completed |
| Android Managed Google Play app deployment | Completed |
| Defender Antivirus policy | Completed |
| Windows Firewall policy | Completed |
| BitLocker encryption policy | Completed |
| Attack Surface Reduction policy | Completed |
| Windows Security Baseline | Completed |
| Windows compliance policy | Completed |
| Conditional Access (report-only and enforced) | Completed |
| Remote actions (Sync, Restart, Retire, Wipe) | Completed |
| Collect diagnostics | Completed |
| Device monitoring and reports | Completed |
| Troubleshooting case studies | Completed |

---

## End-to-End Management Flow

The completed labs cover the full modern endpoint management chain:

```
Entra ID users and groups
  → License assignment
  → Device enrollment (OOBE / Autopilot / BYOD / Android)
  → Configuration profiles
  → Application deployment
  → Endpoint security policies (AV, Firewall, BitLocker, ASR, Baseline)
  → Compliance policy evaluation
  → Conditional Access (report-only → enforced)
  → Remote actions (Sync, Restart, Retire, Wipe, Diagnostics)
  → Monitoring and reports
  → Troubleshooting case studies
```

---

## Repository Structure

```
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
│   └── ios-byod-enrollment.md                 [in progress]
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

---

## Skills Demonstrated

**Identity and Enrollment** — Entra ID user and group management, license assignment, Windows OOBE enrollment, Windows Autopilot (hardware hash import, deployment profile, user-driven provisioning), Windows BYOD, Android Enterprise work profile enrollment, personal vs. corporate ownership validation.

**Configuration and Apps** — Settings catalog profiles, ADMX-backed policy, PowerShell platform scripts, corporate wallpaper deployment, USB storage restriction, Microsoft Store (new), Win32 app packaging with `.intunewin`, detection rule configuration, Microsoft 365 Apps deployment, Managed Google Play app approval and deployment.

**Security and Compliance** — Defender Antivirus, Windows Firewall, BitLocker (with local encryption validation), Attack Surface Reduction in Audit mode (PowerShell validation), Windows Security Baseline deployment and conflict remediation, Device Guard and VBS error investigation.

**Conditional Access** — Compliance policy creation, CA policy in report-only mode, compliant and noncompliant device behavior testing, CA enforced mode blocking validation.

**Remote Actions and Monitoring** — Device Sync, Restart, Retire, Wipe, Collect Diagnostics, Device Actions report, Noncompliant Devices report, configuration policy assignment status review.

**Troubleshooting** — MDM enrollment status investigation, policy conflict identification and resolution, remote action and diagnostics behavior case studies, real-evidence documentation.

---

## Lab Document Format

Each lab document follows a consistent structure:

```
Lab status / Lab objective / Why this lab matters
Lab environment / Prerequisites / Configuration flow
Steps performed / Validation / Final test result
Screenshots captured / Troubleshooting notes
Enterprise reflection / Security and privacy notes
Related labs / Key learning outcomes / Lab conclusion
```

---

## Screenshots

Sanitized screenshots are stored under `screenshots/sanitized/` and organized by lab area. All screenshots have sensitive information removed or blurred before upload, including tenant IDs, email addresses, device IDs, serial numbers, hardware hashes, BitLocker recovery keys, IP addresses, IMEI numbers, and diagnostic package contents.

---

## Notes

This project is for learning, portfolio building, and MD-102 exam preparation. The environment, company name, users, devices, and screenshots are all fictional, test-only, or sanitized.
