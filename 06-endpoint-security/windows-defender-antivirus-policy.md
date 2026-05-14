# Microsoft Defender Antivirus Policy with Intune

## Lab status

**Status:** Completed  
**Lab category:** Endpoint security  
**Platform:** Windows  
**Management platform:** Microsoft Intune  
**Policy area:** Endpoint security  
**Policy type:** Antivirus  
**Profile:** Microsoft Defender Antivirus  
**Assignment group:** GRP-Autopilot-Devices  
**Validation device:** WINAUTO452  
**Enrollment method:** Windows Autopilot user-driven enrollment  
**Final result:** Microsoft Defender Antivirus policy applied successfully  

---

## Lab objective

The objective of this lab is to create, configure, assign, and validate a Microsoft Defender Antivirus policy from the Microsoft Intune admin center.

This lab validates that:

- Microsoft Intune can create Defender Antivirus endpoint security policies.
- Defender Antivirus settings can be configured centrally.
- A Defender Antivirus policy can be assigned to a Windows Autopilot device group.
- An Autopilot-enrolled corporate Windows device can receive the policy.
- Intune policy reporting can confirm successful policy application.

---

## Why this lab matters

Microsoft Defender Antivirus is built into Windows and can be managed through Intune Endpoint security policies.

In real organizations, administrators use Defender Antivirus policies to enforce baseline antivirus protection across corporate devices.

This lab proves that an Autopilot-enrolled Windows device can receive endpoint security settings after enrollment and report successful policy application back to Intune.

Simple flow:

```text
Autopilot device enrolls into Intune
-> Endpoint security policy is created
-> Policy is assigned to corporate device group
-> Device syncs with Intune
-> Defender Antivirus settings apply
-> Intune reports Success
```

---

## Lab environment

| Item | Value |
|---|---|
| Tenant | HOMELAB |
| Management platform | Microsoft Intune |
| Policy area | Endpoint security |
| Policy type | Antivirus |
| Platform | Windows |
| Profile | Microsoft Defender Antivirus |
| Assignment group | GRP-Autopilot-Devices |
| Validation device | WINAUTO452 |
| Device ownership | Corporate |
| Enrollment method | Windows Autopilot user-driven enrollment |
| Primary user | user01 |
| Final policy status | Success |

---

## Prerequisites

Before starting this lab, the following were required:

- Microsoft Intune tenant available.
- Windows Autopilot device enrolled.
- `WINAUTO452` available in Intune.
- `WINAUTO452` included in `GRP-Autopilot-Devices`.
- Device able to sync with Intune.
- Endpoint security policy permissions available in Intune.
- Sanitized screenshots prepared for GitHub documentation.

---

## Policy design

The policy was assigned to the Autopilot device group instead of an individual user.

```text
GRP-Autopilot-Devices
-> WINAUTO452
-> Microsoft Intune managed
-> Defender Antivirus policy applied
-> Device status reported Success
```

This is a realistic enterprise approach because endpoint security policies are commonly targeted to device groups that represent corporate-managed devices.

### Policy details

| Setting | Value |
|---|---|
| Policy name | WIN-Autopilot-Defender-Antivirus-Policy |
| Description | Defender Antivirus policy for MD-102 Intune lab endpoint security testing on Windows Autopilot devices. |
| Platform | Windows |
| Profile | Microsoft Defender Antivirus |
| Assignment | GRP-Autopilot-Devices |
| Target device | WINAUTO452 |
| Assignment result | Success |

---

## Configuration flow

```text
Confirm Autopilot device group membership
-> Create Defender Antivirus endpoint security policy
-> Configure policy basics
-> Configure Defender Antivirus settings
-> Assign policy to GRP-Autopilot-Devices
-> Create policy
-> Sync WINAUTO452
-> Validate device status in Intune
```

---

## Steps performed

### Step 1 - Confirmed Autopilot device group membership

The policy was designed to target the Autopilot device group.

The group `GRP-Autopilot-Devices` contained the device:

```text
WINAUTO452
```

![Autopilot device group member](../screenshots/sanitized/endpoint-security/defender-autopilot-device-group-member-sanitized.png)

---

### Step 2 - Created Microsoft Defender Antivirus profile

The policy was created from the Intune admin center.

Navigation path:

```text
Microsoft Intune admin center
-> Endpoint security
-> Antivirus
-> Create Policy
```

Profile selection:

| Field | Value |
|---|---|
| Platform | Windows |
| Profile | Microsoft Defender Antivirus |

