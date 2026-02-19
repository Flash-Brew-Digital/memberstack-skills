---
title: Records
description: Manage data table records in your Memberstack application.
tags: ["memberstack","records","tables","data","import","export"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack records <subcommand> [options]
```

## records create

Create a new record in a data table.

```bash
memberstack records create <table_key> --data <key=value> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--data <key=value>` | Record field data (repeatable) | Yes |

### Example

```bash
memberstack records create products --data name=Widget --data price=29.99
```

## records update

Update a record in a data table.

```bash
memberstack records update <table_key> <record_id> --data <key=value> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |
| `record_id` | Record ID | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--data <key=value>` | Record field data (repeatable) | Yes |

### Example

```bash
memberstack records update products rec_abc123 --data price=39.99 --data status=active
```

## records delete

Delete a record from a data table.

```bash
memberstack records delete <table_key> <record_id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |
| `record_id` | Record ID | Yes |

### Example

```bash
memberstack records delete products rec_abc123
```

## records query

Query records using a JSON query body.

```bash
memberstack records query <table_key> --query <json>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--query <json>` | Query body as a JSON string | Yes |

### Examples

```bash
# Fetch first 10 records
memberstack records query products --query '{"pagination":{"first":10}}'

# Filter records by field value
memberstack records query products --query '{"filter":{"fieldFilters":{"status":{"equals":"active"}}}}'

# Paginate with cursor
memberstack records query products --query '{"pagination":{"first":10,"after":"cursor_abc"}}'
```

## records count

Count records in a data table.

```bash
memberstack records count <table_key>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Example

```bash
$ memberstack records count products
Total records: 256
```

## records find

Find records with a friendly filter syntax.

```bash
memberstack records find <table_key> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description |
|---|---|
| `--where <clause>` | Filter clause: `"field operator value"` (repeatable) |
| `--take <n>` | Limit number of results |

### Supported Operators

`equals`, `not`, `in`, `notIn`, `lt`, `lte`, `gt`, `gte`, `contains`, `startsWith`, `endsWith`

### Examples

```bash
memberstack records find products --where "status equals active" --take 10
memberstack records find products --where "price gte 20" --where "category equals electronics"
memberstack records find products --where "name contains widget" --take 20
```

## records export

Export all records from a data table.

```bash
memberstack records export <table_key> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description | Default |
|---|---|---|
| `--format <format>` | Output format: `csv` or `json` | `json` |
| `--output <path>` | Output file path | `records-{tableKey}.json` or `.csv` |

### Examples

```bash
memberstack records export products
memberstack records export products --format csv --output products.csv
```

Exported CSV files flatten nested fields with `data.*` prefixes.

## records import

Import records into a data table from a file.

```bash
memberstack records import <table_key> --file <path>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--file <path>` | Input file path (CSV or JSON) | Yes |

### File Format

CSV column headers can optionally use the `data.*` prefix. Both `name` and `data.name` are accepted.

### Examples

```bash
memberstack records import products --file records.csv
memberstack records import products --file records.json
```

## records bulk-update

Bulk update records from a CSV or JSON file.

```bash
memberstack records bulk-update --file <path> [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--file <path>` | Input file with record updates | Yes |
| `--dry-run` | Preview changes without applying them | No |

### File Format

**Required fields:** `id`

**Optional fields:** `data.*` fields

### Examples

```bash
memberstack records bulk-update --file updates.csv
memberstack records bulk-update --file updates.csv --dry-run
```

## records bulk-delete

Bulk delete records matching a filter.

```bash
memberstack records bulk-delete <table_key> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Options

| Option | Description |
|---|---|
| `--where <clause>` | Filter clause: `"field operator value"` (repeatable) |
| `--dry-run` | Preview deletions without applying them |

### Examples

```bash
memberstack records bulk-delete products --where "status equals archived"
memberstack records bulk-delete products --where "price lt 5" --dry-run
```

## FAQ

Q: What is the difference between records query and records find?
A: The query command accepts a raw JSON query body for full control over filters and pagination. The find command provides a friendlier syntax using --where clauses with operators like equals, contains, and gte. Use find for simple lookups and query for advanced filtering.

Q: Can I preview bulk changes before applying them?
A: Yes. Both records bulk-update and records bulk-delete support a --dry-run flag. This shows exactly what would change without modifying any data, so you can verify the operation before committing.

Q: What file formats are supported for import and export?
A: Records can be imported and exported in both CSV and JSON formats. CSV files flatten nested data fields with a data.* prefix. When importing, both name and data.name column headers are accepted.

Q: How do I filter records using the find command?
A: Use --where with a clause in the format "field operator value". Supported operators include equals, not, in, notIn, lt, lte, gt, gte, contains, startsWith, and endsWith. You can chain multiple --where flags to combine filters.
