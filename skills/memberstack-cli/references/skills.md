---
title: Skills
description: Add and remove Memberstack agent skills from the CLI.
tags: ["memberstack", "skills", "agent", "cli", "claude", "codex"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack skills <subcommand> [options]
```

## skills add

Add a Memberstack agent skill to your project.

```bash
memberstack skills add <skill>
```

### Example

```bash
memberstack skills add memberstack-cli
```

## skills remove

Remove a Memberstack agent skill from your project.

```bash
memberstack skills remove <skill>
```

### Example

```bash
memberstack skills remove memberstack-cli
```

## Available Skills

| Skill | Description |
|---|---|
| `memberstack-cli` | Teaches your AI agent how to use the Memberstack CLI |
| `memberstack-admin-api` | Teaches your AI agent the Memberstack Admin REST API |

## FAQ

Q: What does the skills command do?
A: It wraps the skills CLI to add or remove Memberstack agent skills.

Q: Which agents are supported?
A: Skills are installed to .agents/ and .claude/, so they work with any agent that supports loading skills from those directories.

Q: Do I need to install anything extra?
A: No. The command uses npx behind the scenes, so the skills CLI is fetched automatically.
