# Troubleshooting Summary

This section documents real issues encountered during the MD-102 Intune lab project — not simulated scenarios. Each case study shows the observed problem, the investigation method, and the resolution.

---

## Case Studies

| File | Scenario | Result |
|---|---|---|
| `intune-enrollment-troubleshooting.md` | WIN-CORP-001 joined Entra ID but MDM showed None — device not visible in Intune | Manual MDM enrollment completed — device appeared as managed and compliant |
| `configuration-policy-conflict-troubleshooting.md` | Windows Security Baseline reported Conflict and Error 65000 (VBS) | Overlapping and unsupported settings set to Not configured — baseline reached Success |
| `remote-actions-diagnostics-troubleshooting.md` | Expected Device diagnostics report not visible in tenant after Collect diagnostics action | Validated from device-level Device action status — action confirmed Complete |

---

## Troubleshooting Skills Demonstrated

- Windows enrollment troubleshooting and MDM state validation
- Microsoft Entra joined vs Intune managed state distinction
- Intune policy conflict investigation and per-setting status analysis
- Windows Security Baseline conflict and VBS error remediation
- Remote action status validation using device-level and tenant-level views
- Portal navigation discrepancy handling and evidence documentation
- Safe handling of screenshots and diagnostic packages for public repositories

---

## Common Troubleshooting Pattern

Across all three case studies, the same basic approach was used:

```text
1. Identify the expected result
2. Observe and capture the actual result
3. Check the relevant portal report or device-side state
4. Identify the specific mismatch or error
5. Apply a targeted, safe remediation
6. Sync or wait for reporting to refresh
7. Confirm the final result
8. Document the lesson learned
```

---

## Evidence Handling

All screenshots in this section are reused from completed labs — no new screenshots were created specifically for troubleshooting documentation. Diagnostic ZIP packages and raw log files are not uploaded to this repository.

---

## Related Labs

| Lab | Relationship |
|---|---|
| `02-device-enrollment/windows-oobe-enrollment.md` | Source lab for enrollment case study |
| `06-endpoint-security/windows-security-baseline.md` | Source lab for policy conflict case study |
| `07-remote-actions-and-monitoring/collect-diagnostics.md` | Source lab for diagnostics case study |
