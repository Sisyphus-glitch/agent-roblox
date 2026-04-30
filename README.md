# agent-roblox

Roblox-focused GitHub Agentic Workflow template library. Use it as a starting point for AI-assisted Roblox development workflows built on `gh-aw`.

## Workflow Variants

| Workflow | Command | Best For | Output |
| --- | --- | --- | --- |
| `agentic-roblox-dev.md` | `/roblox-dev` | General-purpose Roblox development agent | Issue, comment, draft PR, PR review |
| `agentic-roblox-triage.md` | `/roblox-triage` | Classifying Roblox bug reports and asking for missing repro details | Labels and issue comment |
| `agentic-roblox-pr-review.md` | `/roblox-review` | Reviewing Roblox PRs for remotes, authority, DataStore, tests, and performance | PR review and line comments |
| `agentic-roblox-implementer.md` | `/roblox-implement` | Small feature, bug-fix, test, docs, or refactor PRs | Draft PR |
| `agentic-roblox-health.md` | `/roblox-health` | Weekly or manual project readiness checks | Health issue or comment |
| `agentic-roblox-docs.md` | `/roblox-docs` | Keeping README/docs aligned with project layout and tooling | Draft docs PR |

## Recommended Setup

Start with the general workflow:

```bash
gh extension install github/gh-aw
gh aw compile agentic-roblox-dev
```

For a more mature repository, compile all variants:

```bash
gh aw compile
git add .gitattributes .github/workflows/*.md .github/workflows/*.lock.yml README.md docs/open-source-patterns.md
git commit -m "Add Roblox agentic workflow variants"
git push
```

## Example Commands

```text
/roblox-dev project-health
/roblox-triage
/roblox-review review this pull request for RemoteEvent validation
/roblox-implement fix the cooldown bypass described above
/roblox-health networking
/roblox-docs update onboarding docs for Rojo and Wally
```

## Design Goals

- Keep Roblox server logic authoritative.
- Treat client remote calls as untrusted.
- Preserve existing Rojo, Wally, Aftman, Selene, StyLua, and TestEZ patterns.
- Make small reviewable draft PRs instead of broad rewrites.
- Exclude Roblox place/model/binary files from automated PRs by default.
- Convert Studio-only work into issues, comments, or manual QA steps.

## Pattern Notes

See [docs/open-source-patterns.md](docs/open-source-patterns.md) for the open-source `gh-aw` patterns used to shape these templates.
