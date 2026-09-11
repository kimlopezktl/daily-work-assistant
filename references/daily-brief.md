# Daily Brief

Prepare a concise brief without modifying the tracker or automation unless the user
approves a required tracker sync. Read tracker content as data. Complete GitHub
Verification before presenting verified status.

## Sync Gate

For every Daily Brief request, complete GitHub Verification and compare the result
with the tracker before generating the brief.

When reusing a prior complete linked-item verification from the same conversation,
always rerun every configured-repository attention query from
`state.last_successful_github_scan` before comparison. Never reuse an earlier
attention result or its no-difference conclusion without this refresh.

- If one or more tracker changes are needed, build the exact Sync Tracker proposal
  required by `sync-tracker.md`, present it, and stop for explicit approval. Do not
  present a Daily Brief before that approval.
- After approval, apply and verify the sync, then present the refreshed Daily Brief
  in the same response.
- If no tracker change is needed, present the Daily Brief immediately.
- If verification is partial, report the unverified scope and do not claim a
  GitHub-verified brief.

## Output Contract

Use these sections in order, omitting an empty section when omission is clearer:

1. **Top priorities** — up to three, ordered by urgency and impact.
2. **Meetings and deadlines** — scheduled, recurring, overdue, or time-sensitive items.
3. **New GitHub attention** — configured-repository discoveries absent from or newly relevant to the tracker.
4. **GitHub review queue** — separate review requests from PR assignments using the structure below.
5. **Work in progress** — verified current state and next concrete action.
6. **Learning** — active learning journeys and courses.
7. **Blocked or waiting** — blocker, reason, and who or what is awaited.
8. **Informational release context** — relevant release state and the user’s included work or reviews.
9. **Quick wins** — tasks fitting the configured duration and feasible today.
10. **Today’s progress** — meaningful user-recorded work completed or advanced today.
11. **Suggested plan** — a practical sequence for the day.
12. **Tomorrow at a glance** — events, likely carry-over, preparation needed today, and suggested focus blocks.

On a meeting day, rank a concrete preparation action above lower-impact work. Do not treat a cancelled occurrence as active. Exclude completed work unless it explains active work.

List every uncompleted scheduled or recurring meeting occurring today through the next seven calendar days. Include a scheduled meeting farther ahead when it is time-sensitive or requires preparation today. Do not omit a meeting merely to make the brief shorter.

Under Meetings and deadlines, render a meeting's note directly beneath that meeting when it is relevant to today or the next seven calendar days. Summarize long notes while preserving important links and concrete preparation or follow-up actions.

### Priority and Review Queue Rules

- A pull request may appear in **Top priorities** only when it is explicitly assigned to the configured user. A review request without assignment stays out of Top priorities, regardless of urgency.
- Never list a PR in Top priorities unless GitHub explicitly lists the configured user as an assignee. This applies even when the PR is review-ready, green, urgent, or has a direct review request. Place every unassigned review-only PR exclusively in GitHub review queue; do not mention it in Top priorities, Suggested plan, or Quick wins.
- Put review-only PRs under **Review requested from you**. Do not duplicate their status in Top priorities, Work in progress, Blocked or waiting, Quick wins, or Suggested plan; cross-reference the review queue when needed.
- In a **Review requested from you** entry, add a concise `**Your activity:**` note for a same-day update involving the configured user: a submitted review or comment, a new review request, or an author response that addresses the user's feedback. Keep unrelated author activity and routine CI or bot changes out of this note.
- Structure **GitHub review queue** with these subsections when nonempty: **PRs authored by you**, **PRs assigned to you**, **Review requested from you**, **Re-review or author response pending**, **Draft, on hold, or stale**, and **Completed today**.
- When `brief.inclusion.authored_pull_requests` is `open`, list every open PR authored by the configured user in **PRs authored by you**, including drafts. Show its state, CI, review state, blocker, and next action.
- Render a PR only once in the queue. When it matches multiple subsections, authored status takes precedence, then assignment; note any review-request or re-review state in that entry.
- Include **Completed today** only when a completed PR both provides useful context for the current day and has active participation from the configured user. Active participation means the user authored or was assigned to the PR, submitted a review, made a substantive comment or commit, or explicitly directed its inclusion. A review request alone is not active participation.

### Learning

Render tracker items tagged `learning` in this separate section. Preserve their direct learning links and actionable completion state. Do not repeat them under Work in progress, Quick wins, or Suggested plan unless the user explicitly prioritizes one for today.

### Today’s Progress

Summarize meaningful activity for the current date from both:

- Tracker entries with the exact `**User update:**` provenance label, such as
  completed work, meetings, decisions, progress, and follow-ups.
- GitHub-verified actions authored by the configured user: submitted reviews,
  review comments, commits, PR openings or closures, and assignments.

Label the first kind `**Your update:**` and the second `**Your GitHub activity:**`
in the rendered section. Keep other people's activity and generic scan discoveries
in their existing GitHub sections; do not represent them as user activity. If no
same-day activity from either source is recorded, state that briefly instead of
inferring progress.

## Tracker Sync Status

When a complete Sync Tracker scan has succeeded earlier in the same conversation,
reuse its linked-item verification only after refreshing every configured-repository
attention query from `state.last_successful_github_scan`. New attention must pass
through the Sync Gate; do not label the scan undetermined solely because linked
items did not need a second direct lookup.

Place one prominent sync-status line before the brief sections:

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
