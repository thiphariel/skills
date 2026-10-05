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

Link the file into your home so every agent reads it:

```sh
ln -s ~/horizon/skills/AGENTS.md ~/AGENTS.md
```

A `git pull` in this repo updates it.

## Update

After pushing to this repo:

```sh
npx skills update -g
```

## Uninstall

```sh
npx skills remove unslop -g
```
