# agent-roblox

Roblox-focused GitHub Agentic Workflow template. Use it as a starting point for AI-assisted Roblox development workflows built on `gh-aw`.

## What It Provides

- A `gh-aw` source workflow for Roblox project health checks, feature work, bug fixes, PR review, test planning, docs sync, and custom tasks.
- A `/roblox-dev` slash command for GitHub issues and pull requests.
- Draft PR output for small code, test, or documentation changes.
- PR review output for Roblox-specific review findings.
- Safe boundaries: the agent runs read-only and requests writes through `safe-outputs`.

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

Then commit the generated lock file:

```bash
git add .gitattributes .github/workflows/agentic-roblox-dev.md .github/workflows/agentic-roblox-dev.lock.yml
git commit -m "Compile Roblox agentic workflow"
git push
```

## Slash Command Examples

```text
/roblox-dev project-health
/roblox-dev review this inventory remote and suggest safer validation
/roblox-dev create a test plan for ServerScriptService.InventoryService
/roblox-dev fix the cooldown bypass described above
```

## Design Goals

- Keep Roblox server logic authoritative.
- Treat client remote calls as untrusted.
- Preserve existing Rojo, Wally, Aftman, Selene, StyLua, and TestEZ patterns.
- Make small reviewable draft PRs instead of broad rewrites.
- Avoid editing Roblox place/model files unless a human explicitly handles Studio-side asset changes.
