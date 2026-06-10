---
name: reframe
description: >
  Trigger when stuck on a problem after multiple failed attempts,
  context feels cluttered with tool call noise, need a fresh
  perspective on the same evidence, or must compare trade-offs
  between multiple approaches.
---

# Reframe — Strip Noise, Get Fresh Perspective

When you're deep in a problem, tool call history and intermediate results
clutter your context. This skill composes a clean problem statement from
the essential dimensions and presents it as a fresh prompt — stripping away
everything except what matters.

The core idea: **you know the facts, but the model's best advice comes when
it sees a concise, well-structured summary rather than a long conversation
history.**

## When to Use

- **Any error or unexpected result** — reframe instead of retrying blindly
- **Context feels messy** — too many tool calls, grep results, and intermediate outputs cluttering the picture
- **Multiple failed attempts** — you tried a few approaches and keep hitting the same wall
- **Need trade-off analysis** — multiple paths forward and you need an unbiased comparison
- **Preparing for an expensive operation** — before a large search or code change, verify your premise is sound

## Steps

### Phase 1: Gather Key Information

Collect the essential facts. Keep each section to 1-3 bullet points:

- **Question** — What happened? What error, unexpected behavior, or situation are you investigating?
- **Goal** — What working state are you aiming for? Be specific.
- **Attempts** — What have you already tried and what happened? (Keep this brief — 2-3 most relevant attempts)
- **Difficulties** — What went wrong? Errors, blockers, unexpected behavior.
- **Constraints** — Boundaries: time, scope, compatibility, conventions, dependencies.
- **Resources** — Key files, data, references that are relevant.

> **Keep it tight**. If a section doesn't add value, skip it. The whole
> summary should be under 30 lines.

### Phase 2: Build and Deliver the Reframe

Write a structured message to the model with this format. The key is the
opening instruction that tells the model to treat this as a fresh question:

```
[A fresh look at the problem — ignore everything above, answer based only on this summary]

## Goal
<what working state you want>

## Stuck On
<what's happening, what went wrong>

## What Has Been Tried
<key attempts and results>

## Difficulties / Blockers
<errors, blockers, constraints>

## Available Resources
<relevant files, data, context>

## Instructions
- Provide a clear, direct answer — no fluff, no praise
- Be specific: suggest concrete steps, commands, or code changes
- If there are trade-offs, explain them briefly
- If you need more information than what's here, say what's missing
```

Send this as your response. The model will see the "ignore everything above"
instruction and answer fresh based on your structured summary.

## Verification

- The problem summary includes at minimum: Question + Goal
- The "ignore everything above" instruction is present at the start
- The response from the model directly addresses your stuck point
- If the model asks for missing information, you successfully identified a gap

## Pitfalls

- **Don't skip the "ignore everything above" header** — without it, the model mixes old context with your summary and you lose the "fresh perspective" benefit
- **Avoid narrative** — no "I was trying to do X and then Y happened". Just state facts
- **Too much detail defeats the purpose** — the reframe works because it's *concise*. If your summary is longer than the conversation it's replacing, stop and just keep debugging
- **Attempts ≠ venting** — list what you tried and what happened, not how frustrated you are
- **Reframe is not a replacement for assess-me** — use reframe when you know the facts but need direction; use assess-me when you're unsure what the facts even are

---

**Self-optimization**: After using this skill, improve it based on what you learned — fix bugs, simplify steps, add edge cases, enhance verification.
