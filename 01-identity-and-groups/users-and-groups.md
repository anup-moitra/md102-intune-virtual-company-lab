# Users and Groups

## Lab status

**Status:** Completed  
**Lab category:** Identity and groups  
**Identity platform:** Microsoft Entra ID  
**Management platform:** Microsoft Intune  
**Lab company:** Contoso Startup Lab  
**Primary test user:** user01  
**Primary admin account:** admin01  
**Assignment strategy:** Microsoft Entra security groups  

---

## Lab objective

The objective of this lab is to create the Microsoft Entra ID users and security groups needed for the MD-102 Intune virtual company lab.

These users and groups form the foundation for later Intune tasks, including:

- Windows device enrollment
- Windows Autopilot deployment
- BYOD enrollment
- Application deployment
- Configuration profiles
- Compliance policies
- Conditional Access testing
- Endpoint security policy assignment

This lab validates that users, groups, licenses, and pilot targeting groups are ready for the rest of the project.

---

## Why this lab matters

Microsoft Intune policies, apps, compliance rules, and Conditional Access controls are usually assigned to users or groups.

In a real environment, administrators should avoid assigning policies directly to individual users or all devices without testing. Instead, they use groups to control rollout safely.

Simple flow:

```text
Create users
-> Create groups
-> Add users or devices to groups
-> Assign Intune policies or apps to groups
-> Validate deployment on pilot users/devices
```

This lab creates the identity foundation for the full MD-102 project.

---

## Lab environment

| Item | Value |
|---|---|
| Identity platform | Microsoft Entra ID |
| Device management platform | Microsoft Intune |
| Lab company | Contoso Startup Lab |
| Main administrator | admin01 |
| Main pilot user | user01 |
| BYOD test user | user03 |
| Primary assignment model | Security groups |
| User-based pilot group | GRP-Pilot-Users |
| Autopilot device group | GRP-Autopilot-Devices |
| Final lab status | Completed |

---

## Prerequisites

Before starting this lab, the following were required:

- Access to the Microsoft Entra admin center.
- Access to the Microsoft Intune admin center.
- A lab tenant or test tenant.
- Permission to create users.
- Permission to create groups.
- Permission to assign licenses.
- Available Microsoft 365 or Intune-capable licenses.
- A planned naming standard for users and groups.

---

## Identity and group design

### Lab users

| Display name | Username | Department | Role | Status |
|---|---|---|---|---|
| Admin User 01 | admin01 | IT | Lab administrator | Created |
| User 01 | user01 | Management | Standard user / pilot user | Created |
| User 02 | user02 | Finance | Standard user | Created |
| User 03 | user03 | HR | Standard user / BYOD test user | Created |
| User 04 | user04 | Operations | Standard user / mobile test user | Created |
| User 05 | user05 | Operations | Standard user / policy test user | Created |

---

### Lab groups

| Group name | Group type | Purpose | Status |
|---|---|---|---|
| GRP-All-Lab-Users | Security group | General lab user targeting | Created |
| GRP-Pilot-Users | Security group | Pilot user testing and app deployment targeting | Created |
| GRP-Windows-Users | Security group | Windows user targeting | Created |
| GRP-BYOD-Users | Security group | BYOD enrollment targeting | Created |
| GRP-Mobile-Users | Security group | Mobile device targeting | Created |
| GRP-IT-Admins | Security group | Admin targeting | Created |
| GRP-Autopilot-Devices | Security group / dynamic device group | Windows Autopilot device targeting | Created |

---

### Group membership

| Group name | Members |
|---|---|
| GRP-All-Lab-Users | user01, user02, user03, user04, user05 |
| GRP-Pilot-Users | user01 |
| GRP-Windows-Users | user01, user02 |
| GRP-BYOD-Users | user01, user03 |
| GRP-Mobile-Users | user01, user04 |
| GRP-IT-Admins | admin01 |
| GRP-Autopilot-Devices | WINAUTO452 / Autopilot device targeting |

> [!NOTE]
> `GRP-Autopilot-Devices` was used to target the Windows Autopilot deployment profile to the imported Autopilot device. After enrollment, the device appeared in Intune as `WINAUTO452`.

