# Tracker Structure

Preserve the tracker’s readable style and unrelated content. Use the following semantic sections when initializing or repairing; minor heading variations are acceptable when their meaning is clear.

```text
Work Tracker — <Month YYYY>
Current Work
  Meetings and Deadlines
  Needs Attention
  In Progress
  Waiting / Blocked
Informational
Backlog
Completed Work
Activity Log
Related Notes
Daily Entry Template
```

## Invariants

- Keep only active work under Current Work.
- Give an active item one concrete next action.
- Preserve relevant issue and pull-request links.
- Avoid duplicate task entries; cross-reference instead of repeating details.
- Record meaningful progress, decisions, blockers, and outcomes in Activity Log.
- Prefix every Activity Log entry with exactly one provenance label: **User update:** for user-supplied or user-completed work, **GitHub scan:** for GitHub-discovered or GitHub-verified facts, or **Assistant maintenance:** for tracker organization, migration, reconciliation, or deadline bookkeeping. Split mixed-source updates into separate entries.
- Use ISO dates (`YYYY-MM-DD`). Every Completed Work item has its actual completion, merge, or close date.
- Do not add a merged or closed PR to Completed Work solely because the configured user was requested as a reviewer. Require active participation: the user authored or was assigned to the PR, submitted a review, made a substantive comment or commit, or explicitly directed its inclusion.
- Preserve readable content outside known sections. Malformed structure triggers a repair proposal, never silent deletion.

## Fact Precedence

| Fact | Authority |
|---|---|
| GitHub title, state, assignees, reviews, CI, merge/close dates | GitHub |
| Personal priority, meeting, plan, note, follow-up | User |
| Conflict between authorities | Keep visible in proposal or brief |

Do not turn a GitHub mention into active work automatically. Classify an item based on assignment, requested action, tracker preferences, and user approval.
