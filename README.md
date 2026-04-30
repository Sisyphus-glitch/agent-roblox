# agent-roblox

Roblox-focused GitHub Agentic Workflow template. This repository is meant to be a starting point for building your own AI-assisted Roblox development workflows.

## What It Provides

- A `gh-aw` source workflow for Roblox development tasks.
- Manual runs for project health, feature implementation, bug fixing, code review, test planning, docs sync, and custom instructions.
- A `/roblox-dev` slash command for GitHub issues and pull requests.
- Safe output boundaries: the agent can propose issues, comments, or pull requests, while the workflow job remains read-only.

## Workflow

Source file:

```text
.github/workflows/agentic-roblox-dev.md
```

Compile it with:

```bash
gh extension install github/gh-aw
gh aw compile agentic-roblox-dev
```

Then commit the source and generated lock file:

```bash
git add .gitattributes .github/workflows/agentic-roblox-dev.md .github/workflows/agentic-roblox-dev.lock.yml
git commit -m "Add Roblox agentic development workflow"
```

## Slash Command Example

```text
/roblox-dev review this inventory remote and suggest safer validation
```

## Design Goals

- Keep Roblox server logic authoritative.
- Treat client remote calls as untrusted.
- Preserve the repository's existing Rojo, Wally, Aftman, Selene, StyLua, and TestEZ patterns.
- Make small reviewable pull requests instead of broad rewrites.
- Avoid editing binary Roblox assets unless explicitly requested.
