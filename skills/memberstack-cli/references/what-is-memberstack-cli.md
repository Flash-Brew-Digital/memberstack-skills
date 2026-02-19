---
title: What is Memberstack CLI
description: An open source command-line tool for managing your Memberstack account. Handle apps, members, plans, data tables, custom fields, and agent skills from the terminal.
tags: ["memberstack", "cli", "what-is", "overview", "open-source", "command-line"]
---

**Memberstack CLI** is an open source command-line tool that lets you manage your Memberstack account from the terminal. Apps, members, plans, data tables, custom fields, and agent skills: everything you do in the dashboard, you can do from the command line.

## Why use a CLI?

The Memberstack dashboard handles day-to-day tasks well. But when you need to work at scale (bulk imports, automated workflows, scripted operations), a web UI slows you down.

The CLI gives you:

- **Speed.** Run a command and get results. No clicking through pages.
- **Automation.** Script member imports, plan updates, and data migrations. Combine with cron jobs, CI/CD pipelines, or shell scripts.
- **Bulk operations.** Import and export members and records in CSV or JSON. Create, update, or delete in bulk with dry-run previews.
- **AI agent support.** Works with OpenAI Codex, Claude Code, Gemini CLI, GitHub Copilot, Cursor, and dozens of other agents. Install the [Agent Skills](/docs/agent-skills) so your agent knows how to use the CLI.

## How it works

The CLI authenticates through OAuth in your browser, no API keys to manage. Your tokens are stored locally at `~/.memberstack/auth.json` with restricted file permissions and never leave your machine.

Every command targets your **sandbox** environment (test mode) by default. Add `--live` when you're ready to work with production data (live mode).

```bash
memberstack members list --all           # sandbox (test mode)
memberstack members list --all --live    # production (live mode)
```

## What you can do

| Area | Examples |
|---|---|
| **Members** | List, create, update, delete, import/export, bulk operations |
| **Plans** | List, create, update, delete, reorder |
| **Apps** | View current app, create, update, delete, restore |
| **Data tables** | List, create, update, delete, describe schema |
| **Records** | CRUD, query, import/export, bulk operations |
| **Custom fields** | List, create, update, delete |
| **Skills** | Add and remove agent skills for Claude Code and Codex |

## Who built this?

Memberstack CLI is an open source, community project by Ben Sabic from Flash Brew Digital. It is not affiliated with or endorsed by Memberstack. Contributions are welcome on GitHub.
