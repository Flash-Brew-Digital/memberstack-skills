---
title: Authentication
description: Manage OAuth authentication with the CLI.
tags: ["memberstack","oauth","authentication","auth","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack auth <subcommand> [options]
```

The CLI supports OAuth authentication with your Memberstack account.

## auth login

Authenticate with Memberstack via the browser-based OAuth flow.

```bash
memberstack auth login
```

### Description

Opens your default browser to the Memberstack authorization page.

Tokens are stored locally at `~/.memberstack/auth.json` with restricted file permissions. The access token is used for authenticated requests directly to the Memberstack API only, your credentials are never sent to third-party services.

### Example

```bash
$ memberstack auth login
Opening browser for authentication...
✔ Authentication successful
```

## auth logout

Remove stored authentication tokens.

```bash
memberstack auth logout
```

### Description

Revokes the current refresh token (best-effort) and deletes the local token file at `~/.memberstack/auth.json`.

### Example

```bash
$ memberstack auth logout
✔ Logged out successfully
```

## auth status

Show current authentication status.

```bash
memberstack auth status
```

### Description

Displays whether you are currently authenticated, your app ID, token expiration time, refresh token availability, and token validity.

### Example

```bash
$ memberstack auth status
Authentication Status
  Status:         Logged in
  App ID:         app_abc123
  Access Token:   Expires in 45 minutes
  Refresh Token:  Available
  Token Valid:    Yes
```

## FAQ

Q: How do I log in to the Memberstack CLI?
A: Run memberstack auth login. This opens your browser to authenticate with Memberstack via OAuth. Once approved, tokens are stored locally and you can start running commands.

Q: Where are my authentication tokens stored?
A: Tokens are stored locally at ~/.memberstack/auth.json with restricted file permissions. Your credentials are used only for authenticated requests to the Memberstack API and are never sent to third-party services.

Q: What do I do if my session expires?
A: Run memberstack auth status to check your token status. If your access token has expired, the CLI will attempt to refresh it automatically using your refresh token. If that fails, run memberstack auth login again.