![Defender Antivirus profile creation](../screenshots/sanitized/endpoint-security/defender-antivirus-profile-create-sanitized.png)

---

### Step 3 - Configured policy basics

The policy was named for the Autopilot device scenario.

| Field | Value |
|---|---|
| Name | WIN-Autopilot-Defender-Antivirus-Policy |
| Description | Defender Antivirus policy for MD-102 Intune lab endpoint security testing on Windows Autopilot devices. |

![Defender Antivirus policy basics](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-basics-sanitized.png)

---

### Step 4 - Configured Defender Antivirus settings

The following core Defender Antivirus settings were configured for the lab.

| Defender setting | Configuration |
|---|---|
| Allow Archive Scanning | Allowed |
| Allow Behavior Monitoring | Allowed |
| Allow Cloud Protection | Allowed |
| Allow Email Scanning | Allowed |
| Allow Full Scan on Removable Drive Scanning | Allowed |
| Allow Realtime Monitoring | Allowed |
| Allow Scanning Network Files | Allowed |
| Allow Script Scanning | Allowed |
| Check for Signatures Before Running Scan | Enabled |
| Cloud Block Level | High |
| Cloud Extended Timeout | 50 |
| Days to Retain Cleaned Malware | 30 |
| Enable Network Protection | Enabled in audit mode |
| PUA Protection | Enabled |
| Real Time Scan Direction | Monitor all files |
| Submit Samples Consent | Send safe samples automatically |
| Allow On Access Protection | Allowed |

Threat severity remediation actions were also configured.

| Threat severity | Remediation action |
|---|---|
| Severe | Quarantine |
| High | Quarantine |
| Moderate | Quarantine |
| Low | Quarantine |

Exclusions were intentionally left blank.

| Exclusion type | Configuration |
|---|---|
| Excluded extensions | Not configured |
| Excluded paths | Not configured |
| Excluded processes | Not configured |

![Defender Antivirus policy settings](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-settings-sanitized.png)

---

### Step 5 - Assigned policy to Autopilot device group

The policy was assigned to the Autopilot device group.

| Assignment item | Value |
|---|---|
| Included group | GRP-Autopilot-Devices |
| Group members | 1 device |
| Target type | Include |
| Excluded groups | None |

![Defender Antivirus policy assignment](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-assignment-autopilot-devices-sanitized.png)

---

### Step 6 - Confirmed policy creation

After creation, the policy appeared under the Antivirus policy list in Endpoint security.

![Defender Antivirus policy list](../screenshots/sanitized/endpoint-security/defender-antivirus-policy-list-sanitized.png)

---

### Step 7 - Validated device status

The policy status report showed that the Defender Antivirus policy successfully applied to `WINAUTO452`.

| Result item | Value |
|---|---|
| Device name | WINAUTO452 |
| Assignment status | Success |
| Pending | 0 |
| Success | 1 |
| Error | 0 |
| Conflict | 0 |
| Total | 1 |

![Defender Antivirus device status success](../screenshots/sanitized/endpoint-security/defender-antivirus-device-status-winauto452-succeeded-sanitized.png)

---

## Validation

### Policy creation validation

Validation confirmed that:

- The Antivirus endpoint security blade was used.
- The platform was set to Windows.
- The profile was set to Microsoft Defender Antivirus.
- The policy appeared in the Antivirus policy list.

---

### Settings validation

Validation confirmed that:

- Core Defender Antivirus settings were configured.
- Cloud protection was enabled.
- PUA protection was enabled.
- Network protection was configured in audit mode.
- Threat remediation actions were configured.
- Exclusions were intentionally left blank.

---

### Assignment validation

Validation confirmed that:

- The policy was assigned to `GRP-Autopilot-Devices`.
- `WINAUTO452` was included in the target device group.

---

### Device status validation

Validation confirmed that:

- `WINAUTO452` received the policy.
- Intune reported the device assignment status as Success.
- There were no error, conflict, or pending results for the target device.

---

## Final test result

| Validation item | Status |
|---|---|
| Microsoft Defender Antivirus policy created | Completed |
| Windows platform selected | Completed |
| Microsoft Defender Antivirus profile selected | Completed |
| Core Defender Antivirus settings configured | Completed |
| PUA protection enabled | Completed |
| Threat remediation set to quarantine | Completed |
| Policy assigned to GRP-Autopilot-Devices | Completed |
| WINAUTO452 received the policy | Completed |
| Intune device status reported Success | Completed |
| Screenshots captured and uploaded | Completed |
| Final lab result | Completed |

Observed final result:

