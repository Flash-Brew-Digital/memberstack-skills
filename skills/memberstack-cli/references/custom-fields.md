---
title: Custom Fields
description: Manage custom fields for your Memberstack members.
tags: ["memberstack","custom-fields","members","data","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack custom-fields <subcommand> [options]
```

## custom-fields list

List all custom fields.

```bash
memberstack custom-fields list
```

### Example

```bash
$ memberstack custom-fields list
[
  {
    "id": "fld_abc123",
    "key": "tier",
    "label": "Member Tier",
    "visibility": "PUBLIC",
    "hidden": false
  }
]
```

## custom-fields create

Create a new custom field.

```bash
memberstack custom-fields create --key <key> --label <label> [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--key <key>` | Field key | Yes |
| `--label <label>` | Field label | Yes |
| `--hidden` | Hide the field | No |
| `--visibility <visibility>` | Field visibility: `PUBLIC` or `PRIVATE` | No |
| `--restrict-to-admin` | Restrict field to admin access | No |
| `--plan-ids <ids...>` | Plan IDs to associate with the field | No |

### Examples

```bash
memberstack custom-fields create --key tier --label "Member Tier"

memberstack custom-fields create \
  --key vip \
  --label "VIP Status" \
  --visibility PRIVATE \
  --restrict-to-admin

memberstack custom-fields create --key type --label "Account Type" --hidden
```

## custom-fields update

Update an existing custom field.

```bash
memberstack custom-fields update <id> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Custom field ID | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--label <label>` | Field label | Yes |
| `--hidden` | Hide the field | No |
| `--no-hidden` | Show the field | No |
| `--table-hidden` | Hide the field from the table | No |
| `--no-table-hidden` | Show the field in the table | No |
| `--visibility <visibility>` | Field visibility: `PUBLIC` or `PRIVATE` | No |
| `--restrict-to-admin` | Restrict field to admin access | No |
| `--no-restrict-to-admin` | Remove admin restriction | No |

### Examples

```bash
memberstack custom-fields update fld_abc123 --label "Updated Tier" --hidden

memberstack custom-fields update fld_abc123 \
  --label "Member Status" \
  --no-hidden \
  --visibility PUBLIC
```

## custom-fields delete

Delete a custom field.

```bash
memberstack custom-fields delete <id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Custom field ID | Yes |

### Example

```bash
memberstack custom-fields delete fld_abc123
```

## FAQ

Q: What is the difference between public and private custom fields?
A: Public custom fields are visible to members and can be read client-side (browser). Private custom fields are only accessible server-side or through the admin API. Use private visibility for sensitive data like internal notes or feature flags.

Q: Can I restrict a custom field to admin access only?
A: Yes. Use the --restrict-to-admin flag when creating or updating a custom field. This prevents members from reading or modifying the field value. Remove the restriction with --no-restrict-to-admin.

Q: Can I associate a custom field with specific plans?
A: Yes. When creating a custom field, use --plan-ids to associate it with one or more plans. This limits the field to members on those plans.
