# Safe Upload Instructions

This ZIP is a cleaned current-state project package for the MD-102 Intune virtual company lab.

## Important Screenshot Warning

This package contains the screenshot folder structure and placeholder documentation. If you already have real sanitized screenshots in GitHub, do not delete them.

Recommended safe workflow:

```text
1. Clone your existing GitHub repo.
2. Copy these updated Markdown files and folders into the cloned repo.
3. Keep the existing screenshots/sanitized/ folder from your current repo.
4. Run git status.
5. Confirm screenshots are not listed as deleted.
6. Commit and push.
```

Before pushing, check:

```cmd
git status
```

If you see screenshot files listed as deleted, stop and restore/copy them back before committing.

## Suggested Git Commands

```cmd
cd /d "C:\Users\Anup Moitra\Documents\md102-intune-virtual-company-lab"
git pull --rebase
git status
git add .
git commit -m "Update MD-102 Intune lab documentation structure"
git push
```

## Privacy Reminder

Do not upload:

- Full real email addresses
- Tenant IDs
- Device IDs
- Serial numbers
- Autopilot hardware hashes
- BitLocker recovery keys
- MFA QR codes
- Request IDs
- Correlation IDs
- Unsanitized screenshots
