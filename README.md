# Flash Brew Digital - Memberstack Agent Skills

![Flash Brew Digital OSS](https://img.shields.io/badge/Flash_Brew_Digital-OSS-6F4E37?style=for-the-badge&labelColor=E9E3DD)
![MIT License](https://img.shields.io/badge/License-MIT-6F4E37?style=for-the-badge&labelColor=E9E3DD)

This repository contains a collection of Memberstack Agent Skills by Flash Brew Digital. These skills are designed to enhance the capabilities of agents by providing them with specialized functionalities.

## What are Agent Skills?

Agent Skills are folders of instructions, scripts, and resources that agents can discover and use to do things more accurately and efficiently. They work across any AI agent that supports the [open Agent Skills standard](https://agentskills.io).

## Available Skills
<!-- START:Available-Skills -->
| Skill | Description |
| ----- | ----------- |
| [memberstack-admin-api](./skills/memberstack-admin-api) | Work with the Memberstack Admin API to manage members, plans, and data tables... |
| [memberstack-cli](./skills/memberstack-cli) | Use the Memberstack CLI to manage Memberstack accounts from the terminal. Cov... |
<!-- END:Available-Skills -->

## Installation

### Memberstack CLI

Use the [Memberstack CLI](https://memberstack-cli.flashbrew.digital) to add and remove skills directly:

```bash
# Add a skill
memberstack skills add memberstack-cli

# Remove a skill
memberstack skills remove memberstack-cli
```

### Claude Code Plugin

Install via Claude Code's plugin system:

```bash
# Add the marketplace
/plugin marketplace add Flash-Brew-Digital/memberstack-skills

# Install specific skill
/plugin install memberstack-cli-skill
```

> Claude Code plugins are also supported in Factory's [Droid](https://docs.factory.ai/cli/configuration/plugins#claude-code-compatibility).

### Other Installation Methods

Skills can also be installed using [skills](https://skills.sh/), [Playbooks](https://playbooks.com/skills), or [Context7](https://context7.com/docs/skills):

```bash
# Skills CLI
npx skills add Flash-Brew-Digital/memberstack-skills

# Playbooks
npx playbooks add skill Flash-Brew-Digital/memberstack-skills

# Context7
npx ctx7 skills install /Flash-Brew-Digital/memberstack-skills
```

## Adding New Skills

Use the included script to add new skills:

```bash
node scripts/add-skill.js <skill-name> "<description>"
```

Example:

```bash
node scripts/add-skill.js memberstack-dom-package "Work with the Memberstack DOM Package..."
```

This will create the skill structure and automatically update this README and the marketplace.json.

## Scripts

| Script | Description |
| ------ | ----------- |
| `node scripts/add-skill.js` | Add a new skill to the repository |
| `node scripts/sync-skills.js` | Sync README and marketplace.json with skills directory |

## Resources

- [Memberstack CLI Documentation](https://memberstack-cli.flashbrew.digital)
- [Agent Skills Specification](https://agentskills.io/specification)
- [npx skills](https://skills.sh/)
- [Validate Agent Skill](https://github.com/marketplace/actions/validate-skill)
- [Playbooks](https://playbooks.com/skills)
- [Context7 Skills](https://context7.com/docs/skills)

## Contributing

Contributions are welcome! Please read our [Contributing Guide](.github/CONTRIBUTING.md) for more information.

## License

[MIT License](LICENSE)

## Author

[Ben Sabic](https://bensabic.dev) at [Flash Brew Digital](https://flashbrew.digital)