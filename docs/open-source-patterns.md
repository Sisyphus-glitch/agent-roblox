# Open Source Workflow Patterns

This repository's Roblox workflow templates are based on patterns from GitHub Agentic Workflows and the public workflow examples described in Peli's Agent Factory.

## Patterns Applied

- Issue triage: small event-driven workflow that labels and comments on issues.
- Continuous improvement: scheduled or manual agents that create one focused issue or PR instead of broad rewrites.
- Documentation maintenance: docs agents compare recent changes and repository structure against README/docs, then create small PRs.
- PR management and review: review agents use comments and PR review safe outputs instead of merging or approving.
- Fault investigation: health agents diagnose risk and create actionable reports rather than just announcing that something failed.

## Roblox Adaptation

- Server authority and remote validation are first-class review criteria.
- DataStore safety, retries, migrations, and shutdown saves are tracked as health and review risks.
- Roblox place/model/binary files are excluded from automated PRs by default.
- Studio-only work is converted into issues or manual QA steps instead of unsupported file edits.
- Each specialized workflow has a narrow output contract so maintainers can review agent work safely.

## Sources

- GitHub Agentic Workflows documentation: https://github.github.com/gh-aw/
- Safe outputs reference: https://github.github.com/gh-aw/reference/safe-outputs/
- Pull request safe outputs: https://github.github.com/gh-aw/reference/safe-outputs-pull-requests/
- Issue triage workflow write-up: https://github.github.com/gh-aw/blog/2026-01-13-meet-the-workflows/
- Continuous documentation write-up: https://github.github.com/gh-aw/blog/2026-01-13-meet-the-workflows-documentation/
- Fault investigation write-up: https://github.github.com/gh-aw/blog/2026-01-13-meet-the-workflows-quality-hygiene/
