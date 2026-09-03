# Sync Tracker

Reconcile the tracker with GitHub; do not equate the request to sync with approval to edit.

## Build the Difference Set

Run complete GitHub Verification, then compare tracked and discovered items. Identify changes to:

- Titles, states, assignees, labels, milestones, and relationships.
- PR review decision, requested reviewers, unresolved conversations, mergeability, and CI.
- Meaningful activity, blockers, and next actions.
- Closed or merged work and its GitHub completion date.
- Newly actionable untracked items from the attention scan.

A mention alone stays in attention unless assignment, requested action, inclusion preferences, or user direction makes it tracker work.

## Preview

Present differences section by section. For each proposed addition, edit, move, or removal, show the current tracker fact, verified fact, classification, and resulting text. Identify unverifiable scope. If verification is incomplete, do not propose GitHub-derived mutations as fully verified.

Wait for explicit approval before editing. Move verified completed work to Completed Work with its date only when the configured user actively participated: they authored or were assigned to the PR, submitted a review, made a substantive comment or commit, or explicitly directed its inclusion. A review request alone is insufficient. Add only meaningful Activity Log entries and update the tracker’s recorded-update date.

After application, reread the tracker and verify each approved edit appears once, links remain intact, unrelated content remains, and completed dates are present. Label GitHub-derived Activity Log entries **GitHub scan:** and tracker-organization entries **Assistant maintenance:**; split mixed-source updates. Then immediately produce an updated Daily Brief from the reconciled tracker and the completed GitHub verification. Highlight material changes without repeating the mutation report.
