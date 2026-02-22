---
title: SSO
description: Manage SSO apps for your Memberstack application.
tags: ["memberstack", "sso", "single-sign-on", "oauth", "cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack sso <subcommand> [options]
```

## sso list

List all SSO apps.

```bash
memberstack sso list
```

### Example

```bash
$ memberstack sso list
ID              Name            Client ID
sso_abc123      My App          ck_abc123
sso_def456      Staging App     ck_def456
```

## sso create

Create an SSO app.

```bash
memberstack sso create [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--name <name>` | App name | Yes |
| `--redirect-uri <uri>` | Redirect URI (repeatable) | Yes |

### Examples

```bash
memberstack sso create --name "My App" --redirect-uri https://example.com/callback
memberstack sso create --name "My App" --redirect-uri https://example.com/callback --redirect-uri https://staging.example.com/callback
```

## sso update

Update an SSO app.

```bash
memberstack sso update <id> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | SSO app ID | Yes |

### Options

| Option | Description |
|---|---|
| `--name <name>` | App name |
| `--redirect-uri <uri>` | Redirect URI (repeatable; replaces all URIs) |

### Example

```bash
memberstack sso update sso_abc123 --name "Production App" --redirect-uri https://example.com/callback
```

## sso delete

Delete an SSO app.

```bash
memberstack sso delete <id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | SSO app ID | Yes |

### Example

```bash
memberstack sso delete sso_abc123
```

## FAQ

Q: What are SSO apps?
A: SSO apps let your members authenticate through your own OAuth provider. You create an SSO app, set redirect URIs, and use the generated client ID and secret to integrate with your authentication flow.

Q: Can I have multiple redirect URIs?
A: Yes. Use the --redirect-uri flag multiple times when creating or updating an SSO app to register multiple redirect URIs.

Q: How do I rotate an SSO app's credentials?
A: Delete the existing SSO app and create a new one. The new app will receive a fresh client ID and client secret.

