# Workflow Selection Guide

Use this guide to choose the smallest workflow that fits the job.

## Start Here

| Need | Use |
| --- | --- |
| Unsure what to run | `agentic-roblox-dev.md` |
| Classify a new report | `agentic-roblox-triage.md` |
| Review a pull request | `agentic-roblox-pr-review.md` |
| Implement a small change | `agentic-roblox-implementer.md` |
| Audit project readiness | `agentic-roblox-health.md` |
| Update README or docs | `agentic-roblox-docs.md` |

## Workflow Roles

### General Developer

`agentic-roblox-dev.md` is the broad starter. Use it when a project is young, when you want one command, or when you are still learning which specialized workflows are worth enabling.

### Triage

`agentic-roblox-triage.md` is for issue intake. It labels reports and asks for missing reproduction context. It should not create code changes.

### PR Review

`agentic-roblox-pr-review.md` is for pull request review. It focuses on Roblox correctness risks: server authority, remotes, DataStore safety, lifecycle cleanup, tests, and performance.

### Implementer

`agentic-roblox-implementer.md` is for small, reviewable draft PRs. It is intentionally narrow and excludes Roblox binary assets.

### Health

`agentic-roblox-health.md` is for weekly or manual audits. It creates one focused issue with risks and next actions.

### Docs

`agentic-roblox-docs.md` is for README/docs synchronization. It only edits Markdown documentation paths.

## Suggested Rollout

1. Enable `agentic-roblox-dev.md`.
2. Add `agentic-roblox-health.md` once the repository has real source structure.
3. Add `agentic-roblox-pr-review.md` when PR traffic starts.
4. Add `agentic-roblox-triage.md` when issues are public or frequent.
5. Add `agentic-roblox-implementer.md` after the team is comfortable reviewing draft PRs.
6. Add `agentic-roblox-docs.md` once README/docs drift becomes noticeable.
