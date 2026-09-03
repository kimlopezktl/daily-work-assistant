# Daily Work Assistant

Use this skill to maintain a monthly work tracker, prepare a GitHub-verified daily brief, sync tracker facts with GitHub, record user-provided updates, migrate to a new month, or manage the recurring brief automation.

## Worklog layout

The Worklog holds personal work-planning records. Its active tracker uses year-qualified, lexically chronological folders:

```text
Worklog/
  2026-09/
    Daily Tracker.md
```

The user-specific configuration is `<Worklog root>/.daily-work-assistant.yaml`. It defines the timezone, GitHub account and repositories, tracker naming convention, briefing preferences, and automation state.

## Invoke it

Use `$daily-work-assistant` followed by your request, for example:

```text
$daily-work-assistant give me my daily brief
$daily-work-assistant sync my tracker
$daily-work-assistant update the tracker: add a Friday meeting
$daily-work-assistant migrate my tracker to the next month
```

The assistant asks for the Worklog root once per conversation when it has not already been supplied. The configured root contains sortable `YYYY-MM` folders such as `2026-09/`.

## Behavior

- GitHub is authoritative for linked issues and pull requests; the configured user and repositories are the scan boundary.
- Daily briefs are read-only and surface tracker differences, review requests, assigned PRs, meetings, blockers, and relevant GitHub attention.
- Before any tracker or automation mutation, the assistant presents the exact proposed edits and waits for explicit approval.
- A review request alone does not make a merged PR completed work. Completed work requires active user participation or explicit user direction.
- After an approved sync or update, the assistant verifies the change and produces an updated daily brief.

## Daily workflow

- **Daily brief:** read-only GitHub-verified status, including tracker differences.
- **Sync tracker:** compare the tracker with GitHub; review and approve the exact proposed edits before they are applied.
- **Update tracker:** record user-provided meetings, priorities, progress, blockers, or notes after approval.
- **Monthly migration:** carry active work into the next `YYYY-MM` folder after approval; completed work and historical activity remain in the source tracker.

## Configuration and detailed guidance

See [SKILL.md](SKILL.md) for routing and [references](references/) for setup, GitHub verification, briefing, syncing, updates, migration, and automation procedures.
