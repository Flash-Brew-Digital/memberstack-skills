---
title: Command Reference
description: Every Memberstack CLI command at a glance. Quick reference for auth, apps, members, plans, tables, records, custom fields, and skills.
tags: ["memberstack", "cli", "commands", "reference", "api", "terminal"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack <command> [subcommand] [parameters] [options]
```

## Global Flags

These flags work with every command:

| Flag | Description |
|---|---|
| `--live` | Target your production environment instead of sandbox |
| `--json` | Output raw JSON instead of formatted tables |
| `--after <cursor>` | Pagination cursor for list commands |
| `--all` | Auto-paginate through all results |
| `--dry-run` | Preview bulk operations without applying changes |

## Authentication

Manage OAuth login, logout, and session status.

| Command | Description |
|---|---|
| `memberstack auth login` | Open browser-based OAuth flow |
| `memberstack auth logout` | Revoke tokens and delete local credentials |
| `memberstack auth status` | Show current auth state, app ID, and token expiry |
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

## Skills

Manage Memberstack agent skills.

| Command | Description |
|---|---|
| `memberstack skills add <skill>` | Add a Memberstack agent skill |
| `memberstack skills remove <skill>` | Remove a Memberstack agent skill |

[Learn more about the skills command](/docs/skills)

## FAQ

Q: What commands does Memberstack CLI support?
A: The CLI supports commands for authentication, app management, members, plans, data tables, records, custom fields, and agent skills. Each command group includes subcommands for listing, creating, updating, and deleting resources.

Q: How do I target the live environment?
A: Add the --live flag to any command. Without it, all commands run against your sandbox environment.

Q: Can I get JSON output from CLI commands?
A: Yes. Add the --json flag to any command to get raw JSON output instead of formatted tables.
