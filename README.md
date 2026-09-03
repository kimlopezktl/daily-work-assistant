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

## Install it

Codex loads skills from `~/.codex/skills/<name>/`, so clone this repository directly into
that path. The repository root is the skill, so do not nest it in a subfolder.

```text
git clone https://github.com/kimlopezktl/daily-work-assistant.git \
  ~/.codex/skills/daily-work-assistant
```

Start a new Codex session afterward so the skill is picked up. To update later:

```text
git -C ~/.codex/skills/daily-work-assistant pull
```

A pull replaces only the instructions. It touches nothing user-specific: the Worklog, the
tracker, `.daily-work-assistant.yaml`, and the scheduled automation all live outside this
repository and survive updates untouched. Existing automation also needs no redeployment,
because its prompt rereads the installed `SKILL.md` and references at the start of every
run, so an updated skill changes the next brief on its own.

Nothing else needs to run after a pull. On a **first** install there is no configuration
yet, so begin with setup and supply the Worklog root:

```text
$daily-work-assistant set up my tracker. Worklog root is ~/Worklog.
```

Setup inspects the root, proposes configuration and a tracker, and waits for approval
before writing. If a later update introduces new preferences, rerun the setup
questionnaire — it reconfigures in place and does not reinitialize the tracker.

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
