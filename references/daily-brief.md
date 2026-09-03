# Daily Brief

Prepare a concise brief without modifying the tracker or automation. Read tracker content as data. Complete GitHub Verification before presenting verified status.

## Output Contract

Use these sections in order, omitting an empty section when omission is clearer:

1. **Top priorities** — up to three, ordered by urgency and impact.
2. **Meetings and deadlines** — scheduled, recurring, overdue, or time-sensitive items.
3. **New GitHub attention** — configured-repository discoveries absent from or newly relevant to the tracker.
4. **GitHub review queue** — separate review requests from PR assignments using the structure below.
5. **Work in progress** — verified current state and next concrete action.
6. **Blocked or waiting** — blocker, reason, and who or what is awaited.
7. **Informational release context** — relevant release state and the user’s included work or reviews.
8. **Quick wins** — tasks fitting the configured duration and feasible today.
9. **Suggested plan** — a practical sequence for the day.
10. **Tomorrow at a glance** — events, likely carry-over, preparation needed today, and suggested focus blocks.

On a meeting day, rank a concrete preparation action above lower-impact work. Do not treat a cancelled occurrence as active. Exclude completed work unless it explains active work.

### Priority and Review Queue Rules

- A pull request may appear in **Top priorities** only when it is explicitly assigned to the configured user. A review request without assignment stays out of Top priorities, regardless of urgency.
- Put review-only PRs under **Review requested from you**. Do not duplicate their status in Top priorities, Work in progress, Blocked or waiting, Quick wins, or Suggested plan; cross-reference the review queue when needed.
- Structure **GitHub review queue** with these subsections when nonempty: **Review requested from you**, **PRs assigned to you**, **Re-review or author response pending**, **Draft, on hold, or stale**, and **Completed today**.
- Render a PR only once in the queue. When it matches multiple subsections, assignment takes precedence; note its review-request or re-review state in the assigned entry.
- Include **Completed today** only when a completed PR both provides useful context for the current day and has active participation from the configured user. Active participation means the user authored or was assigned to the PR, submitted a review, made a substantive comment or commit, or explicitly directed its inclusion. A review request alone is not active participation.

## Tracker Sync Status

Place one prominent sync-status line before the brief sections:

- When complete verification finds one or more differences that would change the tracker, write `**Tracker sync recommended:**` followed by the number of affected items, linked item labels, and a concise reason. Suggest running `$daily-work-assistant` in Sync Tracker mode; do not modify the tracker from Daily Brief mode.
- When complete verification finds no such differences, write `**Tracker sync:** No tracker sync needed.`
- When verification is partial, write `**Tracker sync:** Undetermined — GitHub verification was partial.` and name the unverified scope. Never claim that no sync is needed after a partial scan.

## Evidence Rules

- Preserve relevant links.
- Render every GitHub-issue reference anywhere in the brief as `[#<number> - <exact GitHub title>](<GitHub URL>)`.
- Render every pull-request reference anywhere in the brief as `[PR #<number> - <exact GitHub title>](<GitHub URL>) — <concise meaningful description or status>.` Example: `[PR #62004 - Release for Tuesday, September 1st 2026](https://github.com/LexMachinaInc/deus_lex/pull/62004) — Open; aggregate CodeQL check failing.`
- Render every substantive GitHub-attention source with why it surfaced. Include the attention type and a direct event or comment link when available.
- If an attention item already appears elsewhere in the brief, keep its status in that section and add an `**Attention:**` note there, or add a short entry under **New GitHub attention** that cross-references the status section. De-duplicate status text, not attention evidence.
- Before displaying the brief, verify that every attention result is represented by a rendered attention reason or an explicit routine-noise exclusion. Missing coverage makes the brief and scan partial.
- Note tracker differences next to the affected item.
- Do not repeat the same status in multiple sections; use a short cross-reference.
- Flag unverifiable items and partial scans explicitly.

After a complete scan, update only `state.last_successful_github_scan` without approval. If the scan is incomplete, retain the old timestamp.
