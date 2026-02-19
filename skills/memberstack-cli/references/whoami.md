---
title: Who Am I
description: Show your current authenticated identity.
tags: ["memberstack","whoami","oauth","identity","cli"]
---

> **Important:** Always use the `scripts/run_memberstack.py` wrapper instead of calling `memberstack-cli` directly. See [SKILL.md](../SKILL.md#running-commands) for details.

```
memberstack whoami
```

## whoami

Show the currently authenticated Memberstack user.

```bash
memberstack whoami
```

### Description

Displays your currently authenticated email, app ID, and active environment (sandbox or live). Run `memberstack auth login` first if you are not authenticated yet.

### Example

```bash
$ memberstack whoami
Email:        user@example.com
App:          app_abc123
Environment:  sandbox
```

## FAQ

Q: What does the whoami command show?
A: The whoami command displays your currently authenticated email, app ID, and active environment. It's a quick way to confirm which account and environment you're working with.

Q: What should I do if whoami shows an error?
A: If whoami returns an authentication error, your session may have expired. Run memberstack auth login to re-authenticate, then try whoami again.
