# Agent instructions

## Questions are read-only

- A question is a request for an answer, not for changes! If the message opens with "How hard would it be", "what are your thoughts", "why does", "should we", "is it possible", "can X do Y", or otherwise asks rather than instructs: answer it, and do not edit files blindly.
- If the answer is obvious and the change is trivial, still answer first and offer the change, but always ask before making it.

## Behaviour

You should focus on building complex things as simple as possible, always try to find ways to reduce complexity when solving problems.

## Blast radius

Never run destructive or dangerous commands outside your worktree / branch or boundaries you've been given, and if your actual work somehow needs it, name what you are about to do before you're doing it. 

## Reporting

- Keep every reply short. Lead with the answer or the result, then stop.
- Report outcomes, decisions, and what I need to do. Don't narrate each step, restate my request, or recap at the end.
- Be extremely concise. Sacrifice grammar for the sake of concision. Only write longer, fuller text when I explicitly ask for detail.

## Writing

Load the `unslop` skill before writing any text a person will read, and follow its rules.

## Cleanup after merge

Run `clean-merged` in the repository at the start of a task and after merging a PR. For every merged PR it removes the local branch, its worktree and its folder in `/tmp/agent-work`. It keeps a branch whose worktree has changes, whose commits are not all in the merged PR, or that an open PR still uses. Use `clean-merged --dry-run` to see what it would remove.

## Decisions

Before changing a project's design, read its `docs/decisions/`. Decisions there are final. Don't change them or work around them. Report any conflict to me and wait.

## Coding preferences

- Keep things simple. "yagni" energy unless told otherwise.
- Typesafety is useful, take advantage of it when it applies.
- Don't be scared to propose bold ideas if they can benefit our work.
- Tests are good! Endless smoke tests, "regression tests" for feature deletions, etc, much less good. Tests should be focused, not slop.
- Comments are a great way to clarify functionality and how code is used. Don't comment every line, but feel free to concisely describe how functions are used above their definitions, classes, etc.
- Keep comments up to date! When making changes, it's very important to keep things in sync.

## Match ceremony to the task

- Do not spawn subagents or multi-agent panel for work a single agent finishes in one pass. Delegation is for breadth or adversarial review, not for ordinary tasks.
- When several agents do work in parallel, state file ownership up front so they do not collide.

## Scratch files

Put temporary files (logs, PR bodies, test scripts) in `/tmp/agent-work/<repo>/<branch>`, with `/` in the branch name replaced by `-`. Never write fixed names straight into `/tmp`: agents running in parallel overwrite each other's files there.

## Commits

Follow conventional commits spec for every commit.
Use `<type>[optional scope][!]: <description>`.
Use `feat` for features, `fix` for bug fixes, and appropriate
repo types for other changes. Mark breaking changes with `!`
or a `BREAKING CHANGE:` footer. Check the message before committing.
Apply the same convention to PR titles used for squash merges.
Use the identity configured in Git for new commits. Do not override it.
Never add `Co-authored-by` trailers or other commit attribution for AI models or agents.

## Pull requests

Load and follow the `pr` skill whenever creating a PR or updating its description.
