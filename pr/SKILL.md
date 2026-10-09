---
name: pr
description: Tells how to Write PR titles and bodies with clear groups, concise bullets, and verified evidence. Use whenever creating a pull request or updating its description.
---

# PR

Read the repo's PR template, contribution instructions, and relevant decisions. Keep required fields; fit this convention into them. Without a template, use the format below.

Inspect the full diff against the intended base. Describe the final change, not the work history. Use a Conventional Commit title, `<type>[optional scope][!]: <description>`, following the repo's allowed types and scopes. Name the concrete change; mark breaking changes when applicable.

**Open a real PR, not a draft!** Drafts do not get review coverage.

## Evidence

Run checks that exercise the changed behavior, plus checks required by the repo. Reuse results only when they still apply to the submitted code. After relevant edits, rerun affected checks.

Report the command or manual scenario, observed result, and what it verifies. Keep each check to one line. Include counts only when observed. Distinguish passing, failing, skipped, and not run; give a short reason for gaps. Never infer a pass from launching a command, reading code, or adding a test.

For a bug fix, prefer a regression test that fails before and passes after when practical. For UI changes, add screenshots (see below). Link existing CI runs or artifacts when useful. Do not claim CI passed before checking its result for the submitted commit.

Capture verbose command output to a temporary log and report its exit status and concise summary. Inspect failures using targeted excerpts. Never paste full npm output, build logs, stack traces, or successful command transcripts into the PR or chat. Include only the shortest diagnostic needed to explain a failure. Do not add tests solely to fill the evidence section.

## Screenshots

Required when the PR changes what a screen shows. Skip them for changes with no visible effect.

* Capture the changed screen after the change with the `agent-browser` skill. For a visible bug, also capture it before the fix. Add a phone-size capture when the layout changes.
* Use a local dev server with fake data. Never capture a deployed app or real accounts: the images are readable by anyone who can read the repo.
* If your environment's instructions say how to attach screenshots, for example a folder where you save them and a link format, follow those and skip the steps below. Not being allowed to push is never a reason to skip screenshots in that case.
* Otherwise, push the images to their own branch, `screenshots/<pr branch>`, never to the PR branch. From the repo, with `<b>` the PR branch and `<dir>` a new scratch folder:

  ```
  git worktree add --orphan -b screenshots/<b> <dir>
  cp before.png after.png <dir>/
  git -C <dir> add . && git -C <dir> commit -m "chore: screenshots for <b>"
  git -C <dir> push -u origin screenshots/<b>
  git -C <dir> rev-parse HEAD
  git worktree remove <dir> && git branch -D screenshots/<b>
  ```

* Embed them under Checks with the printed commit: `![after](https://github.com/<owner>/<repo>/blob/<commit>/after.png?raw=true)`.
* `clean-merged` deletes the screenshots branch once the PR is merged or closed. The images in the PR break after that.
* Only when no browser runs, or neither way of attaching works, say so in Checks with the reason.

## Body

Lead with a short paragraph stating the problem or purpose and the resulting behavior. Then group the review details under descriptive headings, using concise bullets. Prefer this readable structure over packing several changes into a Summary paragraph.

Choose headings from the actual change: `Decision`, `Behavior`, `Implementation`, `Doc changes`, `Migration`, or another concrete subject. Use separate groups when they answer different reviewer questions. For a decision PR, explain what was decided separately from which documents were updated. For code, explain the behavior and add implementation details only when they help assess the change. A trivial PR can use one short group plus checks. Omit empty sections and boilerplate checklists.

Give each bullet one coherent point. Preserve constraints, timing, limits, and scope boundaries that matter to review. Combine closely related details; split unrelated changes. Use a short before/after example when it clarifies behavior. Link key decisions or documents when useful, rather than listing every changed file or repeating the diff.

Keep the body as short as the change allows. Do not enforce a word target that removes useful groups or compresses important decisions into dense prose. Remove repetition and incidental details instead. Use plain bullets without bold labels or nested lists unless a hierarchy is necessary.

Adapt this shape to the PR; the headings and bullet count are examples, not required fields:

```markdown
<Problem or purpose and resulting behavior in one or two sentences.>

## Behavior

* <A concrete behavior change and its important constraint.>
* <Another related change, with a short example if useful.>

## Implementation

* <A design choice or affected component that helps review.>

## Checks

* `<command>`: <observed result and behavior checked>.
* <Manual scenario>: <observed result, if applicable>.

## Risks

<Only material limitations, compatibility changes, migrations, or rollout needs. Omit otherwise.>
```

For a documentation decision PR, separate the decisions from the document changes. For example:

```markdown
Records the decision to move scheduled reports to a background queue so report generation can be retried independently.

## Decision

* Queue each scheduled report instead of generating it during the request.
* Retry temporary failures up to three times; show a failed status after the final attempt.
* Build behind a feature flag before enabling the queue for all scheduled reports.

## Doc changes

* Add the queue decision and its rollout criteria to the decision document.
* Update the architecture guide to describe the planned worker and retry behavior.

## Checks

* <Documentation check command>: <observed result>.
```

Distinguish decisions and planned work from delivered behavior. A documentation PR records a change; it does not implement that change. Examples illustrate the structure, not reusable claims or check results. Use fictional examples in reusable guidance; do not copy private project names, paths, or decisions into another repository.

State validation gaps plainly. Match evidence to the scope actually tested; a successful build alone does not prove runtime behavior.

Before submitting, check the title and body against the final diff. Ensure the opening explains the purpose, headings form useful groups, bullets retain material details, and checks contain observed results. When editing an existing PR, preserve useful groups and specifics unless they are stale; rewrite around the final scope when it changes. Preserve intentional newlines with a structured body argument or `gh --body-file`. After submission, report the PR link and any unresolved blocker briefly.
