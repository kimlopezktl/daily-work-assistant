# Setup and Reconfiguration

Use when configuration or the current tracker is absent, setup is partial, or the user asks to change briefing preferences.

## Inspect First

Inspect the supplied Worklog root for configuration, month folders, trackers, conventions, and partial setup. Never overwrite an existing tracker or discard unknown configuration.

## Recommended Profile

Present a concise recommended profile that the user can accept or customize. Ask only unresolved questions. Cover:

- Timezone, GitHub username, and configured repositories.
- Tracked tasks plus relevant untracked GitHub attention.
- Assigned issues, authored PRs, assignments, mentions, and review requests.
- Draft PRs and stale review requests.
- Backlog, blocked, waiting, informational, and completed-context inclusion.
- Included/excluded labels, projects, and task types.
- Staleness threshold, priority rules, recurring meetings, meeting preparation, quick-win duration, and Tomorrow at a glance.
- Tracker month-folder and filename conventions.
- Optional primary automation schedule and notification policy.

Defaults are suggestions, not decisions. Store accepted choices in configuration.

Unless existing configuration or the user indicates otherwise, recommend:

- Include active tracked work and linked GitHub verification.
- Surface untracked newly assigned or mentioned issues, updated assigned issues, PR assignments/mentions, and review requests from configured repositories.
- Include authored PRs only when tracked or currently actionable.
- Classify draft PRs and on-hold reviews as waiting; flag stale review requests for confirmation.
- Include blocked/waiting and informational context; use backlog only for feasible quick wins; include completed work only as active context.
- Use 14 days as the initial staleness threshold, 30 minutes as the quick-win threshold, three top priorities, meeting-day preparation, and Tomorrow at a glance.
- Enable no automation until the user accepts a schedule and notification policy.

## Proposal and Application

Preview the configuration, current-month folder, tracker template, and optional automation as one proposal. Identify existing items that remain unchanged and partial items that need focused repair. Wait for explicit approval.

After approval, create only missing items or apply only approved repairs. Verify paths, configuration validity, tracker headings, preserved existing content, and automation state. The questionnaire may be rerun later without reinitializing the tracker.