---

### License assignment

| User | Intune license | Microsoft 365 Apps | Purpose |
|---|---|---|---|
| admin01 | Available as needed | Optional | Lab administration |
| user01 | Assigned | Assigned / available through Microsoft 365 Business Premium | Main testing user |
| user02 | Available as needed | Optional | Windows testing |
| user03 | Available as needed | Optional | BYOD testing |
| user04 | Available as needed | Optional | Mobile testing |
| user05 | Available as needed | Optional | Policy testing |

> [!NOTE]
> The exact license name may depend on the available Microsoft 365 or Intune trial/subscription in the lab tenant.

---

## Configuration flow

```text
Open Microsoft Entra admin center
-> Create lab users
-> Create lab security groups
-> Add users to groups
-> Assign license to user01
-> Create or prepare Autopilot device group
-> Validate group membership
-> Use groups for later Intune assignments
```

---

## Steps performed

### Step 1 - Opened Microsoft Entra admin center

Opened:

```text
https://entra.microsoft.com
```

Signed in with the lab administrator account.

---

### Step 2 - Created lab users

Navigation used:

```text
Microsoft Entra admin center
-> Entra ID
-> Users
-> All users
-> New user
-> Create new user
```

Created the planned users:

```text
admin01
user01
user02
user03
user04
user05
```

---

### Step 3 - Verified users in Microsoft Entra ID

After creation, the users were visible under:

```text
Entra ID
-> Users
-> All users
```

The users list confirmed that the lab user accounts were created successfully.

---

### Step 4 - Created security groups

Navigation used:

```text
Microsoft Entra admin center
-> Entra ID
-> Groups
-> All groups
-> New group
```

Created the planned security groups:

```text
GRP-All-Lab-Users
GRP-Pilot-Users
GRP-Windows-Users
GRP-BYOD-Users
GRP-Mobile-Users
GRP-IT-Admins
GRP-Autopilot-Devices
```

---

### Step 5 - Added users to groups

Users were added to the planned Microsoft Entra ID security groups.

Important memberships configured:

```text
GRP-Pilot-Users -> user01
GRP-IT-Admins -> admin01
GRP-BYOD-Users -> user01, user03
GRP-Mobile-Users -> user01, user04
```

---

### Step 6 - Assigned license to user01

A license was assigned to:

```text
user01
```

This prepared `user01` for:

- Intune enrollment
- App deployment
- Configuration profile testing
- Compliance policy testing
- Conditional Access testing
- Microsoft 365 Apps validation

---

### Step 7 - Prepared Autopilot device group

The Autopilot device group was prepared for imported Autopilot devices:

```text
GRP-Autopilot-Devices
```

This group was later used to assign the Windows Autopilot deployment profile.

---

### Step 8 - Used groups in later Intune labs

The groups created in this lab were later reused throughout the project.

`GRP-Pilot-Users` was used for user-based assignments such as:

```text
Microsoft Store apps
Win32 app deployment
Microsoft 365 Apps deployment
Corporate wallpaper user policy
```

`GRP-Autopilot-Devices` was used for device-based assignments such as:

```text
Windows Autopilot deployment profile
Endpoint security policies
Device restrictions
PowerShell file staging scripts
```

---

## Validation

### User validation

Validation confirmed that:

- Lab users were created in Microsoft Entra ID.
- The administrator account `admin01` existed.
- The pilot user `user01` existed.
- Additional test users existed for Windows, BYOD, mobile, and policy testing.

---

### Group validation

Validation confirmed that:

- Lab security groups were created.
- User memberships were configured.
- `user01` was a member of `GRP-Pilot-Users`.
- `admin01` was a member of `GRP-IT-Admins`.
- `GRP-Autopilot-Devices` was available for Autopilot targeting.

---

### License validation

Validation confirmed that:

- `user01` had the required license.
- `user01` was ready for Intune-managed enrollment and application deployment testing.

---

### Assignment validation

The groups were later validated by using them in real Intune assignments.

`GRP-Pilot-Users` was used successfully for:

