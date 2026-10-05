---
name: pr
description: Structure PR titles and bodies with concise, verified evidence. Use whenever creating a pull request or updating its description, including draft PRs.
---

# PR

Read the repo's PR template, contribution instructions, and relevant decisions. Keep required fields; fit this convention into them. Without a template, use the format below.

Inspect the full diff against the intended base. Describe the final change, not the work history. Follow the repo's title convention; otherwise use a short title naming the change.

## Evidence

Run checks that exercise the changed behavior, plus checks required by the repo. Reuse results only when they still apply to the submitted code. After relevant edits, rerun affected checks.

Report the command or manual scenario, observed result, and what it verifies. Keep each check to one line. Include counts only when observed. Distinguish passing, failing, skipped, and not run; give a short reason for gaps. Never infer a pass from launching a command, reading code, or adding a test.

For a bug fix, prefer a regression test that fails before and passes after when practical. For UI changes, include a screenshot or recording when it helps demonstrate the behavior, with a reviewer-accessible link. Link existing CI runs or artifacts when useful. Do not claim CI passed before checking its result for the submitted commit.

Capture verbose command output to a temporary log and report its exit status and concise summary. Inspect failures using targeted excerpts. Never paste full npm output, build logs, stack traces, or successful command transcripts into the PR or chat. Include only the shortest diagnostic needed to explain a failure. Do not add tests solely to fill the evidence section.

## Body

Aim for 100 to 200 words; trivial changes can be shorter. Exceed this only for required fields or material review details. Omit empty sections and boilerplate checklists.

```markdown
## Summary

<Problem and resulting behavior in one or two sentences.>

## Validation

* `<command>`: <observed result and behavior checked>.
* <Manual scenario>: <observed result, if applicable>.

## Risks

<Only material limitations, compatibility changes, migrations, or rollout needs. Omit otherwise.>
```

State validation gaps plainly. Match evidence to the scope actually tested; a successful build alone does not prove runtime behavior.

Before submitting, check the title and body against the final diff. Preserve intentional newlines with a structured body argument or `gh --body-file`. After submission, report the PR link and any unresolved blocker briefly.
