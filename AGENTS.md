# Agent instructions

## Writing

Load the `unslop` skill before writing any text a person will read, and follow its rules.

## Reporting

- Keep every reply short. Lead with the answer or the result, then stop.
- Report outcomes, decisions, and what I need to do. Don't narrate each step, restate my request, or recap at the end.
- Be extremely concise. Sacrifice grammar for the sake of concision. Only write longer, fuller text when I explicitly ask for detail.

## Decisions

Before changing a project's design, read its `docs/decisions/`. Decisions there are final. Don't change them or work around them. Report any conflict to me and wait.

## Commits

Follow Conventional Commits 1.0.0 for every commit.
Use `<type>[optional scope][!]: <description>`.
Use `feat` for features, `fix` for bug fixes, and appropriate
repo types for other changes. Mark breaking changes with `!`
or a `BREAKING CHANGE:` footer. Check the message before committing.
Apply the same convention to PR titles used for squash merges.
Use the identity configured in Git for new commits. Do not override it.
Never add `Co-authored-by` trailers or other commit attribution for AI models or agents.

## Pull requests

Load and follow the `pr` skill whenever creating a PR or updating its description, including draft PRs.

When authorized to merge a PR, use squash merging.
Use a Conventional Commit message for the squash commit.

## Scratch files

Put temporary files (logs, PR bodies, test scripts) in `$CLAUDE_JOB_DIR/tmp` when it is set. Otherwise use `/tmp/agent-work/<repo>/<branch>`, with `/` in the branch name replaced by `-`. Never write fixed names straight into `/tmp`: agents running in parallel overwrite each other's files there.

## Cleanup after merge

Run `clean-merged` in the repository at the start of a task and after merging a PR. For every merged PR it removes the local branch, its worktree and its folder in `/tmp/agent-work`. It keeps a branch whose worktree has changes, whose commits are not all in the merged PR, or that an open PR still uses. Use `clean-merged --dry-run` to see what it would remove.
