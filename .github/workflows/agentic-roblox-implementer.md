---
description: "Roblox implementation workflow for small feature, bug-fix, test, and docs PRs."
labels: ["roblox", "implementation", "draft-pr"]
metadata:
  version: "0.1.0"
  category: "roblox-implementation"
on:
  workflow_dispatch:
    inputs:
      change_type:
        description: "Kind of change to attempt."
        required: false
        type: choice
        options:
          - bug-fix
          - feature
          - test
          - docs
          - refactor
        default: bug-fix
      target:
        description: "Subsystem, issue, module, or path to work on."
        required: true
        type: string
      instructions:
        description: "Maintainer instructions for the change."
        required: true
        type: string
  slash_command:
    name: roblox-implement
    events: [issues, issue_comment]
  roles: [admin, maintainer, write]
  skip-bots: [github-actions, copilot, dependabot, renovate]
strict: true
permissions:
  contents: read
  issues: read
  pull-requests: read
  actions: read
tools:
  edit:
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
    - git status
    - git diff
    - git log
    - git show
    - rojo
    - wally
    - selene
    - stylua
    - luau-lsp
    - lune
network:
  allowed:
    - defaults
safe-outputs:
  max-patch-size: 512
  concurrency-group: "roblox-implement-${{ github.repository }}"
  create-pull-request:
    title-prefix: "[roblox-implement] "
    draft: true
    max: 1
    auto-close-issue: false
    if-no-changes: warn
    protected-files: fallback-to-issue
    excluded-files:
      - "**/*.lock"
      - "**/*.rbxl"
      - "**/*.rbxlx"
      - "**/*.rbxm"
      - "**/*.rbxmx"
      - "dist/**"
      - "build/**"
      - "out/**"
  add-comment:
    max: 1
    target: triggering
    discussions: false
  create-issue:
    title-prefix: "[roblox-implement] "
    max: 1
  missing-data:
    create-issue: false
    max: 1
---

# Roblox Implementer

Implement one small Roblox change as a draft pull request.

## Mission

Follow the maintainer's `change_type`, `target`, and `instructions`, or the `/roblox-implement` command text. Make the narrowest useful change and explain validation.

## Work Rules

- Do not change Roblox place/model/binary files.
- Do not make broad architecture changes unless the maintainer explicitly asked for that.
- Preserve existing Rojo mapping, naming, folder ownership, and Luau style.
- Prefer server-authoritative logic for privileged gameplay decisions.
- Validate client remote payloads before using them.
- Add or update TestEZ tests when the repository already has a test pattern.
- If automated tests cannot run, include a precise manual Studio QA checklist in the PR body.
- If the request is unclear, call `missing-data` instead of inventing requirements.

## PR Requirements

Create one draft PR with:

- a specific title;
- summary of changed behavior;
- touched files and why;
- tests run or manual QA plan;
- risks and Roblox Studio follow-up when relevant.

If no safe implementation is possible from repository files alone, create an issue or comment explaining the blocker.