```text
The Defender Antivirus policy applied successfully to WINAUTO452 through Microsoft Intune Endpoint security.
```

---

## Screenshots captured

Screenshots are stored in:

```text
screenshots/sanitized/endpoint-security/
```

| Screenshot | Purpose |
|---|---|
| `defender-autopilot-device-group-member-sanitized.png` | Shows WINAUTO452 as a member of GRP-Autopilot-Devices |
| `defender-antivirus-profile-create-sanitized.png` | Shows the Microsoft Defender Antivirus profile selection |
| `defender-antivirus-policy-basics-sanitized.png` | Shows the policy name and description |
| `defender-antivirus-policy-settings-sanitized.png` | Shows the configured Defender Antivirus settings |
| `defender-antivirus-policy-assignment-autopilot-devices-sanitized.png` | Shows assignment to GRP-Autopilot-Devices |
| `defender-antivirus-policy-list-sanitized.png` | Shows the created policy in the Antivirus policy list |
| `defender-antivirus-device-status-winauto452-succeeded-sanitized.png` | Shows WINAUTO452 reporting Success |

---

## Troubleshooting notes

### Policy remains pending

If the policy remains pending:

1. Confirm the target device is in the assigned group.
2. Sync the device from Windows Settings.
3. Sync the device from Intune remote actions.
4. Wait for Intune reporting to refresh.
5. Regenerate the policy report.
6. Check for conflicts with other antivirus or endpoint security policies.

---

### Policy reports conflict

If the policy reports conflict:

1. Check whether another antivirus policy configures the same settings.
2. Check whether a security baseline configures overlapping Defender settings.
3. Review endpoint security policy assignments.
4. Remove duplicate settings from one policy if needed.
5. Sync the device and refresh reporting.

---

### Device does not appear in the report

If the target device does not appear in the report:

1. Confirm the device is enrolled in Intune.
2. Confirm the device is included in `GRP-Autopilot-Devices`.
3. Confirm the policy assignment includes the correct group.
4. Wait for policy reporting to update.
5. Sync the device manually.

---

## Enterprise reflection

In production, Defender Antivirus policies should be planned carefully before broad deployment.

Recommended real-world practices:

- Start with a pilot device group.
- Avoid unnecessary antivirus exclusions.
- Use Intune reporting to check Success, Error, Conflict, and Pending states.
- Use Microsoft Defender for Endpoint integration for stronger threat visibility when available.
- Document policy settings and assignment scope clearly.
- Avoid changing too many endpoint security settings at once.

A safer rollout model is:

```text
Pilot devices
-> IT validation
-> Department pilot
-> Production rollout
```

This lab follows the same principle by assigning the policy to:

```text
GRP-Autopilot-Devices
```

---

## Security and privacy notes

This is a public learning repository.

Do not upload screenshots that show:

- Full user email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Internal IP addresses
- MAC addresses
- Passwords
- MFA prompts
- Unsanitized tenant information
- Production company data

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant/domain name
- Full user principal names
- Device identifiers
- Serial numbers
- Any private endpoint details

---

## Related labs

| Lab file | Relationship |
|---|---|
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Provides the Autopilot-enrolled corporate device WINAUTO452 |
| `03-configuration-profiles/windows-device-restrictions-profile.md` | Also targets WINAUTO452 through device policy assignment |
| `06-endpoint-security/windows-firewall-policy.md` | Next endpoint security policy in the sequence |
| `06-endpoint-security/bitlocker-encryption-policy.md` | Disk encryption endpoint security policy |
| `06-endpoint-security/attack-surface-reduction-policy.md` | Planned advanced endpoint security lab |
| `06-endpoint-security/windows-security-baseline.md` | Planned security baseline lab |

---

## Key learning outcomes

This lab demonstrated how to:

- Create a Microsoft Defender Antivirus policy in Intune.
- Use Endpoint security for antivirus policy management.
- Configure core Defender Antivirus settings.
- Enable PUA protection.
- Configure remediation actions for threat severities.
- Assign endpoint security policies to a device group.
- Validate policy success from Intune reporting.
- Use an Autopilot-enrolled device for endpoint security testing.

---

## Lab conclusion

The Microsoft Defender Antivirus policy lab was completed successfully.

Final result:

```text
Microsoft Defender Antivirus policy was created in Intune.
Core Defender Antivirus settings were configured.
The policy was assigned to GRP-Autopilot-Devices.
WINAUTO452 received the policy successfully.
Intune reported device status as Success.
```

This confirms that the Autopilot-enrolled Windows device is receiving endpoint security policies from Microsoft Intune.
