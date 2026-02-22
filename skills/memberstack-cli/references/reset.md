---
title: Reset
description: Delete local data files and clear authentication.
tags: ["memberstack", "cli", "reset", "clear", "logout", "cleanup"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack reset [options]
```

## reset

Delete local data files and clear authentication.

```bash
memberstack reset [options]
```

### Description

Removes locally generated data files (`members.json`, `members.csv`) if they exist in the current directory and clears your stored authentication tokens. A confirmation prompt is shown before any changes are made.

### Options

| Option | Alias | Description |
|---|---|---|
| `--force` | `-f` | Skip confirmation prompt |

### Example

```bash
$ memberstack reset

  This will:
    - Delete members.json, members.csv (if present)
    - Clear stored authentication tokens

  Continue? (y/n) y

✔ Deleted members.json
✔ Cleared authentication tokens
```

### Force reset

```bash
memberstack reset --force
```

## FAQ

Q: What does the reset command do?
A: It deletes local data files (members.json, members.csv) if they exist and clears your stored authentication tokens. You will need to run memberstack auth login again after resetting.

Q: Can I skip the confirmation prompt?
A: Yes. Use the --force flag to skip the confirmation prompt and reset immediately.

