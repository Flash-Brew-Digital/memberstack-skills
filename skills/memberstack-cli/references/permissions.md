---
title: Permissions
description: Manage permissions and link them to plans or members.
tags: ["memberstack", "permissions", "plans", "members", "cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack permissions <subcommand> [options]
```

## permissions list

List all permissions.

```bash
memberstack permissions list
```

### Example

```bash
$ memberstack permissions list
ID              Name            Description
perm_abc123     edit-posts      Can edit posts
perm_def456     view-dashboard  Can view the dashboard
```

## permissions create

Create a permission.

```bash
memberstack permissions create [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--name <name>` | Permission name | Yes |
| `--description <desc>` | Permission description | No |

### Examples

```bash
memberstack permissions create --name edit-posts
memberstack permissions create --name view-dashboard --description "Can view the dashboard"
```

## permissions update

Update a permission.

```bash
memberstack permissions update <permissionId> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `permissionId` | Permission ID to update | Yes |

### Options

| Option | Description |
|---|---|
| `--name <name>` | Permission name |
| `--description <desc>` | Permission description |

### Example

```bash
memberstack permissions update perm_abc123 --name edit-all-posts --description "Can edit all posts"
```

## permissions delete

Delete a permission.

```bash
memberstack permissions delete <permissionId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `permissionId` | Permission ID to delete | Yes |

### Example

```bash
memberstack permissions delete perm_abc123
```

## permissions link-plan

Link permissions to a plan.

```bash
memberstack permissions link-plan [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--plan-id <id>` | Plan ID | Yes |
| `--permission-id <id>` | Permission ID (repeatable) | Yes |

### Examples

```bash
memberstack permissions link-plan --plan-id pln_abc123 --permission-id perm_def456
memberstack permissions link-plan --plan-id pln_abc123 --permission-id perm_def456 --permission-id perm_ghi789
```

## permissions unlink-plan

Unlink a permission from a plan.

```bash
memberstack permissions unlink-plan [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--plan-id <id>` | Plan ID | Yes |
| `--permission-id <id>` | Permission ID | Yes |

### Example

```bash
memberstack permissions unlink-plan --plan-id pln_abc123 --permission-id perm_def456
```

## permissions link-member

Link permissions to a member.

```bash
memberstack permissions link-member [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--member-id <id>` | Member ID | Yes |
| `--permission-id <id>` | Permission ID (repeatable) | Yes |

### Examples

```bash
memberstack permissions link-member --member-id mem_abc123 --permission-id perm_def456
memberstack permissions link-member --member-id mem_abc123 --permission-id perm_def456 --permission-id perm_ghi789
```

## permissions unlink-member

Unlink a permission from a member.

```bash
memberstack permissions unlink-member [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--member-id <id>` | Member ID | Yes |
| `--permission-id <id>` | Permission ID | Yes |

### Example

```bash
memberstack permissions unlink-member --member-id mem_abc123 --permission-id perm_def456
```

## FAQ

Q: What are permissions?
A: Permissions are named access controls you create and then link to plans or individual members. They let you gate content or features based on what a member has access to.

Q: Can I link multiple permissions at once?
A: Yes. The link-plan and link-member commands accept multiple --permission-id flags to link several permissions in a single command.

Q: What is the difference between linking to a plan vs a member?
A: Linking to a plan gives the permission to every member on that plan. Linking to a member gives the permission to that specific member only, regardless of their plan.

