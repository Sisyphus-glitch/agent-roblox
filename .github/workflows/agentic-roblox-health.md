---
description: "Weekly Roblox project health workflow that reports readiness, quality, and maintenance risks."
labels: ["roblox", "project-health", "maintenance"]
metadata:
  version: "0.1.0"
  category: "roblox-health"
on:
  schedule:
    - cron: "0 2 * * 1"
  workflow_dispatch:
    inputs:
      focus:
        description: "Optional health focus."
        required: false
        type: choice
        options:
          - overall
          - tooling
          - networking
          - datastore
          - tests
          - docs
          - performance
        default: overall
  slash_command:
    name: roblox-health
    events: [issues, issue_comment, pull_request, pull_request_review_comment]
  roles: [admin, maintainer, write]
  skip-bots: [github-actions, copilot, dependabot, renovate]
strict: true
permissions:
  contents: read
  issues: read
  pull-requests: read
  actions: read
tools:
  github:
    toolsets: [context, repos, issues, pull_requests, actions]
  bash:
    - ls
    - find
    - grep
    - rg
    - cat
    - sed
    - awk
    - wc
    - sort
    - uniq
    - git log
    - git show
network:
  allowed:
    - defaults
safe-outputs:
  create-issue:
    title-prefix: "[roblox-health] "
    max: 1
    close-older-issues: true
  add-comment:
    max: 1
    target: triggering
    discussions: false
  missing-data:
    create-issue: false
    max: 1
---

# Roblox Project Health

Produce a focused health report for a Roblox repository.

## Mission

Inspect the repository and create one concise health issue, unless the run was triggered from an issue or PR where a short comment is more appropriate.

## Health Areas

Check:

- Rojo project mapping and whether important services map cleanly to source folders;
- Wally/Aftman/Foreman/Rokit tool manifests and whether commands are documented;
- Selene, StyLua, luau-lsp, TestEZ, or equivalent quality tooling;
- CI coverage for linting, formatting, tests, and build/export checks;
- server/client authority boundaries and obvious unsafe remote patterns;
- DataStore safety patterns: error handling, retries, migration, shutdown saves;
- test coverage and manual Studio QA documentation;
- README accuracy for setup, development, testing, release, and Studio sync;
- oversized modules, repeated code, unbounded loops, and performance-sensitive code.

## Report Format

Create one issue with:

- short summary;
- top 3 risks;
- quick wins;
- larger follow-up items;
- exact files or folders inspected;
- one suggested next workflow to run, such as `/roblox-review`, `/roblox-implement`, or `/roblox-docs`.

If no action is useful, call `noop` with a short reason.
