# Windows Firewall Policy with Intune

This file documents the Windows Firewall endpoint security policy lab for the MD-102 Intune virtual company project.

---

## Status

Planned

---

## Objective

Create and test a Windows Firewall policy using Microsoft Intune Endpoint security.

This lab will validate that:

- Microsoft Intune can configure Microsoft Defender Firewall settings.
- Firewall can be enabled for Domain, Private, and Public network profiles.
- Firewall default inbound and outbound behavior can be configured.
- The policy can be assigned to a pilot group.
- The managed Windows device can receive the firewall policy.
- Intune can report firewall policy deployment status.
- The local Windows Security app can confirm firewall protection is enabled.

---

## Lab Context

This lab continues after:

```text
06-endpoint-security/windows-defender-antivirus-policy.md
```

Defender Antivirus protects against malware. Windows Firewall helps protect the device from unwanted network traffic.

Together, these two labs demonstrate basic endpoint protection management with Intune.

---

## Why This Lab Matters

Windows Firewall is important because devices connect to different networks, such as home Wi-Fi, office networks, public Wi-Fi, and VPN networks.

In real environments, administrators use firewall policies to make sure Windows Firewall stays enabled and follows company security requirements.

Simple flow:

```text
Admin creates firewall policy in Intune
-> Policy is assigned to pilot users or devices
-> Windows device syncs with Intune
-> Firewall settings apply
-> Intune reports policy status
-> Windows Security confirms firewall is on
```

---

## Lab Environment

| Item | Value |
|---|---|
| Test device | `WIN-CORP-001` or `WINAUTO452` |
| Operating system | Windows 11 |
| Management platform | Microsoft Intune |
| Identity platform | Microsoft Entra ID |
| Test user | `user01` |
| Assignment group | `GRP-Pilot-Users` |
| Policy area | Endpoint security |
| Policy type | Firewall |
| Profile | Windows Firewall |
| Screenshot folder | `screenshots/sanitized/endpoint-security/` |

---

## Policy Plan

| Setting | Planned Value |
|---|---|
| Policy name | `WIN-CORP-Windows-Firewall-Policy` |
| Platform | Windows |
| Profile | Windows Firewall |
| Assignment | `GRP-Pilot-Users` |
| Validation device | `WIN-CORP-001` or `WINAUTO452` |
| Expected result | Policy applies successfully |

---

## Recommended Firewall Settings

Use simple baseline firewall settings for this lab.

| Firewall setting | Recommended lab configuration |
|---|---|
| Enable Domain Network Firewall | True / Enabled |
| Enable Private Network Firewall | True / Enabled |
| Enable Public Network Firewall | True / Enabled |
| Default inbound action | Block |
| Default outbound action | Allow |
| Log dropped packets | Enabled, if available |
| Log successful connections | Not configured or disabled |
| Log file path | `%systemroot%\system32\LogFiles\Firewall\pfirewall.log` |
| Log max file size | 1024 KB or default |

> [!NOTE]
> This beginner lab focuses on enabling firewall protection. Advanced inbound/outbound firewall rules can be tested later.

---

## Hands-On Steps

### Step 1: Open Endpoint Security Firewall

Go to:

```text
Intune admin center
-> Endpoint security
-> Firewall
```

### Step 2: Create a New Firewall Policy

Select:

```text
Create Policy
```

Use:

| Option | Value |
|---|---|
| Platform | Windows |
| Profile | Windows Firewall |

### Step 3: Configure Basics

Use:

```text
Name: WIN-CORP-Windows-Firewall-Policy
Description: Windows Firewall endpoint security policy for MD-102 Intune lab.
```

### Step 4: Configure Firewall Settings

Configure the recommended firewall settings from the table above.

### Step 5: Assign the Policy

Assign to:

```text
GRP-Pilot-Users
```

> [!NOTE]
> If the policy applies to more than one device because `user01` signs in on multiple devices, document it as a user-targeting behavior. For stricter production-style testing, use a device group.

### Step 6: Create the Policy

Review and create the policy.

### Step 7: Sync the Device

Sync from the endpoint or from Intune.

Endpoint path:

```text
Settings
-> Accounts
-> Access work or school
-> Connected work account
-> Info
-> Sync
```

Intune path:

```text
Intune admin center
-> Devices
-> Windows
-> Select device
-> Sync
```

### Step 8: Verify Policy Status in Intune

Check:

```text
Endpoint security
-> Firewall
-> WIN-CORP-Windows-Firewall-Policy
-> Device status
```

Expected result:

```text
Succeeded
```

### Step 9: Verify Locally on Windows

Open:

```text
Windows Security
-> Firewall & network protection
```

Confirm firewall is enabled for:

```text
Domain network
Private network
Public network
```

---

## Test Result

| Test item | Result |
|---|---|
| Firewall policy created | Pending |
| Firewall settings configured | Pending |
| Policy assigned to pilot group | Pending |
| Device sync completed | Pending |
| Intune policy status checked | Pending |
| Windows Security firewall status verified | Pending |
| Screenshots captured | Pending |
| Final lab result | Pending |

---

## Screenshots

Screenshots should be stored in:

```text
screenshots/sanitized/endpoint-security/
```

Recommended screenshots:

```text
firewall-policy-list-sanitized.png
firewall-policy-basics-sanitized.png
firewall-policy-settings-sanitized.png
firewall-policy-assignment-sanitized.png
firewall-device-status-succeeded-sanitized.png
windows-security-firewall-status-sanitized.png
```

### Firewall policy list

![Firewall policy list](../screenshots/sanitized/endpoint-security/firewall-policy-list-sanitized.png)

### Firewall policy settings

![Firewall policy settings](../screenshots/sanitized/endpoint-security/firewall-policy-settings-sanitized.png)

### Firewall policy assignment

![Firewall policy assignment](../screenshots/sanitized/endpoint-security/firewall-policy-assignment-sanitized.png)

### Firewall device status

![Firewall device status](../screenshots/sanitized/endpoint-security/firewall-device-status-succeeded-sanitized.png)

### Windows Security firewall status

![Windows Security firewall status](../screenshots/sanitized/endpoint-security/windows-security-firewall-status-sanitized.png)

---

## Troubleshooting Notes

If the policy does not apply:

1. Confirm the device is enrolled in Intune.
2. Confirm the assignment group contains the targeted user or device.
3. Sync the device manually.
4. Restart the device if needed.
5. Wait for Intune reporting to refresh.
6. Check for conflicting firewall policies.

If firewall status looks different locally:

1. Confirm which network profile is active.
2. Check Domain, Private, and Public profiles separately.
3. Confirm the policy settings target all required profiles.
4. Recheck after device sync.

---

## Security and Privacy Notes

Do not upload:

- Tenant IDs
- Full UPNs
- Device IDs
- Object IDs
- Internal IP addresses
- Unsanitized screenshots

Before uploading screenshots, blur or hide:

- Top-right signed-in account
- Tenant/domain name
- Full user principal names
- Device identifiers
- Internal network details

---

## Current Lab Status

Planned.

---

## Next Step

After completing this lab, continue to:

```text
06-endpoint-security/bitlocker-encryption-policy.md
```
