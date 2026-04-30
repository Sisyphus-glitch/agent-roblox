# Setup Guide

Use this guide to install the Roblox workflow templates into a target repository.

## Prerequisites

- GitHub CLI installed and authenticated.
- `gh-aw` extension installed.
- A target repository where GitHub Actions is enabled.
- Permission to push workflow files and configure repository labels.

Install `gh-aw`:

```bash
gh extension install github/gh-aw
```

## Minimal Setup

Start with the general-purpose workflow:

```bash
cp .github/workflows/agentic-roblox-dev.md <target-repo>/.github/workflows/
cd <target-repo>
gh aw compile agentic-roblox-dev
git add .github/workflows/agentic-roblox-dev.md .github/workflows/agentic-roblox-dev.lock.yml
git commit -m "Add Roblox agentic workflow"
git push
```

## Full Template Pack

Copy every workflow variant:

```bash
cp .github/workflows/agentic-roblox-*.md <target-repo>/.github/workflows/
cd <target-repo>
gh aw compile
git add .github/workflows/agentic-roblox-*.md .github/workflows/agentic-roblox-*.lock.yml
git commit -m "Add Roblox agentic workflow pack"
git push
```

## Recommended Repository Labels

Create the labels listed in [labels.md](labels.md) before enabling `agentic-roblox-triage.md`.

## After Install

1. Open the Actions tab and confirm compiled `.lock.yml` workflows appear.
2. Test with a manual dispatch before relying on slash commands.
3. Open a test issue and run `/roblox-health overall`.
4. Review the first generated issue/comment/PR before enabling scheduled workflows broadly.

## Compile Notes

- Edit `.md` files as the source of truth.
- Re-run `gh aw compile` after frontmatter changes.
- Markdown body-only prompt edits usually do not require recompilation.
- Commit both `.md` and `.lock.yml` files.
