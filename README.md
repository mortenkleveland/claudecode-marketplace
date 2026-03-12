# Claude Code Marketplace

An internal plugin registry for sharing Claude Code skills, commands, and agents across teams.

## Available Plugins

| Plugin | Description | Skills | Commands | Agents |
|--------|-------------|--------|----------|--------|
| **android** | Android development | android | — | — |
| **backend** | Backend development | backend | — | — |
| **common** | Shared tools for all teams | git, jira | jira-ticket, pr-review | accessibility-reviewer, code-reviewer, designer, pr-writer, refactorer, security-reviewer |
| **data-analysis** | Data analysis & engineering | data | — | — |
| **ios** | iOS development | swiftui | — | — |
| **web** | Web frontend development | web | — | — |

## Getting Started

### 1. Add the marketplace (one-time)

```
/plugin marketplace add mortenkleveland/claudecode-marketplace
```

This registers the marketplace for your user — you only need to do this once.

### 2. Install plugins

Browse and install with `/plugin`, or install directly:

```
/plugin install common@claudecode-marketplace
/plugin install web@claudecode-marketplace
```

You'll be prompted to choose a scope:

| Scope | Who gets it | Stored in |
|-------|-------------|-----------|
| **User** | You, across all projects | `~/.claude/settings.json` |
| **Project** | Your whole team | `.claude/settings.json` (committed to git) |
| **Local** | You, in this repo only | `.claude/settings.local.json` (gitignored) |

**Tip**: Use **project** scope to share plugins with your team. Use **user** scope for personal defaults.

### 3. Verify

- Skills load into the system context automatically
- Commands: `/<plugin>:<command>` (e.g., `/common:pr-review 123`)
- Agents: Claude delegates to them automatically based on context

Run `/reload-plugins` to pick up changes without restarting.

## Plugin Structure

```
plugins/<name>/
├── .claude-plugin/
│   └── plugin.json      # Plugin manifest: name and description
├── agents/
│   └── <agent>.md       # Agent with frontmatter and system prompt
├── skills/
│   └── <skill>/
│       └── SKILL.md     # Skill definition with frontmatter and instructions
└── commands/
    └── <command>.md     # Command definition with arguments and steps
```

## Contributing

1. Create a directory under `plugins/` with the structure above
2. Write a `plugin.json` manifest in `.claude-plugin/`
3. Add skills, commands, and/or agents
4. Register the plugin in `.claude-plugin/marketplace.json`
5. Open a PR for review

## License

MIT
