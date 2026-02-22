---
title: Auth Providers
description: Manage auth providers such as Google, Facebook, GitHub, LinkedIn, Spotify, and Dribbble.
tags: ["memberstack", "auth", "providers", "sso", "oauth", "google", "facebook", "github", "linkedin", "spotify", "dribbble", "cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack providers <subcommand> [options]
```

## providers list

List configured auth providers.

```bash
memberstack providers list
```

### Example

```bash
$ memberstack providers list
ID              Type      Name            Enabled   Client ID
sso_abc123      GOOGLE    Google Login    true      123456789.apps.googleusercontent.com
sso_def456      GITHUB    GitHub Login    false
```

## providers configure

Configure an auth provider. Use this to set up a new provider or update an existing one.

```bash
memberstack providers configure [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--type <type>` | Provider type: `GOOGLE`, `FACEBOOK`, `GITHUB`, `LINKEDIN`, `SPOTIFY`, `DRIBBBLE` | Yes |
| `--name <name>` | Display name | No |
| `--client-id <id>` | OAuth client ID | No |
| `--client-secret <secret>` | OAuth client secret | No |
| `--status <status>` | Provider status: `enabled`, `disabled` | No |

> **WARN:** Setting `--status enabled` requires both `--client-id` and `--client-secret` to be provided.

### Examples

```bash
# Configure a Google provider with credentials and enable it
memberstack providers configure --type GOOGLE --name "Google Login" --client-id YOUR_CLIENT_ID --client-secret YOUR_CLIENT_SECRET --status enabled

# Update the display name of an existing provider
memberstack providers configure --type GITHUB --name "Sign in with GitHub"

# Disable a provider without removing it
memberstack providers configure --type FACEBOOK --status disabled
```

## providers remove

Remove an auth provider by its configuration ID.

```bash
memberstack providers remove <id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Provider configuration ID | Yes |

### Example

```bash
memberstack providers remove sso_abc123
```

## FAQ

Q: What auth providers are supported?
A: The CLI supports Google, Facebook, GitHub, LinkedIn, Spotify, and Dribbble as auth providers.

Q: How do I enable a provider?
A: Use memberstack providers configure with --type, --client-id, --client-secret, and --status enabled. Both --client-id and --client-secret are required when enabling a provider.

Q: How do I disable a provider without removing it?
A: Use memberstack providers configure --type GOOGLE --status disabled. This keeps the configuration but disables the provider.

