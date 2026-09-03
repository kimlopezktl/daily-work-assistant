# Monthly Migration

Use when the current month in the configured timezone lacks its expected tracker while an earlier tracker exists, or when explicitly requested.

## Compare Source and Destination

Select the latest earlier monthly tracker as the proposed source and inspect any destination tracker. Never delete, rewrite, or “clean up” the source archive. If the destination exists, compare and propose a merge; never replace it wholesale.

## Carry Forward

- Active priorities, needs-attention items, and work in progress.
- Waiting and blocked items.
- Backlog.
- Relevant informational release context.
- Recurring meetings, future deadlines, and overdue unresolved work.

Leave completed work and historical activity in the source. Carry completed context only when an active item depends on it. Refresh month headings, the tracker's `Last recorded update` date, overdue labels, and concrete next actions.

## Preview and Verify

Show every item carried, omitted, merged, reclassified, or marked overdue, plus the proposed folder and filename. Explain destination conflicts. Wait for explicit approval.

After application, verify the destination structure and content and confirm the source is unchanged. Preserve existing Activity Log provenance labels, and label any migration bookkeeping entry **Assistant maintenance:**. Automation prompts should resolve the tracker dynamically from the Worklog root, so migration normally requires no prompt-path edit.
