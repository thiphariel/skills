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
