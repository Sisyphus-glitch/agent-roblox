---
description: "Roblox documentation workflow that keeps README and docs aligned with project layout, tooling, and gameplay systems."
labels: ["roblox", "documentation", "docs-sync"]
metadata:
  version: "0.1.0"
  category: "roblox-docs"
on:
  workflow_dispatch:
    inputs:
      target:
        description: "Documentation area, subsystem, or path to update."
        required: false
        type: string
      instructions:
        description: "Maintainer instructions for the docs update."
        required: false
        type: string
  slash_command:
    name: roblox-docs
    events: [issues, issue_comment, pull_request, pull_request_review_comment]
  roles: [admin, maintainer, write]
  skip-bots: [github-actions, copilot, dependabot, renovate]
strict: true
permissions:
  contents: read
  issues: read
  pull-requests: read
tools:
  edit:
  github:
    toolsets: [context, repos, issues, pull_requests]
  bash:
    - ls
    - find
    - grep
    - rg
    - cat
    - sed
    - awk
    - wc
    - git diff
    - git log
    - git show
network:
  allowed:
    - defaults
safe-outputs:
  max-patch-size: 384
  create-pull-request:
    title-prefix: "[roblox-docs] "
    draft: true
    max: 1
    if-no-changes: warn
    protected-files: fallback-to-issue
    allowed-files:
      - "README.md"
      - "*.md"
      - "docs/**"
      - "documentation/**"
  add-comment:
    max: 1
    target: triggering
    discussions: false
  create-issue:
    title-prefix: "[roblox-docs] "
    max: 1
  missing-data:
    create-issue: false
    max: 1
---

# Roblox Documentation Sync

Keep Roblox project documentation accurate and useful.

## Mission

Review README and documentation against the actual repository layout and recent changes. Create a small draft PR for obvious docs fixes, or create/comment with a clear docs task when the needed update is too broad.

## What To Check

- Project setup: Roblox Studio, Rojo sync, package manager, toolchain installation.
- Source layout: server, client, shared, ReplicatedStorage, ServerScriptService, StarterPlayer, StarterGui, and tests.
- Common commands: build, serve/sync, lint, format, test, package, release.
- Gameplay/system docs: remote contracts, DataStore schemas, services/modules, UI flows, and manual QA steps.
- Accuracy drift: docs mentioning files, commands, or systems that no longer exist.
- Onboarding gaps: what a new Roblox developer needs to run the project safely.

## Editing Rules

- Only edit Markdown documentation files allowed by `safe-outputs.create-pull-request.allowed-files`.
- Do not invent Roblox behavior that is not visible in code or maintainer instructions.
- Keep docs concise and task-oriented.
- Include Studio-only steps when a change cannot be validated from source files alone.
- Use `missing-data` if the project has no docs target and the requested docs update is unclear.

## PR Requirements

Create one draft PR with:

- summary of docs updated;
- source files or project structure used as evidence;
- commands or Studio steps documented;
- any areas needing human confirmation.

If no docs change is needed, call `noop` with a short reason.
