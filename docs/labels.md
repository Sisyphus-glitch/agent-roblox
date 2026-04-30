# Labels

`agentic-roblox-triage.md` can add these labels. Create them in target repositories before enabling the triage workflow.

| Label | Purpose |
| --- | --- |
| `bug` | Defect or broken behavior |
| `enhancement` | Feature or improvement request |
| `documentation` | README, docs, onboarding, or instructions |
| `question` | Needs clarification or answer |
| `help-wanted` | Maintainer wants outside help |
| `good-first-issue` | Small scoped task suitable for a newcomer |
| `needs-repro` | Bug report lacks reproduction steps or environment details |
| `roblox-studio` | Requires Studio inspection or manual Studio steps |
| `luau` | Luau source, typing, linting, or runtime issue |
| `networking` | Remotes, replication, matchmaking, latency, or client/server boundary |
| `datastore` | DataStore, persistence, migrations, rollback, or data loss |
| `ui` | StarterGui, ScreenGui, input device, viewport, or interaction issue |
| `performance` | Frame time, memory, unbounded loops, physics, streaming, or allocations |
| `testing` | TestEZ, Studio QA, regression coverage, or verification plan |

## Create Labels With GitHub CLI

```bash
gh label create needs-repro --description "Needs reproduction steps or environment details" --color BFD4F2
gh label create roblox-studio --description "Requires Roblox Studio inspection or manual steps" --color 7057FF
gh label create luau --description "Luau source, typing, linting, or runtime issue" --color 1D76DB
gh label create networking --description "Remotes, replication, matchmaking, latency, or client/server boundary" --color D93F0B
gh label create datastore --description "Persistence, migrations, rollback, or data loss" --color B60205
gh label create ui --description "Roblox UI, input, viewport, or interaction issue" --color C5DEF5
gh label create performance --description "Frame time, memory, loops, streaming, or allocation concern" --color FBCA04
gh label create testing --description "TestEZ, Studio QA, regression coverage, or verification plan" --color 0E8A16
```

Default GitHub labels such as `bug`, `enhancement`, `documentation`, `question`, `help-wanted`, and `good-first-issue` may already exist.
