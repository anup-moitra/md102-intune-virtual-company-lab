# Windows Firewall Policy with Intune

This lab documents the creation and validation of a **Windows Firewall endpoint security policy** in Microsoft Intune for the MD-102 Intune virtual company project.

The policy was assigned to the Autopilot device group and successfully applied to the Autopilot-enrolled Windows device `WINAUTO452`.

## Objective

Create, assign, and validate a Windows Firewall policy using Microsoft Intune Endpoint security.

This lab validates that:

- Microsoft Intune can configure Windows Firewall settings from the Endpoint security node.
- Firewall protection can be enabled for Domain, Private, and Public network profiles.
- The policy can be assigned to the Autopilot device group.
- The Autopilot device `WINAUTO452` can receive and report the policy as successful.
- Intune policy reporting can confirm policy deployment status.

## Lab Context

This lab is part of the MD-102 Intune virtual company project.

The virtual company uses Microsoft Intune to manage corporate Windows devices and apply endpoint security settings after Windows Autopilot enrollment.

This lab continues the endpoint security sequence after the Microsoft Defender Antivirus policy lab.

Simple security flow:

```text
Windows Autopilot device enrolled
-> Device becomes Intune managed
-> Endpoint security Firewall policy is created
-> Policy is assigned to GRP-Autopilot-Devices
-> WINAUTO452 syncs with Intune
-> Firewall policy applies successfully
-> Intune reports Success
```

## Why This Lab Matters

Windows Firewall helps reduce the attack surface of a Windows device by controlling inbound and outbound network traffic.

In a real environment, endpoint administrators usually enable firewall protection across managed corporate devices to help block unauthorized network connections and reduce exposure to network-based threats.

This lab demonstrates a beginner-friendly firewall baseline before moving into more advanced endpoint security controls such as BitLocker, Attack Surface Reduction, and Windows Security Baselines.

## Lab Environment

| Item | Value |
|---|---|
| Tenant type | Microsoft 365 / Intune lab tenant |
| Management platform | Microsoft Intune |
| Device enrollment method | Windows Autopilot user-driven enrollment |
| Validation device | WINAUTO452 |
| Device ownership | Corporate |
| Primary user | user01 |
| Assignment group | GRP-Autopilot-Devices |
| Policy area | Endpoint security |
| Policy type | Firewall |
| Profile | Windows Firewall |
| Platform | Windows |

## Policy Details

| Setting | Value |
|---|---|
| Policy name | WIN-Autopilot-Windows-Firewall-Policy |
| Description | Windows Firewall endpoint security policy for MD-102 Intune lab testing on Windows Autopilot devices. |
| Platform | Windows |
| Profile | Windows Firewall |
| Assignment | GRP-Autopilot-Devices |
| Target device | WINAUTO452 |
| Policy result | Success |

## Assignment Design

The policy was assigned to the device group:

```text
GRP-Autopilot-Devices
```

This group contained the Autopilot-enrolled corporate device:

```text
WINAUTO452
```

This assignment model is better for this lab than assigning to a user group because the policy follows the device rather than any device where the user signs in.

Simple comparison:

| Assignment type | Behavior |
|---|---|
| User group assignment | Policy follows the user across devices |
| Device group assignment | Policy targets specific devices directly |

For this lab, the device group approach is cleaner because Defender Antivirus, Windows Firewall, and BitLocker are endpoint security controls intended for the managed Autopilot device.

## Firewall Settings Configured

The policy enabled Windows Firewall for the main Windows network profiles.

| Firewall setting | Configuration |
|---|---|
| Enable Domain Network Firewall | True |
| Enable Private Network Firewall | True |
| Enable Public Network Firewall | True |
| Default inbound action for Domain profile | Block |
| Default inbound action for Private profile | Block |
| Default inbound action for Public profile | Block |
| Default outbound action | Allow |
| Shielded mode | False |
| Log file path | `%systemroot%\system32\LogFiles\Firewall\pfirewall.log` |
| Log max file size | 1024 |

> [!NOTE]
> This lab focused on enabling and validating Windows Firewall profile protection. Custom firewall rules were not created in this lab.

## Steps Performed

### 1. Opened Endpoint Security Firewall

The Microsoft Intune admin center was opened.

Navigation path:

```text
Intune admin center
-> Endpoint security
-> Firewall
```

The Firewall page showed the Windows Firewall policy area and the option to create a policy.

### 2. Created a New Firewall Policy

The following profile was selected:

| Option | Value |
|---|---|
| Platform | Windows |
| Profile | Windows Firewall |

The following options were not selected:

| Option | Reason |
|---|---|
| Windows Firewall Rules | Used for specific inbound/outbound firewall rules, not needed for this baseline lab |
| Windows Hyper-V Firewall Rules | Used for Hyper-V container-specific firewall scenarios |

### 3. Entered Policy Basics

The policy was named:

```text
WIN-Autopilot-Windows-Firewall-Policy
```

Description used:

```text
Windows Firewall endpoint security policy for MD-102 Intune lab testing on Windows Autopilot devices.
```

### 4. Configured Firewall Settings

The policy was configured to enable Windows Firewall across the main network profiles.

Main configured values:

```text
Enable Domain Network Firewall: True
Enable Private Network Firewall: True
Enable Public Network Firewall: True
```

The default inbound action was left as **Block**, while outbound traffic was left as **Allow**. This is a safe beginner baseline because it keeps normal outbound connectivity working while keeping unsolicited inbound traffic blocked.

Shielded mode was left disabled because it can be too restrictive for a beginner lab and may impact connectivity.

### 5. Left Scope Tags as Default

