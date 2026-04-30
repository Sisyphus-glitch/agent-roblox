# Command Cookbook

Use these examples in GitHub issues and pull requests after compiling the workflows.

## General Development

```text
/roblox-dev project-health
/roblox-dev review ReplicatedStorage.Shared.Inventory for server authority issues
/roblox-dev create a test plan for matchmaking remotes
```

## Issue Triage

```text
/roblox-triage
/roblox-triage classify this crash report and ask for missing repro details
```

## PR Review

```text
/roblox-review review this pull request for RemoteEvent validation
/roblox-review focus on DataStore migration and shutdown save risk
/roblox-review check for lifecycle cleanup and performance regressions
```

## Implementation

```text
/roblox-implement fix the cooldown bypass described above
/roblox-implement add TestEZ coverage for InventoryService validation
/roblox-implement refactor the repeated remote payload checks into a local helper
```

## Health

```text
/roblox-health overall
/roblox-health networking
/roblox-health datastore
/roblox-health tests
```

## Documentation

```text
/roblox-docs update onboarding docs for Rojo and Wally
/roblox-docs document manual Studio QA for multiplayer inventory sync
/roblox-docs align README commands with the current tool manifests
```

## Better Prompts

Good commands include:

- the system or file to inspect;
- the risk area to focus on;
- what output you want;
- any known constraints.

Example:

```text
/roblox-review focus on ServerScriptService.TradingService. Check remote payload validation, ownership checks, cooldowns, and DataStore rollback risks. Ignore UI style unless it affects correctness.
```