```text
Microsoft Store app deployment
Win32 7-Zip app deployment
Microsoft 365 Apps deployment
Corporate wallpaper ADMX policy
```

`GRP-Autopilot-Devices` was used successfully for:

```text
Windows Autopilot profile assignment
Defender Antivirus policy
Windows Firewall policy
BitLocker policy
USB storage block policy
Corporate wallpaper staging script
```

---

## Final test result

| Validation item | Status |
|---|---|
| Lab users created | Completed |
| Lab security groups created | Completed |
| user01 added to GRP-Pilot-Users | Completed |
| admin01 added to GRP-IT-Admins | Completed |
| user01 license assigned | Completed |
| GRP-Pilot-Users prepared for user-based targeting | Completed |
| GRP-Autopilot-Devices prepared for device-based targeting | Completed |
| Autopilot device group used for WINAUTO452 | Completed |
| Groups reused in later Intune labs | Completed |
| Screenshots captured and uploaded | Completed |
| Final lab result | Completed |

---

## Screenshots captured

Screenshots are stored in:

```text
screenshots/sanitized/identity-and-groups/
```

### Admin user creation review screen

![Admin user creation review screen](../screenshots/sanitized/identity-and-groups/lab-user-admin01-create-sanitized.png)

### Lab users created in Microsoft Entra ID

![Lab users created in Microsoft Entra ID](../screenshots/sanitized/identity-and-groups/lab-users-created-sanitized.png)

### Lab groups created in Microsoft Entra ID

![Lab groups created in Microsoft Entra ID](../screenshots/sanitized/identity-and-groups/lab-groups-created-sanitized.png)

### Pilot users group membership

![Pilot users group membership](../screenshots/sanitized/identity-and-groups/grp-pilot-users-membership-sanitized.png)

### User 01 license assignment

![User 01 license assignment](../screenshots/sanitized/identity-and-groups/user01-license-assignment-sanitized.png)

### Autopilot dynamic device group rule

![Autopilot dynamic device group rule](../screenshots/sanitized/identity-and-groups/autopilot-device-group-dynamic-rule-sanitized.png)

### Autopilot dynamic group rule validation

![Autopilot dynamic group rule validation](../screenshots/sanitized/identity-and-groups/autopilot-device-group-rule-validation-sanitized.png)

### Autopilot device group member

![Autopilot device group member](../screenshots/sanitized/identity-and-groups/autopilot-device-group-member-sanitized.png)

---

## Screenshot file list

```text
lab-user-admin01-create-sanitized.png
lab-users-created-sanitized.png
lab-groups-created-sanitized.png
grp-pilot-users-membership-sanitized.png
user01-license-assignment-sanitized.png
autopilot-device-group-dynamic-rule-sanitized.png
autopilot-device-group-rule-validation-sanitized.png
autopilot-device-group-member-sanitized.png
```

---

## Related labs

The users and groups created in this lab are used by later labs.

| Lab file | Relationship |
|---|---|
| `02-device-enrollment/windows-oobe-enrollment.md` | Uses `user01` for Windows enrollment |
| `02-device-enrollment/windows-autopilot-user-driven-enrollment.md` | Uses `GRP-Autopilot-Devices` for Autopilot profile assignment and `user01` for OOBE sign-in |
| `02-device-enrollment/windows-byod-enrollment.md` | Uses `user03` and `GRP-BYOD-Users` for BYOD enrollment |
| `03-configuration-profiles/windows-corporate-wallpaper-policy.md` | Uses `GRP-Pilot-Users` for the user-based wallpaper policy |
| `03-configuration-profiles/windows-device-restrictions-profile.md` | Uses `GRP-Autopilot-Devices` for device restriction targeting |
| `05-application-deployment/microsoft-store-app-deployment.md` | Uses `GRP-Pilot-Users` for required and available app assignments |
| `05-application-deployment/win32-app-deployment-7zip.md` | Uses `GRP-Pilot-Users` for required Win32 app deployment |
| `05-application-deployment/microsoft-365-apps-autopilot-deployment.md` | Uses `GRP-Pilot-Users` for Microsoft 365 Apps required deployment |
| `06-endpoint-security/windows-defender-antivirus-policy.md` | Uses `GRP-Autopilot-Devices` for endpoint security targeting |
| `06-endpoint-security/windows-firewall-policy.md` | Uses `GRP-Autopilot-Devices` for endpoint security targeting |
| `06-endpoint-security/bitlocker-encryption-policy.md` | Uses `GRP-Autopilot-Devices` for endpoint security targeting |

