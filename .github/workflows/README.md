# Agentic Workflow Templates

This directory contains GitHub Agentic Workflow source files. The editable source of truth is the `.md` file. After changing frontmatter, compile it with `gh-aw` to generate the matching `.lock.yml`.

## Files

- `agentic-roblox-dev.md`: Roblox development workflow for project health, feature work, bug fixes, PR review, test planning, and docs sync.
- `agentic-roblox-dev.lock.yml`: generated file to create with `gh aw compile agentic-roblox-dev`.

## Enable The Roblox Workflow

1. Install GitHub CLI and the extension:

   ```bash
   gh extension install github/gh-aw
   ```

2. From the repository root, compile the workflow:

   ```bash
   gh aw compile agentic-roblox-dev
   ```

3. Commit both the source and generated workflow:

   ```bash
   git add .gitattributes .github/workflows/agentic-roblox-dev.md .github/workflows/agentic-roblox-dev.lock.yml
   git commit -m "Compile Roblox agentic workflow"
   ```

## Slash Command

After the compiled workflow is merged, use this in a GitHub issue or pull request comment:

```text
/roblox-dev review this inventory remote and suggest safer validation
```

Useful examples:

```text
/roblox-dev project-health
/roblox-dev create a test plan for ServerScriptService.InventoryService
/roblox-dev fix the cooldown bypass described above
/roblox-dev review this pull request for RemoteEvent validation
```

## Safety Shape

- The agent job keeps GitHub permissions read-only.
- Writes happen through `safe-outputs`: issues, comments, draft PRs, and PR review comments.
- Generated PRs exclude Roblox place/model files, build output, and lock files by default.
- The workflow ignores common bot triggers and only allows users with write-level repository access or higher.
- Re-run `gh aw compile agentic-roblox-dev` after changing triggers, permissions, tools, network, or `safe-outputs`.
