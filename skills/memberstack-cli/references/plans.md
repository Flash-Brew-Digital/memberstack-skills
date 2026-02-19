---
title: Plans
description: Manage Memberstack plans.
tags: ["memberstack","plans","billing","subscriptions","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack plans <subcommand> [options]
```

## plans list

List all plans.

```bash
memberstack plans list [options]
```

### Options

| Option | Description |
|---|---|
| `--status <status>` | Filter by status: `ALL`, `ACTIVE`, `INACTIVE` |
| `--order-by <field>` | Order by field: `PRIORITY`, `CREATED_AT` |

## plans get

Get a plan by ID.

```bash
memberstack plans get <id>
```

### Arguments

| Argument | Description |
|---|---|
| `id` | Plan ID |

## plans create

Create a new plan.

```bash
memberstack plans create [options]
```

### Options

| Option | Description |
|---|---|
| `--name <name>` | Plan name |
| `--description <description>` | Plan description |
| `--icon <icon>` | Plan icon |
| `--is-paid` | Mark plan as paid |
| `--team-accounts-enabled` | Enable team accounts |
| `--team-account-invite-signup-link <url>` | Team account invite signup link |
| `--team-account-upgrade-link <url>` | Team account upgrade link |

### Example

```bash
memberstack plans create --name "Pro" --description "Professional tier" --is-paid
```

## plans update

Update a plan.

```bash
memberstack plans update <id> [options]
```

### Arguments

| Argument | Description |
|---|---|
| `id` | Plan ID |

### Options

| Option | Description |
|---|---|
| `--name <name>` | Plan name |
| `--description <description>` | Plan description |
| `--icon <icon>` | Plan icon |
| `--status <status>` | Plan status: `ACTIVE`, `INACTIVE` |
| `--limit-members` | Enable member limit |
| `--no-limit-members` | Disable member limit |
| `--member-limit <number>` | Maximum number of members |
| `--team-account-upgrade-link <url>` | Team account upgrade link |
| `--team-account-invite-signup-link <url>` | Team account invite signup link |
| `--restrict-to-admin` | Restrict plan to admin |
| `--no-restrict-to-admin` | Remove admin restriction |
| `--redirect <key=url>` | Set redirect URL (repeatable). Keys: `afterSignup`, `afterLogin`, `afterLogout`, `afterPurchase`, `afterCancel`, `afterReplace`, `verificationRequired` |
| `--permission-id <id>` | Permission ID (repeatable; replaces all permissions) |
| `--allowed-domain <email>` | Allowed email domain (repeatable; replaces all domains) |

### Example

```bash
memberstack plans update pln_abc123 --status ACTIVE --restrict-to-admin
```

## plans delete

Delete a plan.

```bash
memberstack plans delete <id>
```

### Arguments

| Argument | Description |
|---|---|
| `id` | Plan ID |

## plans order

Reorder plans by priority.

```bash
memberstack plans order --plan <planId:priority> [--plan <planId:priority> ...]
```

### Options

| Option | Description |
|---|---|
| `--plan <planId:priority>` | Plan ID and priority (repeatable), for example `--plan pln_abc:1` |

### Example

```bash
memberstack plans order --plan pln_basic:1 --plan pln_pro:2 --plan pln_enterprise:3
```

## FAQ

Q: How do I create a paid plan?
A: Run memberstack plans create --name "Pro" --is-paid to create a paid plan. You can also set a description and icon during creation. Pricing and billing details are configured in the Memberstack dashboard.

Q: Can I reorder plans?
A: Yes. Use memberstack plans order with --plan flags to set priority for each plan. For example, --plan pln_basic:1 --plan pln_pro:2 --plan pln_enterprise:3 sets the display order.

Q: How do I restrict a plan to admin-only access?
A: Use memberstack plans update with the --restrict-to-admin flag. This prevents members from self-selecting the plan. Remove the restriction with --no-restrict-to-admin.
