---
title: What is Memberstack CLI
description: An open-source command-line tool for managing your Memberstack account. Handle apps, members, plans, data tables, custom fields, and more from the terminal.
tags: ["memberstack", "cli", "what-is", "overview", "open-source", "command-line"]
---

**Memberstack CLI** is an open-source command-line tool that lets you manage your Memberstack account from the terminal. From apps to members to plans to permissions: everything you do in the dashboard, you can do from the command line.

## Why use a CLI?

The Memberstack dashboard handles day-to-day tasks well. But when you need to work at scale (bulk imports, automated workflows, scripted operations), a web UI slows you down.

The CLI gives you:

- **Speed.** Run a command and get results. No clicking through pages.
- **Automation.** Script member imports, plan updates, and data migrations. Combine with cron jobs, CI/CD pipelines, or shell scripts.
- **Bulk operations.** Import and export members and records in CSV or JSON. Create, update, or delete in bulk with dry-run previews.
- **AI agent support.** Works with OpenAI Codex, Claude Code, Gemini CLI, GitHub Copilot, Cursor, and dozens of other agents. Install the [Agent Skills](/docs/agent-skills) so your agent knows how to use the CLI.

## How it works

The CLI authenticates through OAuth in your browser, no API keys to manage. Your tokens are stored locally at `~/.memberstack/auth.json` with restricted file permissions and never leave your machine.

Every command targets your **sandbox** environment (test mode) by default. Use `--mode live` or the `--live` shorthand when you're ready to work with your live environment. See [Global Options](/docs/global-options) for all available flags.

```bash
memberstack members list --all           # sandbox (test mode)
memberstack members list --all --live    # live
```

## What you can do

| Area | Examples |
|---|---|
| **Members** | List, create, update, delete, import/export, bulk operations |
| **Plans** | List, create, update, delete, reorder |
| **Prices** | Create, update, activate, deactivate, delete |
| **Apps** | View current app, create, update, delete, restore |
| **Data tables** | List, create, update, delete, describe schema |
| **Records** | CRUD, query, import/export, bulk operations |
| **Custom fields** | List, create, update, delete |
| **Permissions** | List, create, update, delete, link/unlink to plans and members |
| **Auth providers** | List, configure, remove (Google, GitHub, Facebook, and more) |
| **SSO** | List, create, update, delete SSO apps |
| **Users** | List, get, add, remove, update roles |
| **Skills** | Add and remove agent skills for Claude Code and Codex |

## Why not MCP?

Model Context Protocol (MCP) is the standard for connecting AI agents to external tools. It works, but it comes with trade-offs that a CLI avoids.

- **Context bloat.** MCP servers load every tool definition into the agent's context window upfront. A single server can burn thousands of tokens before the agent even reads your request. Anthropic's own engineering team documented setups where tool definitions consumed 134,000 tokens before optimization.
- **CLIs are nearly free.** A CLI command and its `--help` output cost a few hundred tokens. The same operation as an MCP tool definition costs thousands. That's context your agent can spend on solving problems, not reading schemas.
- **Agents are built for terminals.** Claude Code, Codex, Gemini CLI, Cursor, Copilot — they all run shell commands natively. No server to keep running, no protocol layer. The agent reads the docs, runs the command, and parses the output.
- **No infrastructure.** MCP servers need to be installed, configured, and kept alive. A CLI is a single install. Authenticate once and every agent on your machine can use it immediately.

## Who built this?

Memberstack CLI is an open-source, community project by Ben Sabic from Flash Brew Digital. It is not affiliated with or endorsed by Memberstack. Contributions are welcome on GitHub.

