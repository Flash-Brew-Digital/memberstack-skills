---
title: Tables
description: Manage data tables in your Memberstack application.
tags: ["memberstack","tables","data","schema","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack tables <subcommand> [options]
```

## tables list

List all data tables.

```bash
memberstack tables list
```

### Example

```bash
$ memberstack tables list
[
  {
    "id": "tbl_abc123",
    "name": "Products",
    "key": "products",
    ...
  }
]
```

## tables get

Get a data table by key or ID.

```bash
memberstack tables get <table_key>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Examples

```bash
memberstack tables get products
memberstack tables get tbl_abc123
```

## tables describe

Show detailed schema information for a table.

```bash
memberstack tables describe <table_key>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `table_key` | Table key or ID | Yes |

### Description

Displays the table name, key, ID, access rules (create, read, update, delete), and all fields with their type, required status, and references.

### Example

```bash
$ memberstack tables describe products
Table: Products
  Key:  products
  ID:   tbl_abc123

Access Rules:
  Create:  ADMIN
  Read:    PUBLIC
  Update:  ADMIN
  Delete:  ADMIN

Fields:
  name        String    required
  price       Number    required
  category    String
  owner       Relation  → members
```

## tables create

Create a new data table.

```bash
memberstack tables create [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--name <name>` | Table name | Yes |
| `--key <key>` | Table key (unique identifier) | Yes |
| `--create-rule <rule>` | Access rule for creating records | No |
| `--read-rule <rule>` | Access rule for reading records | No |
| `--update-rule <rule>` | Access rule for updating records | No |
| `--delete-rule <rule>` | Access rule for deleting records | No |

Access rule values: `PUBLIC`, `AUTHENTICATED`, `AUTHENTICATED_OWN`, `ADMIN_ONLY`

### Examples

```bash
memberstack tables create --name "Products" --key products
memberstack tables create --name "Orders" --key orders --create-rule AUTHENTICATED --read-rule PUBLIC
```

## tables update

Update a data table.

```bash
memberstack tables update <id> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Table ID | Yes |

### Options

| Option | Description |
|---|---|
| `--name <name>` | Table name |
| `--create-rule <rule>` | Access rule for creating records |
| `--read-rule <rule>` | Access rule for reading records |
| `--update-rule <rule>` | Access rule for updating records |
| `--delete-rule <rule>` | Access rule for deleting records |

Access rule values: `PUBLIC`, `AUTHENTICATED`, `AUTHENTICATED_OWN`, `ADMIN_ONLY`

### Examples

```bash
memberstack tables update tbl_abc123 --name "Updated Products"
memberstack tables update tbl_abc123 --delete-rule ADMIN_ONLY --read-rule PUBLIC
```

## tables delete

Delete a data table.

```bash
memberstack tables delete <id>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id` | Table ID | Yes |

### Example

```bash
memberstack tables delete tbl_abc123
```

## FAQ

Q: How do I see the schema of a data table?
A: Run memberstack tables describe followed by the table key. This displays the table name, key, ID, access rules for CRUD operations, and all fields with their type, required status, and references.

Q: What access rules can I set on a table?
A: Tables support four access rule levels for create, read, update, and delete operations. PUBLIC allows anyone, AUTHENTICATED requires login, AUTHENTICATED_OWN restricts access to a member's own records, and ADMIN_ONLY limits access to admins.

Q: Can I reference a table by its key instead of its ID?
A: Yes. Most table commands accept either the table key (e.g., products) or the table ID (e.g., tbl_abc123). Using keys is shorter and easier to remember.
