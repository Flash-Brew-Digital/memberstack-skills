---
title: Prices
description: Manage prices for your Memberstack plans.
tags: ["memberstack", "prices", "plans", "subscription", "billing", "cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack prices <subcommand> [options]
```

## prices create

Create a price for a plan.

```bash
memberstack prices create [options]
```

### Options

| Option | Description | Required |
|---|---|---|
| `--plan-id <id>` | Plan ID to add the price to | Yes |
| `--name <name>` | Price name | Yes |
| `--amount <amount>` | Price amount | Yes |
| `--type <type>` | Price type: `SUBSCRIPTION` or `ONETIME` | Yes |
| `--currency <currency>` | Currency code (e.g. `USD`, `EUR`, `GBP`) | No |
| `--interval-type <type>` | Billing interval: `YEARLY`, `MONTHLY`, or `WEEKLY` | No |
| `--interval-count <count>` | Number of intervals between billings | No |
| `--setup-fee-amount <amount>` | Setup fee amount | No |
| `--setup-fee-name <name>` | Setup fee name | No |
| `--setup-fee-enabled` | Enable setup fee | No |
| `--free-trial-enabled` | Enable free trial | No |
| `--free-trial-requires-card` | Require card for free trial | No |
| `--free-trial-days <days>` | Free trial duration in days | No |
| `--expiration-count <count>` | Expiration count | No |
| `--expiration-interval <interval>` | Expiration interval: `MONTHS` or `DAYS` | No |
| `--cancel-at-period-end` | Cancel at period end | No |

### Examples

```bash
memberstack prices create --plan-id pln_abc123 --name "Monthly" --amount 999 --type SUBSCRIPTION --interval-type MONTHLY

memberstack prices create \
  --plan-id pln_abc123 \
  --name "One-Time Access" \
  --amount 4999 \
  --type ONETIME

memberstack prices create \
  --plan-id pln_abc123 \
  --name "Annual Pro" \
  --amount 9999 \
  --type SUBSCRIPTION \
  --interval-type YEARLY \
  --free-trial-enabled \
  --free-trial-days 14
```

## prices update

Update a price.

```bash
memberstack prices update <priceId> [options]
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `priceId` | Price ID to update | Yes |

### Options

| Option | Description |
|---|---|
| `--name <name>` | Price name |
| `--amount <amount>` | Price amount |
| `--type <type>` | Price type: `SUBSCRIPTION` or `ONETIME` |
| `--currency <currency>` | Currency code |
| `--interval-type <type>` | Billing interval: `YEARLY`, `MONTHLY`, or `WEEKLY` |
| `--interval-count <count>` | Number of intervals between billings |
| `--setup-fee-amount <amount>` | Setup fee amount |
| `--setup-fee-name <name>` | Setup fee name |
| `--setup-fee-enabled` / `--no-setup-fee-enabled` | Enable or disable setup fee |
| `--free-trial-enabled` / `--no-free-trial-enabled` | Enable or disable free trial |
| `--free-trial-requires-card` | Require card for free trial |
| `--free-trial-days <days>` | Free trial duration in days |
| `--expiration-count <count>` | Expiration count |
| `--expiration-interval <interval>` | Expiration interval: `MONTHS` or `DAYS` |
| `--cancel-at-period-end` / `--no-cancel-at-period-end` | Cancel at period end |

### Examples

```bash
memberstack prices update prc_abc123 --name "Monthly Pro" --amount 1499
memberstack prices update prc_abc123 --free-trial-enabled --free-trial-days 7
memberstack prices update prc_abc123 --no-free-trial-enabled
```

## prices activate

Reactivate a price.

```bash
memberstack prices activate <priceId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `priceId` | Price ID to reactivate | Yes |

### Example

```bash
memberstack prices activate prc_abc123
```

## prices deactivate

Deactivate a price.

```bash
memberstack prices deactivate <priceId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `priceId` | Price ID to deactivate | Yes |

### Example

```bash
memberstack prices deactivate prc_abc123
```

## prices delete

Delete a price.

```bash
memberstack prices delete <priceId>
```

### Arguments

| Argument | Description | Required |
|---|---|---|
| `priceId` | Price ID to delete | Yes |

### Example

```bash
memberstack prices delete prc_abc123
```

## FAQ

Q: What price types are supported?
A: You can create SUBSCRIPTION or ONETIME prices. Subscription prices support interval billing (yearly, monthly, weekly) and free trials.

Q: How do I add a price to a plan?
A: Use memberstack prices create with --plan-id to specify which plan the price belongs to, along with --name, --amount, and --type.

Q: Can I deactivate a price without deleting it?
A: Yes. Use memberstack prices deactivate to deactivate a price. You can reactivate it later with memberstack prices activate.

