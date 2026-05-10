# Users and Groups

This file documents the planned Microsoft Entra ID users and groups for the MD-102 Intune virtual company lab.

---

## Status

Planned / documentation template prepared / not yet tested

---

## Objective

Create Microsoft Entra ID lab users and security groups that will be used for Intune policy assignments, application deployment, compliance testing, Conditional Access testing, BYOD testing, and Windows Autopilot testing.

This lab will validate that:

- Lab users can be created in Microsoft Entra ID.
- Security groups can be created for targeted Intune assignments.
- Pilot users can be separated from general lab users.
- Users and groups can be used later for device enrollment, app deployment, compliance, and Conditional Access.

---

## Why This Lab Matters

Microsoft Intune policies, apps, compliance policies, and Conditional Access rules are usually assigned to users or groups.

Instead of assigning settings directly to individual users, real environments use groups to make management easier and safer.

Simple example:

```text
Create group
-> Add users or devices
-> Assign Intune policy to group
-> Policy applies to group members
```

This lab creates the identity foundation for the rest of the MD-102 project.

---

## Lab Environment

| Item | Planned Value |
|---|---|
| Identity platform | Microsoft Entra ID |
| Management platform | Microsoft Intune |
| Lab company | Contoso Startup Lab |
| Main test user | user01 |
| Main admin account | admin01 |
| Assignment strategy | Security groups |
| Current status | Planned |

---

## Planned Lab Users

| Display Name | Username | Department | Role | Status |
|---|---|---|---|---|
| Admin User 01 | admin01 | IT | Lab administrator | Planned |
| User 01 | user01 | Management | Standard user / pilot user | Planned |
| User 02 | user02 | Finance | Standard user | Planned |
| User 03 | user03 | HR | Standard user | Planned |
| User 04 | user04 | Operations | Standard user | Planned |
| User 05 | user05 | Operations | Standard user | Planned |

---

## Planned Lab Groups

| Group Name | Group Type | Purpose | Status |
|---|---|---|---|
| GRP-All-Lab-Users | Security group | General lab user targeting | Planned |
| GRP-Pilot-Users | Security group | Pilot users for testing policies and apps | Planned |
| GRP-Windows-Users | Security group | Windows user targeting | Planned |
| GRP-BYOD-Users | Security group | BYOD user targeting | Planned |
| GRP-Mobile-Users | Security group | Android and iOS user targeting | Planned |
| GRP-IT-Admins | Security group | Lab administrator targeting | Planned |
| GRP-Autopilot-Devices | Security group | Autopilot registered Windows devices | Planned |

---

## Planned Group Membership

| Group Name | Planned Members |
|---|---|
| GRP-All-Lab-Users | user01, user02, user03, user04, user05 |
| GRP-Pilot-Users | user01 |
| GRP-Windows-Users | user01, user02 |
| GRP-BYOD-Users | user01, user03 |
| GRP-Mobile-Users | user01, user04 |
| GRP-IT-Admins | admin01 |
| GRP-Autopilot-Devices | Autopilot test device after import |

---

## Planned License Assignment

| User | Intune License | Microsoft 365 Apps License | Purpose |
|---|---|---|---|
| admin01 | Planned | Optional | Lab administration |
| user01 | Planned | Planned | Main testing user |
| user02 | Planned | Optional | Additional Windows testing |
| user03 | Planned | Optional | BYOD testing |
| user04 | Planned | Optional | Mobile testing |
| user05 | Planned | Optional | Additional policy testing |

> [!NOTE]
> The exact license name may depend on the available Microsoft 365 or Intune trial/subscription in the lab tenant.

---

## Group Assignment Strategy

The lab will use a pilot-first assignment approach.

Instead of assigning new policies to all users or all devices immediately, new policies should first target a small pilot group.

Recommended pilot group:

```text
GRP-Pilot-Users
```

This group will be used for early testing of:

