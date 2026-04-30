# Roblox Safety Checklist

Use this checklist when tuning prompts or reviewing agent-generated work.

## Server Authority

- Server owns economy, rewards, inventory, combat, progression, matchmaking, and persistence.
- Client requests are treated as suggestions, not truth.
- Server recalculates privileged decisions from trusted state.

## Remote Validation

- Validate payload type and shape.
- Validate player identity and ownership.
- Validate current state and permissions.
- Validate distance, cooldowns, and rate limits.
- Reject unexpected fields and impossible values.
- Avoid returning privileged server-only data to clients.

## DataStore Safety

- Wrap reads and writes with error handling.
- Include retry/backoff strategy where appropriate.
- Track schema version and migration path.
- Handle shutdown saves deliberately.
- Avoid overwriting newer data with stale state.
- Consider rollback or recovery for critical state.

## Lifecycle Cleanup

- Disconnect events when instances or controllers are destroyed.
- Stop loops and tasks when systems are disabled.
- Avoid unbounded `while true` loops.
- Avoid per-frame work unless it is necessary and bounded.
- Clean up CollectionService tag listeners and temporary instances.

## UI And Input

- Test mouse/keyboard, touch, and gamepad where relevant.
- Handle different viewport sizes.
- Avoid assuming every UI instance exists.
- Keep text resilient to localization and longer strings.
- Avoid blocking core gameplay with non-dismissible UI.

## Performance

- Avoid repeated full-tree scans during gameplay.
- Avoid expensive allocations inside Heartbeat or RenderStepped.
- Cache services and stable references when used frequently.
- Prefer event-driven updates over polling.
- Watch replication cost for large or frequently changing instances.

## Testing

- Add TestEZ coverage where a project already has test patterns.
- Include multiplayer Studio QA when replication matters.
- Test server/client boundaries with invalid client inputs.
- Document manual Studio steps when automation cannot cover the behavior.
