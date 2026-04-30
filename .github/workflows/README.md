# Agentic Workflow Templates

This directory contains GitHub Agentic Workflow source files. The editable source of truth is the `.md` file. After changing frontmatter, compile it with `gh-aw` to generate the matching `.lock.yml`.

## Files

- `agentic-roblox-dev.md`: Roblox development workflow for project health, feature work, bug fixes, review, testing notes, and docs sync.
- `agentic-roblox-dev.lock.yml`: generated file to create with `gh aw compile agentic-roblox-dev`.

## Enable The Roblox Workflow

1. Install GitHub CLI and the extension:

   ```bash
   gh extension install github/gh-aw
   ```

2. From the repository root, compile the Roblox workflow:

   ```bash
   gh aw compile agentic-roblox-dev
   ```

3. Commit both the source and generated workflow:

   ```bash
   git add .gitattributes .github/workflows/agentic-roblox-dev.md .github/workflows/agentic-roblox-dev.lock.yml
   git commit -m "Add Roblox agentic development workflow"
   ```

## Slash Command

After the compiled workflow is merged, use this in a GitHub issue or pull request comment:

```text
/roblox-dev review this remote handling and suggest safer validation
```

## Customize

- Change markdown body instructions freely; those changes do not require recompilation.
- Re-run `gh aw compile agentic-roblox-dev` after changing triggers, permissions, tools, network, or `safe-outputs`.
- Keep the agent permissions read-only and route GitHub writes through `safe-outputs`.
- Add network access only for specific ecosystems or domains needed by your Roblox workflow.
