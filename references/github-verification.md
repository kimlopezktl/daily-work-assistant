# GitHub Verification

Use authenticated GitHub tools available in the environment. GitHub is authoritative for GitHub facts. Preserve direct issue and pull-request links.

## Linked Items

For every linked issue or pull request in relevant tracker sections, verify:

- Exact title and open, closed, draft, or merged state.
- Assignees, author, labels, milestone, parent/subissue or associated PR relationships.
- Latest meaningful activity: state changes, human decisions, substantive comments, commits, review changes, CI changes, or blocker changes.
- Review decision, requested reviewers, unresolved conversations, mergeability, and CI for pull requests.
- Blocker and next concrete action supported by current evidence.

Exclude routine bot noise, repeated status events, and activity that does not change understanding or action.

## Identity Fidelity

Attribute GitHub activity using the verified `@username` by default. Never derive or guess a person's full or preferred name from a username. Use a human name only when the user supplied that identity mapping or an authoritative GitHub profile explicitly verifies it; retain the username whenever ambiguity remains.

## Attention Scan

Within every configured repository, search since `state.last_successful_github_scan` for:

1. Issues where the configured user was newly assigned or mentioned.
2. Assigned issues updated in that interval, even when absent from the tracker.
3. Pull requests where the user was assigned, mentioned, or requested as a reviewer.

Paginate until the interval is fully covered. De-duplicate linked and discovered items. For each result retain why it surfaced, current state, latest meaningful activity, blockers or review/CI state, and next action.

### Attention Evidence

For every attention result, retain one or more source records containing:

- Attention type: assignment, mention, PR assignment, PR mention, or review request.
- Actor, timestamp, and direct event or comment URL when available.
- A concise explanation of why the event is actionable or informational.

For mention results, inspect comments or timeline activity in the scan interval to locate the actual mention. A notification or supplied URL may point to an adjacent reply rather than the comment containing `@<username>`; retain the direct mention as the source and the adjacent reply only as supporting context.

De-duplication merges attention evidence into the linked or discovered item. Never discard an attention source because the issue or PR is already linked in the tracker or will be described in another brief section. Routine bot noise and metadata-only updates may be excluded, but retain an explicit exclusion reason for coverage validation.

## Completion Rule

A complete scan requires every relevant linked-item lookup and every configured-repository attention query, including pagination and required PR review/CI details, to succeed. Only then update the scan timestamp. If any part fails, label the result partial, identify unverifiable scope, do not claim source-of-truth completeness, and retain the prior timestamp.

Before declaring the scan complete, account for every attention result as either:

1. Substantive evidence that will be rendered in the brief, or
2. Explicitly excluded routine bot noise, repeated status, or metadata-only activity.

An unaccounted substantive result makes the scan incomplete and prevents the timestamp update.