- Windows enrollment
- Configuration profiles
- Compliance policies
- Conditional Access report-only testing
- Microsoft Store app deployment
- Win32 app deployment
- Microsoft 365 Apps deployment

---

## Steps to Perform

### Step 1: Open Microsoft Entra Admin Center

Go to:

```text
https://entra.microsoft.com
```

Sign in with the lab administrator account.

### Step 2: Create Lab Users

Go to:

```text
Microsoft Entra admin center
-> Identity
-> Users
-> All users
-> New user
```

Create the planned users:

```text
admin01
user01
user02
user03
user04
user05
```

### Step 3: Create Security Groups

Go to:

```text
Microsoft Entra admin center
-> Identity
-> Groups
-> All groups
-> New group
```

Create the planned security groups:

```text
GRP-All-Lab-Users
GRP-Pilot-Users
GRP-Windows-Users
GRP-BYOD-Users
GRP-Mobile-Users
GRP-IT-Admins
GRP-Autopilot-Devices
```

### Step 4: Add Users to Groups

Add users based on the planned group membership table.

For the first pilot test, make sure this group contains:

```text
GRP-Pilot-Users -> user01
```

### Step 5: Assign Licenses

Assign the required Intune/Microsoft 365 license to the users that will perform enrollment and app testing.

At minimum, assign a license to:

```text
user01
```

### Step 6: Verify Users and Groups

Confirm:

- Users are visible in Microsoft Entra ID.
- Groups are visible in Microsoft Entra ID.
- Group memberships are correct.
- user01 has the required license.

---

## Expected Result

After this lab is completed:

- Lab users should exist in Microsoft Entra ID.
- Lab security groups should exist in Microsoft Entra ID.
- user01 should be a member of GRP-Pilot-Users.
- user01 should have an Intune-capable license.
- Groups should be ready for future Intune assignments.

---

## Test Result

| Test Item | Result |
|---|---|
| Lab users created | Pending |
| Lab security groups created | Pending |
| user01 added to GRP-Pilot-Users | Pending |
| admin01 added to GRP-IT-Admins | Pending |
| user01 license assigned | Pending |
| Users and groups verified | Pending |

---

## Screenshot Placeholders

Screenshots should be stored in:

```text
screenshots/sanitized/identity-and-groups/
```

Suggested screenshot filenames:

```text
lab-users-created-sanitized.png
lab-groups-created-sanitized.png
user01-license-assignment-sanitized.png
grp-pilot-users-membership-sanitized.png
grp-autopilot-devices-sanitized.png
```

> [!NOTE]
> Do not add image links until the screenshot files actually exist in the repository. This avoids broken images in GitHub.

---

## Troubleshooting Notes

If a user cannot be created:

1. Confirm the signed-in account has permission to create users.
2. Confirm the username is unique.
3. Check whether the tenant has user creation restrictions.

If a group cannot be created:

1. Confirm the signed-in account has permission to create groups.
2. Confirm the group name is unique.
3. Confirm the group type is Security.

If a license cannot be assigned:

1. Confirm licenses are available in the tenant.
2. Confirm the user location is set if required.
3. Confirm the account has license administrator or global administrator permissions.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Full real email addresses
- Real tenant names
- Tenant IDs
- User object IDs
- Group object IDs
- Passwords
- MFA QR codes
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Object IDs
- Any authentication prompts or sensitive account information

---

## Current Status

| Task | Status |
|---|---|
| users-and-groups.md created | Completed |
| Lab users created in Entra ID | Planned |
| Lab groups created in Entra ID | Planned |
| Group memberships configured | Planned |
| Intune licenses assigned | Planned |
| Screenshots added | Planned |

---

## Next Step

Perform the hands-on identity setup in Microsoft Entra ID:

```text
Create users
Create security groups
Add group memberships
Assign license to user01
Take sanitized screenshots
Update this file from Planned to Completed
```
