---
name: ask-me-with-docs
description: Question the user round after round about a plan or design, recording the decisions in one doc per subject under docs/decisions/ that is updated after every round so the session can resume later. Use when the user asks to be questioned and wants the decisions written down, or when the plan concerns a project in the current repo.
---

Call the Skill tool with "ask-me" and run the interview it describes. On top of it, keep a decision doc.

## The decision doc

Every project keeps one file per subject: `docs/decisions/<subject>.md`, with a short subject name and no date, such as `billing.md`. The folder listing is the index, so the name and the `# Title` must say what the file covers. Create `docs/decisions/` if it doesn't exist.

Before the first round, list `docs/decisions/` and look for a doc on the same subject. If one is `in progress`, read it, tell the user where it stopped, and resume from its open questions instead of starting over. If one is `done`, set it back to `in progress` and work in it. Create a new file only for a new subject.

Update the doc every time you ask a round and every time the user answers one, before doing anything else. A fresh session must be able to resume from the doc alone.

Template:

```md
# <Topic>

Status: in progress
Updated: <date>

> Decisions in this doc are final. Agents must not change or work around them. Report any conflict to the user, who decides.

## Goal

<What we're deciding and why, in one to three sentences.>

## Decisions

- **<Decision>.** <What was chosen and why, in one or two sentences.>

## Open questions

<The current round as asked, with your recommended answers. Questions that depend on them go below.>

## Next

<What happens next. The next round to ask, facts a sub agent is looking up, or the work to start once the user confirms.>
```

Record decisions, not the conversation. Keep only the current rule. When the user changes their mind, or a later decision changes an earlier one, rewrite it in place. Don't add amendment notes, "was X" history or a replacing file, because git keeps the history. Keep a fact found by a sub agent only when it shaped a decision.

## At the end

When no open decision is left and the user confirms the summary, set the status to `done` and fill Next with the follow up work.

## Decisions outside an interview

A small decision made during other work goes in the same place. Add or rewrite one bullet in its subject's file and update the date. Never create a file for a single small decision.

## Decisions are final

A decision in the doc is final. Only the user can change it, by naming the decision and the change. When that happens, rewrite it in place and update the date.

An agent that finds a decision wrong, outdated, or in conflict with the code must not change the decision or work around it. It tells the user which decision, what conflicts, and what it suggests, then waits.
