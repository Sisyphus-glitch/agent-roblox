# Agentic Workflow Templates

This directory contains GitHub Agentic Workflow source files. The editable source of truth is each `.md` file. After changing frontmatter, compile with `gh-aw` to generate matching `.lock.yml` files.

## Files

- `agentic-roblox-dev.md`: general-purpose Roblox development workflow.
- `agentic-roblox-triage.md`: issue classification and missing-repro workflow.
- `agentic-roblox-pr-review.md`: PR review workflow focused on Roblox correctness risks.
- `agentic-roblox-implementer.md`: small implementation and bug-fix draft PR workflow.
- `agentic-roblox-health.md`: scheduled/manual project health workflow.
- `agentic-roblox-docs.md`: README/docs synchronization workflow.

## Compile

Compile one workflow:

```bash
gh aw compile agentic-roblox-dev
```

Compile every workflow in this directory:

```bash
gh aw compile
```

Commit both source and generated lock files:

```bash
git add .github/workflows/*.md .github/workflows/*.lock.yml
git commit -m "Compile Roblox agentic workflows"
```

## Slash Commands

```text
/roblox-dev project-health
/roblox-triage
/roblox-review review this pull request for RemoteEvent validation
/roblox-implement fix the cooldown bypass described above
/roblox-health datastore
/roblox-docs update setup instructions
```

## Safety Shape

- Agent jobs keep GitHub permissions read-only.
- Writes happen through `safe-outputs`: labels, comments, issues, draft PRs, and PR review comments.
- Automated PRs exclude Roblox place/model files, build output, and lock files unless a specialized workflow says otherwise.
- Common bot triggers are skipped.
- Maintainer/write-level role gates are enabled by default.
- Re-run `gh aw compile` after changing triggers, permissions, tools, network, or `safe-outputs`.

## Labels

`agentic-roblox-triage.md` can add labels such as `bug`, `needs-repro`, `networking`, `datastore`, and `testing`. Create or customize these labels in your target repository before enabling the triage variant.
