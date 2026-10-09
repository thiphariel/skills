# skills

My skills for compatible agents.

Each skill is a folder at the repo root with a `SKILL.md` inside. `AGENTS.md` holds my global agent instructions.

## Install

All skills, globally, for the agents I use:

```sh
npx skills add thiphariel/skills -g -y -s '*' -a claude-code codex pi
```

A single skill:

```sh
npx skills add thiphariel/skills -g -y -s unslop -a claude-code codex pi
```

Without `-a`, `-y` targets every agent the CLI knows, and some of them refuse global installs.

Files go to `~/.agents/skills/`, with a link in `~/.claude/skills/` for claude.

## Global instructions

Link the file into your home for agents that read `~/AGENTS.md`:

```sh
ln -s ~/horizon/skills/AGENTS.md ~/AGENTS.md
```

A `git pull` in this repo updates it.

### Codex

Codex reads global instructions from `~/.codex/AGENTS.md`, not `~/AGENTS.md`. Link the file there too:

```sh
mkdir -p ~/.codex
ln -s ~/horizon/skills/AGENTS.md ~/.codex/AGENTS.md
```

If `~/.codex/AGENTS.md` already exists, `ln` fails. Move it aside or merge its content into this file first. To check, start Codex and ask it to list the instructions it loaded.

### Other agents

For other agents, include this file from their global instructions. The `pr` skill needs both a global skill install and the instruction to load it on every PR. Automatic skill discovery alone does not require invocation.

## Cleanup script

`bin/clean-merged` removes the local branches, worktrees and scratch folders of merged pull requests. `AGENTS.md` tells agents to run it. Put it on your `PATH`:

```sh
ln -s ~/horizon/skills/bin/clean-merged ~/.local/bin/clean-merged
```

It needs `git` and an authenticated `gh`.

## Update

After pushing to this repo:

```sh
npx skills update -g
```

## Uninstall

```sh
npx skills remove unslop -g
```
