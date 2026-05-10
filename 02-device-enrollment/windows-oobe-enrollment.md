# Windows OOBE Enrollment

This file documents the first corporate Windows device enrollment using Windows Out-of-Box Experience, Microsoft Entra ID, and Microsoft Intune.

---

## Objective

Enroll a corporate Windows 11 device into Microsoft Intune by signing in with a Microsoft Entra ID work account during Windows Out-of-Box Experience.

This lab will validate that:

- A Windows device can be set up for work or school during OOBE.
- The device can join Microsoft Entra ID.
- The device can automatically enroll into Microsoft Intune.
- The device can appear in the Intune admin center.
- The device can be managed as a corporate Windows device.

---

## Why This Lab Matters

Windows OOBE enrollment is one of the most important modern Windows enrollment methods.

In a real company, a user can receive a new or reset Windows device, connect it to the internet, sign in with a work account, and allow the device to become cloud managed.

Simple flow:

```text
Windows OOBE
-> User signs in with Microsoft Entra ID account
-> Device joins Microsoft Entra ID
-> Automatic MDM enrollment enrolls the device into Intune
-> Device becomes managed
```

This lab is the first Windows device enrollment test in the MD-102 Intune virtual company project.

---

## Lab Environment

| Item | Planned Value |
|---|---|
| Test device | WIN-CORP-001 |
| Device type | Laptop |
| Ownership | Corporate |
| Operating system | Windows 11 Pro or supported edition |
| Enrollment method | Windows OOBE work or school setup |
| Join type | Microsoft Entra joined |
| Management | Microsoft Intune |
| Primary user | user01 |
| Assignment group | GRP-Pilot-Users |
| Current status | In progress |

---

## Prerequisites

Before starting this lab, the following should be completed:

- Microsoft Entra ID lab users created.
- Microsoft Entra ID security groups created.
- user01 created and available for testing.
- user01 added to GRP-Pilot-Users.
- user01 assigned an Intune-capable license.
- Automatic MDM enrollment configured or ready to verify.
- Windows test device reset or ready for OOBE.
- Device connected to the internet during setup.

---

## Important Notes

This lab is not Windows Autopilot.

This lab uses the basic corporate Windows OOBE work or school setup flow.

Windows Autopilot will be documented separately in:

```text
02-device-enrollment/windows-autopilot-user-driven-enrollment.md
```

---

## Device Naming

The lab device is documented as:

```text
WIN-CORP-001
```

If Windows initially shows a default device name, document it in the test result and rename the device later if needed.

Example note:

```text
Windows assigned a default device name during initial enrollment. The device is documented as WIN-CORP-001 for lab tracking.
```

---

## Steps to Perform

### Step 1: Prepare the Windows Device

Reset or reinstall the Windows test device so that it starts from Windows Out-of-Box Experience.

The device should display the first setup screens, such as:

```text
Region selection
Keyboard selection
Network connection
Work or school setup
```

Connect the device to the internet using Wi-Fi or Ethernet.

---

### Step 2: Choose Work or School Setup

During Windows setup, when asked how to set up the device, choose:

```text
Set up for work or school
```

Do not choose personal use for this corporate enrollment lab.

---

### Step 3: Sign In as user01

Sign in using the lab user account:

```text
user01
```

Use the full lab user principal name when signing in, but hide the full domain in screenshots.

---

### Step 4: Complete Windows Setup

Continue through the setup prompts until Windows reaches the desktop.

Allow Windows time to complete sign-in, policy processing, and enrollment.

---

### Step 5: Verify Work or School Connection Locally

On the Windows device, go to:

```text
Settings
-> Accounts
-> Access work or school
```

Expected result:

```text
The device shows a connected work or school account.
```

This confirms that the device is connected to the lab organization account.

---

### Step 6: Verify Device in Intune

Open:

```text
https://intune.microsoft.com
```

Go to:

```text
Devices
-> Windows
-> Windows devices
```

Look for the enrolled Windows device.

Expected device properties:

