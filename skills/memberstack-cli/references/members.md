---
title: Members
description: Manage members in your Memberstack application.
tags: ["memberstack","members","plans","import","export","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack members <subcommand> [options]
```

## members list

List members with optional pagination and sorting.

```bash
memberstack members list [options]
```

### Options

| Option | Description | Default |
|---|---|---|
| `--after <cursor>` | Pagination cursor (from previous `endCursor`) | — |
| `--order <order>` | Sort order: `ASC` or `DESC` | `ASC` |
| `--limit <number>` | Maximum members to return (max 200) | `50` |
| `--all` | Auto-paginate and fetch all members | — |

### Examples

```bash
memberstack members list
memberstack members list --limit 100 --order DESC
memberstack members list --all
```

Results are written to `members.json` in the current directory.

## members get

Get a member by ID or email.

```bash
memberstack members get <id_or_email>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id_or_email` | Member ID (`mem_...`) or email address | Yes |

### Examples

```bash
memberstack members get mem_abc123
memberstack members get user@example.com
```

## members create

Create a new member.

```bash
memberstack members create [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--email <email>` | Member email address | Yes |
| `--password <password>` | Member password | Yes |
| `--plans <planId>` | Plan ID to connect (repeatable) | No |
| `--custom-fields <key=value>` | Custom field value (repeatable) | No |
| `--meta-data <key=value>` | Metadata field value (repeatable) | No |
| `--login-redirect <url>` | Login redirect URL | No |

### Examples

```bash
memberstack members create --email user@example.com --password secure123

memberstack members create \
  --email user@example.com \
  --password secure123 \
  --plans pln_abc123 \
  --custom-fields tier=premium \
  --meta-data ref=partner
```

## members update

Update an existing member.

```bash
memberstack members update <id> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Member ID (`mem_...`) | Yes |

### Options

| Option | Description |
|---|---|
| `--email <email>` | Update email address |
| `--custom-fields <key=value>` | Custom field value (repeatable) |
| `--meta-data <key=value>` | Metadata field value (repeatable) |
| `--json <json>` | Additional JSON data as a string |
| `--login-redirect <url>` | Login redirect URL |

### Examples

```bash
memberstack members update mem_abc123 --email newemail@example.com
memberstack members update mem_abc123 --custom-fields tier=gold
```

## members delete

Delete a member.

```bash
memberstack members delete <id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Member ID (`mem_...`) | Yes |

### Examples

```bash
memberstack members delete mem_abc123
```

## members add-plan

Add a free plan to a member.

```bash
memberstack members add-plan <id> --plan-id <planId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Member ID (`mem_...`) | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--plan-id <planId>` | Plan ID to add (`pln_...`) | Yes |

### Example

```bash
memberstack members add-plan mem_abc123 --plan-id pln_xyz789
```

## members remove-plan

Remove a free plan from a member.

```bash
memberstack members remove-plan <id> --plan-id <planId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Member ID (`mem_...`) | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--plan-id <planId>` | Plan ID to remove (`pln_...`) | Yes |

### Example

```bash
memberstack members remove-plan mem_abc123 --plan-id pln_xyz789
```

## members count

Show total member count.

```bash
memberstack members count
```

### Example

```bash
$ memberstack members count
Total members: 1,234
```

## members find

Find members by custom field values or plan.

```bash
memberstack members find [options]
```

### Options

| Option | Description |
|---|---|
| `--field <key=value>` | Filter by custom field (repeatable) |
| `--plan <planId>` | Filter by plan ID |

### Examples

```bash
memberstack members find --plan pln_abc123
memberstack members find --field tier=premium --field status=active
```

## members stats

Show member statistics.

```bash
memberstack members stats
```

### Description

Displays an overview of member activity including total count, active vs inactive members, recent signups, and a breakdown by plan.

### Example

```bash
$ memberstack members stats
Member Statistics
  Total members:       1,234
  Active members:      1,100
  Inactive members:    134
  Signups (7 days):    42
  Signups (30 days):   187

Members by Plan:
  Free Plan:           800
  Pro Plan:            300
  Enterprise:          100
  No Plan:             34
```

## members export

Export all members to CSV or JSON.

```bash
memberstack members export [options]
```

### Options

| Option | Description | Default |
|---|---|---|
| `--format <format>` | Output format: `csv` or `json` | `json` |
| `--output <path>` | Output file path | `members.json` or `members.csv` |

### Examples

```bash
memberstack members export
memberstack members export --format csv --output members-backup.csv
```

Exported CSV files flatten nested fields with `customFields.*` and `metaData.*` prefixes.

## members import

Import members from a CSV or JSON file.

```bash
memberstack members import --file <path>
```

### Options

| Option | Description | Required |
|---|---|---|
| `--file <path>` | Input file path (CSV or JSON) | Yes |

### File Format

**Required fields:** `email`, `password`

**Optional fields:** `plans` (comma-separated plan IDs), `loginRedirect`, `customFields.*`, `metaData.*`

### Examples

```bash
memberstack members import --file members.csv
memberstack members import --file members.json
```

## members bulk-update

Bulk update members from a CSV or JSON file.

```bash
memberstack members bulk-update --file <path> [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--file <path>` | Input file with member updates | Yes |
| `--dry-run` | Preview changes without applying them | No |

### File Format

**Required fields:** `id`

**Optional fields:** `email`, `loginRedirect`, `customFields.*`, `metaData.*`

### Examples

```bash
memberstack members bulk-update --file updates.csv
memberstack members bulk-update --file updates.csv --dry-run
```

## members bulk-add-plan

Add a plan to multiple members at once.

```bash
memberstack members bulk-add-plan --plan <planId> --filter <filter> [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--plan <planId>` | Plan ID to add (`pln_...`) | Yes |
| `--filter <filter>` | Member filter: `no-plan` or `all` | Yes |
| `--dry-run` | Preview without applying changes | No |

### Examples

```bash
memberstack members bulk-add-plan --plan pln_abc123 --filter no-plan
memberstack members bulk-add-plan --plan pln_abc123 --filter all --dry-run
```

## FAQ

Q: How do I export all my members?
A: Run memberstack members export to export all members as JSON. Add --format csv for CSV output. You can specify a custom file path with --output, otherwise it defaults to members.json or members.csv in the current directory.

Q: Can I bulk update members from a file?
A: Yes. Use memberstack members bulk-update --file updates.csv to update members in bulk. Each row must include the member ID. Add --dry-run to preview changes before applying them.

Q: How do I find members by custom field values?
A: Use memberstack members find --field key=value to search by custom field. You can combine multiple field filters and also filter by plan ID with --plan.

Q: What file format do I need for importing members?
A: Import files (CSV or JSON) require email and password fields. Optional fields include plans (comma-separated plan IDs), loginRedirect, and any custom fields or metadata using the customFields.* and metaData.* prefixes.
