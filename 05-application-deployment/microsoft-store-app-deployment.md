# Microsoft Store App Deployment with Intune

This file documents Microsoft Store app deployment using Microsoft Intune.

## Objective

Test application deployment using **Microsoft Store app (new)** in Intune.

This lab covers two common deployment scenarios:

- Required apps that install automatically
- Available apps that users install manually from Company Portal

## Lab Environment

| Item | Value |
|---|---|
| Test device | WIN-CORP-001 |
| Operating system | Windows 11 |
| Management | Microsoft Intune |
| Test user | user01 |
| Assignment group | GRP-Pilot-Users |
| Deployment method | Microsoft Store app (new) |

## Apps Deployed

| App | Assignment type | Result |
|---|---|---|
| Company Portal | Required | Installed successfully |
| Spotify | Required | Installed successfully |
| VLC UWP | Required | Installed successfully |
| ChatGPT | Available for enrolled devices | Visible in Company Portal |

## Key Learning

```text
Required = Intune installs the app automatically
Available for enrolled devices = User installs the app from Company Portal
```

## Test Result

| Test | Result |
|---|---|
| Company Portal required deployment | Successful |
| Spotify required deployment | Successful |
| VLC required deployment | Successful |
| ChatGPT available app visibility in Company Portal | Successful |
| Store app deployment monitoring reviewed | Successful |

## Screenshots

Suggested folder:

```text
screenshots/sanitized/application-deployment/
```

Suggested screenshots:

```text
store-apps-list-sanitized.jpg
company-portal-required-assignment-sanitized.jpg
spotify-required-assignment-sanitized.jpg
vlc-required-assignment-sanitized.jpg
chatgpt-available-assignment-sanitized.jpg
store-apps-managed-apps-status-sanitized.jpg
chatgpt-company-portal-available-sanitized.jpg
```

## Current Lab Status

Completed:

- Company Portal deployed as a Required Store app
- Spotify deployed as a Required Store app
- VLC deployed as a Required Store app
- ChatGPT deployed as an Available Store app
- App deployment status reviewed in Intune

Pending:

- Add screenshots as available
