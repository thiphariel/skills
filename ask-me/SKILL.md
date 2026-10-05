---
name: ask-me
description: Question the user round after round about a plan, decision, or idea until every open point is settled, without writing a doc. Use when the user asks to be questioned or wants a plan examined and no written record is needed.
---

Keep asking until you and the user share the same understanding of the plan. Nothing gets settled by assumption.

## How the questions are organized

Treat the plan as a set of decisions where some depend on others. A decision is ready to ask once every decision it depends on is settled. Each round, ask every ready decision at once. Leave out a question whose answer depends on another question in the same round, and ask it next round.

After each round of answers, work out which decisions just became ready and ask those next.

## Round format

Number questions across the whole session, so the user can answer "3: yes" without ambiguity.

```
### 3. <Short title>

<The question and the context needed to answer it.>

1. <Option>
2. <Option>

**Recommended:** <option and the reason in one sentence>
```

Stop after the round and wait for the answers.

## Facts and decisions

Facts are your job. If a question depends on something you can check, such as code, files, config, or docs, look it up with a sub agent instead of asking. While it runs, ask the questions that don't depend on it.

Decisions are the user's. Give your recommendation, then let them choose.

## Finishing

The session ends when no open decision is left. Summarize the decisions, ask the user to confirm the summary, and don't act on any of it before they do.
