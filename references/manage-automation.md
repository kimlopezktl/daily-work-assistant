# Manage Daily-Brief Automation

Manage one primary recurring daily-brief automation per Worklog configuration. Prefer the Codex `automation_update` capability when available; inspect existing automation state before changing it.

## Supported Actions

- View schedule, status, prompt, and notification policy.
- Create or reschedule.
- Pause or resume.
- Update prompt or notification behavior.
- Delete.

Viewing is read-only. For every other action, resolve the existing automation by configured identifier or matching name/prompt, show the exact schedule, status, prompt behavior, notification change, and configuration update, then wait for explicit approval.

## Prompt Contract

The automation prompt is a short dispatcher, not a copy of the Daily Brief rules. It must identify the Worklog root and direct `$daily-work-assistant` to run Daily Brief using the configuration and timezone. At the start of every run, it explicitly rereads the installed `SKILL.md` and the current routed references, including `daily-brief.md` and `github-verification.md`, so instruction changes apply without redeploying copied prompt text. It resolves the active month dynamically rather than naming a month-specific tracker path. It requires the full linked-item verification and configured attention scan, the skill-defined tracker sync status, the nine brief sections, tracker-difference reporting, and no tracker mutation. It may update only a complete-scan timestamp.

When rollover is detected, the automation reports a migration proposal for later user approval; it does not migrate. When GitHub access is incomplete, it reports the missing scope and retains scan state.

## Apply and Verify

Use the product’s scheduling tool rather than writing raw recurrence directives. Apply only the approved action, then save the returned automation identifier, schedule, status, and notification policy in configuration as part of that same approval. Verify tool state matches configuration.

If automation support is unavailable, clearly state that scheduling was not applied. Record desired settings in configuration only when that configuration change was included in the approved proposal.
