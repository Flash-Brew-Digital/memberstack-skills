---
title: Users
description: Manage users with access to your Memberstack application.
tags: ["memberstack", "users", "roles", "access", "cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack users <subcommand> [options]
```

## users list

List all users with access to the app.

```bash
memberstack users list
```

### Example

```bash
$ memberstack users list
ID          Email                  First Name  Last Name  Role
usr_abc123  admin@example.com      Jane        Doe        ADMIN
usr_def456  viewer@example.com     John        Smith      MEMBERS_READ
```

## users get

Get a user by ID or email.

```bash
memberstack users get <id_or_email>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `id_or_email` | User ID or email address | Yes |

### Examples

```bash
memberstack users get usr_abc123
memberstack users get admin@example.com
```

## users add

Add a user to the app.

> **INFO:** Users must have an existing Memberstack account before they can be added to an app. They can sign up on the Memberstack website.

```bash
memberstack users add [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--email <email>` | Email address of the user to add | Yes |
| `--role <role>` | Role to assign: `ADMIN`, `OWNER`, `MEMBERS_WRITE`, or `MEMBERS_READ` | No |

### Examples

```bash
memberstack users add --email user@example.com
memberstack users add --email user@example.com --role ADMIN
```

## users remove

Remove a user from the app.

```bash
memberstack users remove <userId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `userId` | User ID to remove | Yes |

### Example

```bash
memberstack users remove usr_abc123
```

## users update-role

Update a user's role.

```bash
memberstack users update-role <userId> --role <role>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `userId` | User ID to update | Yes |

### Options

| Option | Description | Required |
|---|---|---|
| `--role <role>` | New role: `ADMIN`, `OWNER`, `MEMBERS_WRITE`, or `MEMBERS_READ` | Yes |

### Example

```bash
memberstack users update-role usr_abc123 --role MEMBERS_WRITE
```

## FAQ

Q: What roles can I assign to a user?
A: You can assign ADMIN, OWNER, MEMBERS_WRITE, or MEMBERS_READ. Use the --role option when adding a user or updating their role.

Q: Can I look up a user by email?
A: Yes. Use memberstack users get with either a user ID or email address.

Q: How do I change a user's role?
A: Use memberstack users update-role with the user ID and --role flag to assign a new role.

