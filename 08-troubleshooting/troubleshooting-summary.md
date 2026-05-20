# Troubleshooting Summary

This file summarizes the real troubleshooting scenarios documented during the MD-102 Intune virtual company lab project.

---

## Purpose

The purpose of this section is to show that the project includes real-world troubleshooting, not only successful policy creation.

In endpoint administration, admins must be able to:

- Identify where a problem is happening.
- Compare expected and observed behavior.
- Check device, user, policy, and report status.
- Use portal evidence and endpoint validation.
- Document resolution steps clearly.
- Avoid uploading sensitive diagnostic data to a public repository.

---

## Troubleshooting Files

| File | Scenario | Status |
|---|---|---|
| intune-enrollment-troubleshooting.md | Device Entra joined but Intune MDM enrollment initially showed MDM None | Completed |
| configuration-policy-conflict-troubleshooting.md | Windows Security Baseline conflicts and VBS error 65000 | Completed |
| remote-actions-diagnostics-troubleshooting.md | Collect Diagnostics completed, but expected Device diagnostics report path was not visible in the same way | Completed |

---

## Case Study 1: Intune Enrollment Troubleshooting

Related source lab:

```text
02-device-enrollment/windows-oobe-enrollment.md
```

Issue observed:

```text
WIN-CORP-001 joined Microsoft Entra ID.
The Microsoft Entra device record initially showed MDM: None.
The device was not immediately visible as managed by Intune.
```

Resolution:

```text
Manual MDM enrollment was completed.
The device later appeared in Intune as managed by Intune and compliant.
```

Important learning:

```text
Microsoft Entra joined does not automatically mean Intune managed.
```

Evidence screenshots reused from:

```text
screenshots/sanitized/device-enrollment/
```

---

## Case Study 2: Configuration Policy Conflict Troubleshooting

Related source lab:

```text
06-endpoint-security/windows-security-baseline.md
```

Issue observed:

```text
Windows Security Baseline initially reported Conflict and Error states.
VBS related setting showed Error code 65000.
Firewall and Defender related settings overlapped with dedicated endpoint security policies.
```

Resolution:

```text
Overlapping baseline settings were changed to Not configured.
Device Guard and VBS related settings were also changed to Not configured for the lab device.
The final baseline device assignment status showed Success.
```

Important learning:

```text
Security baselines can overlap with dedicated endpoint security policies.
The administrator must decide which policy owns each setting.
```

Evidence screenshots reused from:

```text
screenshots/sanitized/endpoint-security/
```

---

## Case Study 3: Remote Actions Diagnostics Troubleshooting

Related source lab:

```text
07-remote-actions-and-monitoring/collect-diagnostics.md
```

Issue observed:

```text
The expected Device diagnostics report path was not visible in the same way in the lab tenant.
```

Resolution:

```text
The action was validated from the device-level Device action status tab.
Tenant diagnostics settings were also reviewed under Tenant administration.
```

Important learning:

```text
Portal layouts can vary. Validate the action result using available device-level and tenant-level evidence.
```

Evidence screenshots reused from:

```text
screenshots/sanitized/remote-actions-and-monitoring/
```

---

## Troubleshooting Skills Demonstrated

This section demonstrates practical skills in:

- Windows enrollment troubleshooting.
- Microsoft Entra joined versus Intune managed state validation.
- MDM enrollment troubleshooting.
- Intune policy conflict investigation.
- Security baseline remediation.
- Device Guard and VBS error handling in a lab environment.
- Remote action status validation.
- Intune reporting and portal navigation troubleshooting.
- Safe handling of screenshots and diagnostic packages.

---

## Common Troubleshooting Pattern Used

Across the labs, the same basic troubleshooting pattern was followed:

```text
1. Identify the expected result.
2. Observe the actual result.
3. Capture evidence.
4. Check the relevant portal report.
5. Check the device-side state.
6. Identify the mismatch.
7. Apply a safe remediation.
8. Sync or wait for reporting.
9. Confirm the final result.
10. Document the lesson learned.
```

---

## Evidence Handling Rule

No fake screenshots were created for this section.

This troubleshooting section reuses existing screenshots from completed labs:

```text
screenshots/sanitized/device-enrollment/
screenshots/sanitized/endpoint-security/
screenshots/sanitized/remote-actions-and-monitoring/
```

Diagnostic ZIP packages and sensitive data are not uploaded to GitHub.

---

## Privacy and Security Notes

Before publishing screenshots, hide:

- Tenant names
- Full email addresses
- Tenant IDs
- Device IDs
- Object IDs
- Serial numbers
- Hardware hashes
- Diagnostic package contents
- Internal IP addresses
- MFA prompts
- Recovery keys
- Top-right signed-in account details

---

## Current Status

| Task | Status |
|---|---|
| Intune enrollment troubleshooting documented | Completed |
| Configuration policy conflict troubleshooting documented | Completed |
| Remote actions diagnostics troubleshooting documented | Completed |
| Troubleshooting summary created | Completed |
| Screenshots reused from existing repo evidence | Completed |

---

## Next Step

Continue normal lab progression and add future troubleshooting files only when real issues are encountered.

Possible future troubleshooting case studies:

```text
conditional-access-troubleshooting.md
office-app-signin-troubleshooting.md
autopilot-reset-or-device-recovery-troubleshooting.md
```