```text
Platform: Windows
Management: Intune
Join type: Microsoft Entra joined
Primary user: user01
Ownership: Corporate or organization-owned
```

---

### Step 7: Open Device Overview in Intune

Open the device record in Intune and review:

- Device name
- Primary user
- Compliance status
- Ownership
- Managed by
- Microsoft Entra join type
- Last check-in

---

## Expected Result

After this lab is completed:

- WIN-CORP-001 should complete Windows OOBE.
- user01 should be able to sign in with a work account.
- The device should join Microsoft Entra ID.
- The device should enroll into Microsoft Intune.
- The device should appear under Windows devices in Intune.
- The device should be ready for compliance, app deployment, and configuration profile testing.

---

## Test Result

| Test Item | Result |
|---|---|
| Windows OOBE started | Pending |
| Work or school setup selected | Pending |
| user01 signed in successfully | Pending |
| Device joined Microsoft Entra ID | Pending |
| Device enrolled into Intune | Pending |
| Device visible in Intune | Pending |
| Device overview verified | Pending |
| Final lab result | Pending |

---

## Screenshots

Screenshots should be stored in:

```text
screenshots/sanitized/device-enrollment/
```

Recommended screenshot filenames:

```text
windows-oobe-work-school-selection-sanitized.png
windows-oobe-user01-signin-sanitized.png
win-corp-001-access-work-school-sanitized.png
win-corp-001-intune-windows-devices-list-sanitized.png
win-corp-001-intune-overview-sanitized.png
```

Minimum recommended screenshots:

```text
win-corp-001-access-work-school-sanitized.png
win-corp-001-intune-overview-sanitized.png
```

> [!NOTE]
> OOBE screenshots can be difficult to capture. If the OOBE screens cannot be captured safely, document the steps and capture the post-enrollment verification screens instead.

---

## Screenshot Links

Image links will be added after the screenshots are captured, sanitized, and uploaded to GitHub.

---

## Troubleshooting Notes

If the device does not show the work or school setup option:

1. Confirm the Windows edition supports Microsoft Entra join.
2. Confirm the device is connected to the internet.
3. Confirm the device is not using Windows Home edition.
4. Restart OOBE if needed.

If sign-in fails:

1. Confirm user01 exists in Microsoft Entra ID.
2. Confirm the password is correct.
3. Confirm user01 is allowed to sign in.
4. Confirm the account has the required license.
5. Check for MFA or Conditional Access prompts.

If the device does not appear in Intune:

1. Confirm automatic MDM enrollment is configured.
2. Confirm user01 is in the MDM user scope.
3. Confirm user01 has an Intune-capable license.
4. Wait several minutes and refresh Intune.
5. Check Windows Settings > Accounts > Access work or school.
6. Check Intune enrollment failures if available.

If the device appears with a random name:

1. Document the original name.
2. Rename later if needed.
3. Continue tracking the device as WIN-CORP-001 in the lab documentation.

---

## Security and Privacy Notes

This is a public learning repository.

Do not upload:

- Full real email addresses
- Real tenant names
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Autopilot hardware hashes
- BitLocker recovery keys
- Passwords
- MFA QR codes
- Internal IP addresses
- Unsanitized screenshots

Before uploading screenshots, hide or blur:

- Top-right signed-in admin account
- Tenant or domain name
- Full user principal names
- Device IDs
- Object IDs
- Serial numbers
- Any recovery keys, tokens, or QR codes

---

## Current Status

| Task | Status |
|---|---|
| windows-oobe-enrollment.md created | Completed |
| Windows device prepared for OOBE | Planned |
| Work or school setup selected | Planned |
| user01 sign-in completed | Planned |
| Microsoft Entra join verified | Planned |
| Intune enrollment verified | Planned |
| Screenshots added | Planned |

---

## Next Step

Perform Windows OOBE enrollment on the test device:

```text
Reset or start Windows OOBE
Choose Set up for work or school
Sign in as user01
Verify Access work or school
Verify device in Intune
Capture sanitized screenshots
Update this file from In progress to Completed
```
