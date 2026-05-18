# Project Configuration Guide

This skill stores project-specific context in `skill/worktrees.json` (gitignored).
All git-tracked skill files are project-agnostic.

## File Separation

```
.claude/skills/playwright-skill/
├── SKILL.md                    # Tracked — generic, no project data
├── bin/                        # Tracked — generic wrapper scripts
├── skill/
│   ├── CONFIG.md               # Tracked — this file, setup guide
│   ├── REFERENCE.md            # Tracked — generic command reference
│   ├── AUTH.md                 # Tracked — generic auth patterns
│   ├── INSTALL.md              # Tracked — setup instructions
│   ├── worktrees.example.json  # Tracked — schema + template
│   └── worktrees.json          # NOT tracked — your project data ← create this
└── .playwright-skill/
    └── auth/                   # NOT tracked — session tokens
```

## Setup

Copy the example and customize for your project:

```bash
cp skill/worktrees.example.json skill/worktrees.json
```

## worktrees.json Schema

```json
{
  "description": "Your project name — worktree configuration",

  "worktrees": {
    "<worktree-name>": {
      "baseUrl": "https://your-app.test",
      "branch": "develop",
      "description": "Human-readable description",
      "auth": {
        "defaultUser": "admin@example.com",
        "roles": {
          "<role-name>": "<email-or-username>"
        },
        "notes": "Optional notes about auth quirks"
      },
      "authProfiles": ["<profile-a>", "<profile-b>"],
      "notes": ["Optional array of known quirks or patterns"]
    }
  },

  "detection": {
    "method": "directory-name",
    "fallback": "<default-worktree-name>",
    "notes": "Worktree detected from the last path component of your working directory"
  }
}
```

### Key fields

| Field | Required | Description |
|-------|----------|-------------|
| `worktrees.<name>.baseUrl` | Yes | App base URL for this environment |
| `worktrees.<name>.auth.roles` | Yes | Map of role name → username |
| `worktrees.<name>.authProfiles` | No | Named auth profiles (for `bin/auth-save/load`) |
| `detection.fallback` | Yes | Default worktree when detection fails |

### authProfiles vs auth.roles

- `auth.roles` documents who can log in with what identity (informational)
- `authProfiles` lists the saved session profile names used with `bin/auth-save <name>` / `bin/auth-load <name>`

Profile names can match role names (convenient) or differ (e.g., one profile per role × environment).

## Project-Specific Selector Patterns

If your app has framework-specific selectors that the generic `bin/` wrappers need to target, document them here so Claude knows what patterns to use:

```json
{
  "selectorPatterns": {
    "modal.confirm": "[data-modal-confirm]",
    "modal.close": "button[data-dismiss]",
    "fileInput": "input[type=file]",
    "notes": "Framework-specific selector patterns for this project"
  }
}
```

Or simply add a `notes` section to your worktree entry:

```json
{
  "worktrees": {
    "my-app": {
      "baseUrl": "...",
      "notes": [
        "Modals use [data-modal-confirm] for confirm buttons",
        "File inputs are hidden — target via input[type=file]",
        "Some components require CSS selector clicks to fire framework event handlers"
      ]
    }
  }
}
```

## Browser Launch Configuration

`playwright-cli` reads optional browser launch arguments from `.playwright/cli.config.json` in the skill root. This is useful for local dev environments that need special flags:

```json
{
  "browser": {
    "launchOptions": {
      "args": [
        "--host-resolver-rules=MAP *.test 127.0.0.1",
        "--ignore-certificate-errors"
      ]
    }
  }
}
```

Common use cases:
- `--host-resolver-rules=MAP *.test 127.0.0.1` — resolve `.test` TLDs to localhost (Herd / Valet / dnsmasq)
- `--ignore-certificate-errors` — bypass self-signed cert warnings in local dev

This file is gitignored (environment-specific). Create it if your local setup needs it.

## Gitignore

The following are already gitignored by the skill:

```gitignore
skill/worktrees.json          # project-specific config
.playwright-skill/auth/       # saved session tokens
.playwright-skill/cache/      # runtime cache data
.playwright-skill/sessions/   # session state
.playwright/                  # browser launch config (environment-specific)
```

## Security Notes

- **Never store passwords** in `worktrees.json` — use `bin/auth-save` / `bin/auth-load` for credential persistence
- `worktrees.json` may contain usernames, which some teams consider sensitive — gitignore it regardless
- Auth profiles in `.playwright-skill/auth/` contain session tokens — always gitignored