The default scope tag was used.

No custom scope tag was required for this lab.

### 6. Assigned the Policy

The policy was assigned to:

```text
GRP-Autopilot-Devices
```

This group contained:

```text
WINAUTO452
```

### 7. Reviewed and Created the Policy

The policy was reviewed and created in Intune.

The Review + create screenshot was not required for this lab because the policy list and device status screenshots provide stronger final evidence.

### 8. Verified Policy in Firewall Policy List

After creation, the policy appeared under:

```text
Endpoint security
-> Firewall
-> Firewall policies
```

The policy list showed the firewall policy as assigned.

### 9. Verified Device Status in Intune

The policy status report showed the following result:

| Status | Count |
|---|---:|
| Pending | 0 |
| Success | 1 |
| Error | 0 |
| Conflict | 0 |
| Total | 1 |

The device row showed:

```text
WINAUTO452 = Success
```

## Test Result

| Test item | Result |
|---|---|
| Firewall policy created | Successful |
| Platform selected as Windows | Successful |
| Windows Firewall profile selected | Successful |
| Domain network firewall enabled | Successful |
| Private network firewall enabled | Successful |
| Public network firewall enabled | Successful |
| Policy assigned to GRP-Autopilot-Devices | Successful |
| Target device | WINAUTO452 |
| Intune policy status | Success |
| Lab result | Completed |

## What This Proves

This lab proves that Microsoft Intune can deploy Windows Firewall settings through Endpoint security policies to an Autopilot-enrolled corporate Windows device.

Simple explanation:

```text
Admin created Windows Firewall policy in Intune
-> Policy assigned to GRP-Autopilot-Devices
-> WINAUTO452 received the policy
-> Intune reported policy status as Success
-> Firewall baseline deployment was validated
```

This confirms that `WINAUTO452` is now managed by Intune and receiving endpoint security policies after Autopilot enrollment.

## Screenshots

> [!NOTE]
> Screenshots must be sanitized before upload. Hide tenant names, full email addresses, admin account details, device IDs, serial numbers, object IDs, IP addresses, and any sensitive information.

### Create Firewall profile

![Create Windows Firewall profile](../screenshots/sanitized/endpoint-security/firewall-profile-create-sanitized.png)

### Firewall policy basics

![Firewall policy basics](../screenshots/sanitized/endpoint-security/firewall-policy-basics-sanitized.png)

### Firewall policy configuration settings

![Firewall policy settings](../screenshots/sanitized/endpoint-security/firewall-policy-settings-sanitized.png)

### Firewall policy assignment to Autopilot devices

![Firewall policy assignment to Autopilot devices](../screenshots/sanitized/endpoint-security/firewall-policy-assignment-autopilot-devices-sanitized.png)

### Firewall policy list

![Firewall policy list](../screenshots/sanitized/endpoint-security/firewall-policy-list-sanitized.png)

### Firewall device status succeeded

![Firewall device status WINAUTO452 succeeded](../screenshots/sanitized/endpoint-security/firewall-device-status-winauto452-succeeded-sanitized.png)

## Screenshot Folder Path

Screenshots for this lab are stored in:

```text
screenshots/sanitized/endpoint-security/
```

Screenshot filenames used:

```text
firewall-profile-create-sanitized.png
firewall-policy-basics-sanitized.png
firewall-policy-settings-sanitized.png
firewall-policy-assignment-autopilot-devices-sanitized.png
firewall-policy-list-sanitized.png
firewall-device-status-winauto452-succeeded-sanitized.png
```

## Troubleshooting Notes

### Device status shows Pending

If the device status shows **Pending**, wait for Intune check-in or manually sync the device.

Manual sync path on Windows:

```text
Settings
-> Accounts
-> Access work or school
-> Connected work or school account
-> Info
-> Sync
```

You can also trigger sync from Intune:

```text
Intune admin center
-> Devices
-> Windows
-> WINAUTO452
-> Sync
```

### Policy does not apply

If the policy does not apply, check:

1. The policy is assigned to the correct group.
2. `WINAUTO452` is a member of `GRP-Autopilot-Devices`.
3. The device is enrolled in Microsoft Intune.
4. The device has checked in recently.
5. The device has internet connectivity.
6. There are no conflicting firewall policies.

### Firewall policy conflicts

If a conflict appears, check whether another Intune policy, security baseline, or local policy is configuring the same Windows Firewall settings.

## Security Notes

This lab enabled Windows Firewall across Domain, Private, and Public profiles.

For production environments:

- Test firewall changes with a pilot device group before broad deployment.
- Avoid blocking outbound traffic unless there is a tested business requirement.
- Avoid enabling shielded mode without validating remote management and network access.
- Create custom firewall rules only after confirming the required ports, protocols, applications, and network profiles.

## Current Lab Status

Completed:

- Windows Firewall endpoint security policy created
- Windows platform selected
- Windows Firewall profile selected
- Domain network firewall enabled
- Private network firewall enabled
- Public network firewall enabled
- Policy assigned to `GRP-Autopilot-Devices`
- Policy appeared in the Firewall policy list
- `WINAUTO452` reported policy status as Success
- Screenshots uploaded to GitHub path `screenshots/sanitized/endpoint-security/`

## Next Step

Continue to the next endpoint security lab:

```text
06-endpoint-security/bitlocker-encryption-policy.md
```

After BitLocker, continue to:

```text
06-endpoint-security/attack-surface-reduction-policy.md
```

## References

- Microsoft Learn: Firewall policy for endpoint security in Intune
- Microsoft Learn: Firewall policy settings for endpoint security in Intune
