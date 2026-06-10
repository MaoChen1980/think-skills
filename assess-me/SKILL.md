---
name: assess-me
description: >
  Trigger when debugging goes in circles, results are confusing,
  multiple hypotheses exist, or you need a sanity check on your direction.
  Use before expensive operations, after repeated failures, or when
  you feel like you're guessing.
---

# Assess Me — Self-Cognition Audit

A structured self-assessment protocol. You review your own conversation
context (which you already have) against a fixed set of cognition questions.
The result is a compact status snapshot that catches blind spots,
unverified assumptions, and wasted directions.

## When to Use

- **Going in circles** — same error, different attempts, no progress
- **Confusing results** — a tool returned something unexpected
- **Multiple hypotheses** — competing explanations, not sure which to pursue
- **Before expensive operations** — about to grep/read/write your way through a large codebase
- **Feeling uncertain** — you sense you might be missing something but can't name it
- **Periodic checkpoint** — every 5-10 turns on complex tasks

## Steps

### Phase 1: Self-Review

Review what you know about the current situation. Answer these six questions
based on your working memory of the conversation:

1. **Goal** — What is the task? What priority? What does "done" look like?
2. **Progress** — What's done? What's pending? Are you ahead or behind where you expected?
3. **Gaps** — What information do you need but don't have yet? What files haven't you checked?
4. **Assumptions** — What unverified beliefs are driving your current approach? Call these out explicitly — assumptions are the most common blind spot.
5. **Blocker** — Are you stuck? If so, what specifically is blocking you? Name the exact obstacle, not a symptom.
6. **Recovery** — If stuck, what should you do differently on the next attempt? Be specific.

> **Tip**: If you can't answer one of these, that itself is useful information —
> it means you haven't been tracking that dimension.

### Phase 2: Critical Analysis

Re-read your answers from Phase 1 as if a colleague wrote them. Look for:

- **Circular reasoning** — is your "progress" description just restating efforts without results?
- **Vague blockers** — "the API doesn't work" vs "the POST /users endpoint returns 403 with this exact payload"
- **Missing gaps** — if you listed no gaps, you're probably missing some
- **Wishful assumptions** — "this should work" without evidence
- **Confirmation bias** — are you only looking for evidence that supports your current theory?

Revise any items that fail this critique.

### Phase 3: Output

Write the assessment as a structured block in your response:

```
[assess]
Goal: ...
Progress: ...
Gaps: ...
Assumptions: ...
Blocker: ...
Recovery: ...
[/assess]
```

Keep each section to 1-2 sentences. No fluff. The point is to externalize
your thinking so you (and the model) can see it clearly.

## Verification

- All 6 sections are filled (use "N/A" if genuinely not applicable)
- Assumptions section is not empty — there are always assumptions
- Recovery says more than "keep trying" if there's a blocker
- The output is surrounded by `[assess]...[/assess]` tags for clear delimitation

## Pitfalls

- **Don't skip Phase 2** — the critical re-read is where most value comes from
- **Don't inflate** — if nothing is blocked, say "N/A" for Blocker. If progress is obvious, keep it brief
- **Assumptions are not facts** — if you caught yourself thinking "this should work", that's an assumption until verified
- **Gaps vs Assumptions** — gaps are information you *know* you lack; assumptions are things you *believe* without evidence. They overlap, but the distinction matters
- **Recovery is not a wish** — it should be a concrete next action, not "figure out X"

---

**Self-optimization**: After using this skill, improve it based on what you learned — fix bugs, simplify steps, add edge cases, enhance verification.
