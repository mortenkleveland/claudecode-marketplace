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

### 1. Clone the marketplace

```bash
git clone <repo-url> ~/claudecode-marketplace
```

### 2. Install plugins in your repo

Add plugin paths to your **repo's** `.claude/settings.json` so the whole team gets them:

```json
{
  "plugins": [
    "/absolute/path/to/claudecode-marketplace/plugins/common",
    "/absolute/path/to/claudecode-marketplace/plugins/web"
  ]
}
```

Commit `.claude/settings.json` to your repo so all team members share the same plugin set.

### 3. Verify

Open Claude Code in your project and check that skills and commands are available:

- Skills should appear in the system context automatically
- Commands can be invoked with `/<command-name>` (e.g., `/pr-review 123`)

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
4. Register the plugin in `marketplace.json`
5. Open a PR for review

## License

MIT
