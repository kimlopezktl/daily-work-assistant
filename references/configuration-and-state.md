# Configuration and State

Resolve configuration at `<Worklog root>/.daily-work-assistant.yaml`. If it is absent or incomplete, use Setup; do not infer a different root.

## Schema

```yaml
version: 1
timezone: Asia/Manila
github:
  username: example-user
  repositories:
    - owner/repository
tracker:
  month_directory_format: YYYY-MM
  filename: Daily Tracker.md
brief:
  inclusion: {}
  priority_rules: {}
  stale_after_days: 14
  quick_win_minutes: 30
  include_tomorrow: true
automation:
  name: daily-work-brief
  id: null
  schedule: null
  notification_policy: null
  status: null
state:
  last_successful_github_scan: null
```

Values shown are examples, not universal defaults. Setup proposes defaults and lets the user customize them.

## Resolution and Validation

- Resolve dates and the current month in `timezone`.
- Use a year-qualified, lexically chronological `YYYY-MM` month-directory format. Resolve the active tracker as `<root>/<formatted current month>/<filename>`.
- Scan only `github.repositories`; never broaden to all accessible repositories.
- Require a valid GitHub username and at least one `owner/repository` entry for GitHub modes.
- Preserve unknown supported keys when changing configuration.
- Treat an invalid version, timezone, repository entry, or tracker convention as a repair proposal, not permission to rewrite the file.

## Mutable State

“New” and “recently updated” mean after `state.last_successful_github_scan`. Update that field only after the complete-scan conditions in GitHub Verification pass. Write an ISO 8601 timestamp with timezone.

A failed linked lookup, repository query, authentication check, pagination step, or required review/CI lookup makes the scan incomplete. Report the missing scope and retain the prior timestamp.

All configuration writes other than the successful-scan timestamp require preview and explicit approval.