---

## Troubleshooting notes

### User creation issues

If a user cannot be created:

1. Confirm the signed-in account has permission to create users.
2. Confirm the username is unique.
3. Check whether the tenant has user creation restrictions.
4. Confirm required user properties are completed.

---

### Group creation issues

If a group cannot be created:

1. Confirm the signed-in account has permission to create groups.
2. Confirm the group name is unique.
3. Confirm the group type is set to Security.
4. Confirm Microsoft Entra ID is not blocking group creation due to permissions or policy.

---

### License assignment issues

If a license cannot be assigned:

1. Confirm licenses are available in the tenant.
2. Confirm the user has a usage location configured if required.
3. Confirm the account has the required admin role.
4. Confirm the selected license includes Intune or the required service plan.

---

### Group membership delay

If group membership does not appear immediately:

1. Refresh the group members page.
2. Wait a few minutes for Microsoft Entra ID to update.
3. Search for the user or device again inside the group membership page.
4. Confirm the correct group was selected.

---

### Autopilot dynamic group delay

If an Autopilot device does not appear in the Autopilot group:

1. Confirm the device was imported into Windows Autopilot devices.
2. Confirm the dynamic device rule is correct.
3. Wait for dynamic group processing.
4. Validate the dynamic membership rule.
5. Confirm the deployment profile is assigned to the correct group.

---

## Enterprise reflection

In real organizations, identity and group design should be planned before deploying Intune policies.

A good group strategy helps administrators:

- Pilot new policies safely.
- Separate user-based and device-based assignments.
- Avoid assigning risky policies to all users too early.
- Reuse the same assignment groups across apps, compliance, configuration, and security policies.
- Troubleshoot policy targeting more easily.

Recommended enterprise design:

```text
Use pilot groups first
-> Validate policy/app behavior
-> Expand to department groups
-> Expand to production groups
```

Example:

```text
GRP-Pilot-Users
-> GRP-Department-Users
-> GRP-All-Corporate-Users
```

For device-based policies:

```text
GRP-Autopilot-Devices
-> GRP-Windows-Corporate-Devices
-> GRP-All-Managed-Windows-Devices
```

This lab follows that same principle by using `GRP-Pilot-Users` and `GRP-Autopilot-Devices` as controlled rollout targets.

---

## Security and privacy notes

This is a public learning repository.

Do not upload:

- Full real email addresses
- Real tenant names
- Tenant IDs
- User object IDs
- Group object IDs
- Device object IDs
- Device serial numbers
- Autopilot hardware hashes
- Passwords
- MFA QR codes
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Object IDs
- Device IDs
- Serial numbers
- Hardware hashes
- Authentication prompts
- Sensitive account information

---

## Key learning outcomes

This lab demonstrated how to:

- Create Microsoft Entra ID lab users.
- Create Microsoft Entra ID security groups.
- Organize users into role-based groups.
- Prepare pilot users for Intune testing.
- Prepare BYOD users for enrollment testing.
- Prepare an Autopilot device group for corporate Windows enrollment.
- Assign licenses to test users.
- Use groups for user-based Intune assignments.
- Use groups for device-based Intune assignments.
- Build a reusable identity foundation for future Intune labs.

---

## Lab conclusion

The identity and group foundation for the MD-102 Intune virtual company lab was completed successfully.

Final result:

```text
Lab users were created in Microsoft Entra ID.
Security groups were created and populated.
user01 was prepared as the main pilot user.
admin01 was prepared as the lab administrator.
GRP-Pilot-Users and GRP-Autopilot-Devices were ready for Intune assignments.
The groups were later reused successfully across enrollment, app deployment, configuration profile, and endpoint security labs.
```
