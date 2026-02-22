---
title: Update
description: Update the Memberstack CLI to the latest version.
tags: ["memberstack", "cli", "update", "upgrade", "version"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack update
```

## update

Update the Memberstack CLI to the latest version.

```bash
memberstack update
```

### Description

Detects your package manager (npm, pnpm, yarn, or bun) and runs the appropriate global install command to update to the latest version. The current version and detected package manager are displayed before the update begins.

### Example

```bash
$ memberstack update

  Current version: 1.2.0
  Package manager: npm

✔ Successfully updated Memberstack CLI. Run "memberstack --version" to verify.
```

## FAQ

Q: How do I update the Memberstack CLI?
A: Run memberstack update. The CLI detects your package manager (npm, pnpm, yarn, or bun) and runs the appropriate global install command automatically.

Q: Which package managers are supported?
A: The update command supports npm, pnpm, yarn, and bun. It auto-detects which one you used to install the CLI and runs the correct update command.

