---
title: Apps
description: Manage Memberstack apps.
tags: ["memberstack","apps","settings","cli","oauth"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack apps <subcommand> [options]
```

## apps current

Show the current app.

```bash
memberstack apps current
```

## apps create

Create a new app.

```bash
memberstack apps create [options]
```

### Options

| Option | Description |
|---|---|
| `--name <name>` | App name |
| `--stack <stack>` | Tech stack: `REACT`, `WEBFLOW`, `VANILLA`, `WORDPRESS` |
| `--wordpress-page-builder <builder>` | WordPress page builder: `GUTENBERG`, `ELEMENTOR`, `DIVI`, `BEAVER_BUILDER`, `BRICKS`, `CORNERSTONE`, `OTHER` |
| `--template-id <templateId>` | Template ID to use |

### Example

```bash
memberstack apps create --name "My App" --stack REACT
```

## apps update

Update the current app.

```bash
memberstack apps update [options]
```

### Options

| Option | Description |
|---|---|
| `--name <name>` | App name |
| `--stack <stack>` | Tech stack: `REACT`, `WEBFLOW`, `VANILLA`, `WORDPRESS` |
| `--status <status>` | App status: `ACTIVE`, `DELETED` |
| `--wordpress-page-builder <builder>` | WordPress page builder |
| `--business-entity-name <name>` | Business entity name |
| `--terms-of-service-url <url>` | Terms of service URL |
| `--privacy-policy-url <url>` | Privacy policy URL |
| `--prevent-disposable-emails` | Prevent disposable emails |
| `--no-prevent-disposable-emails` | Allow disposable emails |
| `--captcha-enabled` | Enable captcha |
| `--no-captcha-enabled` | Disable captcha |
| `--require-user-2fa` | Require user 2FA |
| `--no-require-user-2fa` | Disable required 2FA |
| `--disable-concurrent-logins` | Disable concurrent logins |
| `--no-disable-concurrent-logins` | Allow concurrent logins |
| `--member-session-duration-days <days>` | Member session duration in days |
| `--allow-member-self-delete` | Allow members to self-delete |
| `--no-allow-member-self-delete` | Prevent member self-deletion |

### Example

```bash
memberstack apps update --name "Acme App" --captcha-enabled --require-user-2fa
```

## apps delete

Delete an app.

```bash
memberstack apps delete --app-id <appId>
```

### Options

| Option | Description |
|---|---|
| `--app-id <appId>` | App ID to delete |

## apps restore

Restore a deleted app.

```bash
memberstack apps restore --app-id <appId>
```

### Options

| Option | Description |
|---|---|
| `--app-id <appId>` | App ID to restore |

## FAQ

Q: Can I manage multiple Memberstack apps from the CLI?
A: Yes. You can create, update, delete, and restore apps using the apps command. Use apps current to see which app you're working with. To switch apps, log out and log back in with a different account.

Q: What happens when I delete an app?
A: Deleting an app with apps delete removes it from your account. If you need to recover a deleted app, use apps restore with the app ID to bring it back.

Q: What tech stacks does Memberstack support?
A: You can set your app's tech stack to React, Webflow, Vanilla, or WordPress when creating or updating an app. WordPress apps also support specifying a page builder such as Gutenberg, Elementor, Divi, Beaver Builder, Bricks, or Cornerstone.
