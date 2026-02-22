---
title: Command Reference
description: Every Memberstack CLI command at a glance. Quick reference for auth, apps, members, plans, prices, and more.
tags: ["memberstack", "cli", "commands", "reference", "api", "terminal"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack <command> [subcommand] [parameters] [options]
```

## Global Options

Global options are available to use with multiple Memberstack CLI commands.

| Flag | Alias | Description |
|---|---|---|
| `--mode <mode>` | | Set environment mode (`sandbox` or `live`) |
| `--live` | | Shorthand for `--mode live` |
| `--sandbox` | | Shorthand for `--mode sandbox` |
| `--json` | `-j` | Output raw JSON instead of formatted tables |
| `--quiet` | `-q` | Suppress banner and non-essential output |
| `--no-color` | | Disable color output (respects the NO_COLOR standard) |
| `--help` | `-h` | Show help for any command |
| `--version` | `-V` | Show the installed CLI version |

### Pagination & Bulk Flags

These flags only apply to specific commands:

| Flag | Applies to | Description |
|---|---|---|
| `--after <cursor>` | List commands | Pagination cursor for fetching the next page of results |
| `--all` | List commands | Auto-paginate through all results |
| `--dry-run` | Bulk operations | Preview changes without applying them |

[Learn more about global options](/docs/global-options)

## Authentication

Manage OAuth login, logout, session status, and profile updates.

| Command | Description |
|---|---|
| `memberstack auth login` | Open browser-based OAuth flow |
| `memberstack auth logout` | Revoke tokens and delete local credentials |
| `memberstack auth status` | Show current auth state, app ID, and token expiry |
| `memberstack auth update-profile` | Update your profile (name, email) |
| `memberstack whoami` | Display authenticated email, app ID, and environment |

[Learn more about the auth command](/docs/auth)

## Apps

Manage your Memberstack applications.

| Command | Description |
|---|---|
| `memberstack apps current` | Show the current app |
| `memberstack apps create` | Create a new app |
| `memberstack apps update` | Update app settings |
| `memberstack apps delete` | Delete an app |
| `memberstack apps restore` | Restore a deleted app |

[Learn more about the apps command](/docs/apps)

## Plans

Manage membership plans.

| Command | Description |
|---|---|
| `memberstack plans list` | List all plans (filterable by status) |
| `memberstack plans get <id>` | Get a plan by ID |
| `memberstack plans create` | Create a new plan |
| `memberstack plans update <id>` | Update a plan |
| `memberstack plans delete <id>` | Delete a plan |
| `memberstack plans order` | Reorder plans by priority |

[Learn more about the plans command](/docs/plans)

## Prices

Manage prices for plans.

| Command | Description |
|---|---|
| `memberstack prices create` | Create a price for a plan |
| `memberstack prices update <priceId>` | Update a price |
| `memberstack prices activate <priceId>` | Reactivate a price |
| `memberstack prices deactivate <priceId>` | Deactivate a price |
| `memberstack prices delete <priceId>` | Delete a price |

[Learn more about the prices command](/docs/prices)

## Members

Manage members, including bulk operations and import/export.

| Command | Description |
|---|---|
| `memberstack members list` | List members with pagination and sorting |
| `memberstack members get <id>` | Get a member by ID or email |
| `memberstack members create` | Create a new member |
| `memberstack members update <id>` | Update a member |
| `memberstack members delete <id>` | Delete a member |
| `memberstack members add-plan <id>` | Add a free plan to a member |
| `memberstack members remove-plan <id>` | Remove a free plan from a member |
| `memberstack members count` | Show total member count |
| `memberstack members find` | Find members by custom field or plan |
| `memberstack members stats` | Show member statistics |
| `memberstack members export` | Export all members to CSV or JSON |
| `memberstack members import` | Import members from CSV or JSON |
| `memberstack members bulk-update` | Bulk update members from file |
| `memberstack members bulk-add-plan` | Add a plan to multiple members |
| `memberstack members note <id>` | Update or clear a member's note |

[Learn more about the members command](/docs/members)

## Data Tables

Manage data tables and their schemas.

| Command | Description |
|---|---|
| `memberstack tables list` | List all data tables |
| `memberstack tables get <key>` | Get a table by key or ID |
| `memberstack tables describe <key>` | Show table schema and access rules |
| `memberstack tables create` | Create a new table |
| `memberstack tables update <id>` | Update table name or access rules |
| `memberstack tables delete <id>` | Delete a table |

[Learn more about the tables command](/docs/tables)

## Records

Manage table records, including queries, bulk operations, and import/export.

| Command | Description |
|---|---|
| `memberstack records create <key>` | Create a record |
| `memberstack records update <key> <id>` | Update a record |
| `memberstack records delete <key> <id>` | Delete a record |
| `memberstack records query <key>` | Query records with raw JSON filters |
| `memberstack records count <key>` | Count records in a table |
| `memberstack records find <key>` | Filter records with `--where` syntax |
| `memberstack records export <key>` | Export records to CSV or JSON |
| `memberstack records import <key>` | Import records from CSV or JSON |
| `memberstack records bulk-update` | Bulk update records from file |
| `memberstack records bulk-delete <key>` | Bulk delete records matching filters |

[Learn more about the records command](/docs/records)

## Custom Fields

Manage custom member fields.

| Command | Description |
|---|---|
| `memberstack custom-fields list` | List all custom fields |
| `memberstack custom-fields create` | Create a custom field |
| `memberstack custom-fields update <id>` | Update a custom field |
| `memberstack custom-fields delete <id>` | Delete a custom field |

[Learn more about the custom-fields command](/docs/custom-fields)

## Permissions

Manage permissions and link them to plans or members.

| Command | Description |
|---|---|
| `memberstack permissions list` | List all permissions |
| `memberstack permissions create` | Create a permission |
| `memberstack permissions update <id>` | Update a permission |
| `memberstack permissions delete <id>` | Delete a permission |
| `memberstack permissions link-plan` | Link permissions to a plan |
| `memberstack permissions unlink-plan` | Unlink a permission from a plan |
| `memberstack permissions link-member` | Link permissions to a member |
| `memberstack permissions unlink-member` | Unlink a permission from a member |

[Learn more about the permissions command](/docs/permissions)

## Auth Providers

Manage auth providers (e.g. Google, GitHub, Facebook).

| Command | Description |
|---|---|
| `memberstack providers list` | List configured auth providers |
| `memberstack providers configure` | Configure an auth provider |
| `memberstack providers remove <id>` | Remove an auth provider |

[Learn more about the providers command](/docs/providers)

## SSO

Manage SSO apps.

| Command | Description |
|---|---|
| `memberstack sso list` | List all SSO apps |
| `memberstack sso create` | Create an SSO app |
| `memberstack sso update <id>` | Update an SSO app |
| `memberstack sso delete <id>` | Delete an SSO app |

[Learn more about the sso command](/docs/sso)

## Users

Manage users with access to your app.

| Command | Description |
|---|---|
| `memberstack users list` | List all users with access to the app |
| `memberstack users get <id_or_email>` | Get a user by ID or email |
| `memberstack users add` | Add a user to the app |
| `memberstack users remove <userId>` | Remove a user from the app |
| `memberstack users update-role <userId>` | Update a user's role |

[Learn more about the users command](/docs/users)

## Skills

Manage Memberstack agent skills.

| Command | Description |
|---|---|
| `memberstack skills add <skill>` | Add a Memberstack agent skill |
| `memberstack skills remove <skill>` | Remove a Memberstack agent skill |

[Learn more about the skills command](/docs/skills)

## Utility

Standalone commands for CLI maintenance.

| Command | Description |
|---|---|
| `memberstack update` | Update the CLI to the latest version |
| `memberstack reset` | Delete local data files and clear authentication |

[Learn more about the update command](/docs/update) · [Learn more about the reset command](/docs/reset)

## FAQ

Q: What commands does the Memberstack CLI support?
A: The CLI supports commands for authentication, app management, members, plans, prices, data tables, records, custom fields, permissions, auth providers, SSO, users, agent skills, and utility commands (update, reset). Each command group includes subcommands for listing, creating, updating, and deleting resources.

Q: How do I target the live environment?
A: Use --mode live or the --live shorthand with any command. You can also set the MEMBERSTACK_MODE environment variable. Without it, all commands run against your sandbox environment.

Q: Can I get JSON output from CLI commands?
A: Yes. Add the --json flag to any command to get raw JSON output instead of formatted tables.

