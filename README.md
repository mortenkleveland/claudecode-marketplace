# Claude Code Marketplace

An internal plugin registry for sharing Claude Code skills and commands across teams.

## Available Plugins

| Plugin | Description | Skills | Commands |
|--------|-------------|--------|----------|
| **common** | Shared tools for all teams | jira, git | pr-review, jira-ticket |
| **ios** | iOS development | swiftui | — |
| **android** | Android development | android | — |
| **backend** | Backend development | backend | — |
| **web** | Web frontend development | web | — |
| **data-analysis** | Data analysis & engineering | data | — |

## Setup

### 1. Add the marketplace

In Claude Code, add this repo as a marketplace source:

```
/plugin marketplace add mortenkleveland/claudecode-marketplace
```

### 2. Install plugins

Browse available plugins with `/plugin`, or install directly:

```
/plugin install common@claudecode-marketplace
/plugin install web@claudecode-marketplace
```

Choose the installation scope when prompted:
- **Project** — shared with collaborators via `.claude/settings.json` (recommended for teams)
- **User** — available across all your projects
- **Local** — only for you in this repo

### 3. Verify

Skills should appear in the system context automatically. Commands can be invoked with `/<plugin>:<command>` (e.g., `/common:pr-review 123`).

Run `/reload-plugins` to pick up changes without restarting.

## Plugin Structure

Each plugin follows this structure:

```
plugins/<name>/
├── .claude-plugin/
│   └── plugin.json      # Plugin manifest: id, name, description, file references
├── skills/
│   └── <skill>.md       # Skill definition with frontmatter and instructions
└── commands/
    └── <command>.md     # Command definition with arguments and steps
```

## Adding a New Plugin

1. Create a directory under `plugins/` with the structure above
2. Write a `plugin.json` manifest in `.claude-plugin/`
3. Add skills and/or commands
4. Register the plugin in `.claude-plugin/marketplace.json`
5. Open a PR for review

## License

MIT
