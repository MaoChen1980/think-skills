---
name: debug-root-cause
description: >
  Trigger when any tool returns an error, you encounter unexpected
  behavior, debugging stalls, or you're starting a new investigation
  and want a systematic approach. Use before diving into random grepping.
---

# Debug Root Cause — Systematic Investigation Methodology

When something goes wrong, the instinct is to grep around and try things.
This skill replaces random exploration with a structured approach: pick the
right root-cause analysis method for your situation and apply it step by step.

## When to Use

- **Any tool returns an error or unexpected result**
- **You see an error and need to figure out how to approach it**
- **You tried a few things but kept hitting dead ends**
- **You're about to start investigating** — stop first, get a methodology
- **You have a complex bug with multiple possible causes**

## Steps

### Phase 1: Define the Problem

Write a one-paragraph problem statement:

```
## Problem
What: <what happened — error message, unexpected behavior>
Expected: <what should have happened instead>
Frequency: <always / intermittent / specific conditions>
Impact: <what broke — failed test, production issue, compilation error>
```

### Phase 2: Select Investigation Methods

Read the [RCA Methods Reference](references/rca-methods.md) and pick 1-3
methods that fit your situation. General guidance:

| Situation | Best Methods |
|-----------|-------------|
| **Unknown cause, lots of variables** | Divide & Conquer, Single Variable |
| **Regression (used to work)** | Rollback, Comparison |
| **Intermittent failure** | Reproduction, Wait & Observe |
| **Error message points somewhere** | Reverse Inference, Chain Tracing |
| **Complex system, many layers** | Layer Stripping, Elimination |
| **Data looks wrong** | Look Inside, Boundary Testing |
| **Need to understand unknown code** | Log Injection, Time Travel |
| **Can't find the pattern** | Outlier Analysis, Hypothesis Testing |

Pick methods based on which dimension of the problem is most opaque to you.

### Phase 3: Apply the Method

For each selected method, follow its discipline:

**Divide & Conquer**: Split the problem space into independent halves.
Test which half contains the bug. Recurse on the failing half.

**Comparison**: Compare a working case vs failing case. What differs?
Environment, input, config, state, timing?

**Rollback**: Revert to a known-good state. Re-apply changes one by one.
Which change reintroduces the problem?

**Hypothesis Testing**: State "If X is true, then Y should happen when I Z."
Predict, test, confirm or refute. One variable at a time.

**Reverse Inference**: Start at the failure. Trace backward: what had to
be true just before? What had to be true before that?

**Look Inside**: Don't trust the surface output. Inspect internal state:
logs, metrics, dumps, debuggers, intermediate values.

**Single Variable**: Change exactly one factor between tests. Isolate
which variable causes the change.

**Boundary Testing**: Test edge values: empty, null, zero, max, min,
overflow. Most bugs live at boundaries.

**Reproduction**: Find the minimal steps to reproduce reliably. A bug
you can't reproduce, you can't fix.

**Elimination**: Disable/remove parts of the system. Does the problem go
away? When it does, the last thing you removed is related.

**Substitution**: Replace a suspicious component with a known-good one.
Does the problem follow the component or stay?

**Chain Tracing**: Walk the full dependency chain. The bug is often not
where the symptom appears.

**Log Injection**: Add targeted logging at decision points. What path
does execution actually take?

**Time Travel**: Compare timestamps. What changed right before the
problem started? Config deploy? Data update? Dependency release?

**Wait & Observe**: For intermittent problems, extend observation.
Sometimes you need to see the cycle.

**Layer Stripping**: Bypass outer layers, test the core directly. Does
the raw API work? Is it an integration issue?

**Outlier Analysis**: What's special about the failing cases vs passing
ones? Common pattern in the differences?

**Force Failure**: Deliberately induce the failure condition. Verify
your understanding by making it happen on demand.

**Peer Review / Rubber Ducking**: Explain the problem aloud (or in
writing) to an imaginary colleague. The act of structuring the
explanation often reveals the answer.

### Phase 4: Execute and Iterate

1. Start with your top-ranked method
2. Execute one investigation step
3. Record what you learned
4. If no progress, switch to the next method
5. If making progress, continue deepening with the current method

## Verification

- Problem is defined in writing before any investigation starts
- Selected methods have a clear rationale ("because the bug is intermittent, I'll use Reproduction + Hypothesis Testing")
- Each investigation step produces a clear outcome (confirmed/refuted a hypothesis, narrowed the scope, found the root cause)
- Root cause is identified and fix is verified before reporting done

## Pitfalls

- **Don't skip Phase 1** — writing down the problem forces precision. A vague problem statement produces vague investigation
- **Don't try all methods** — pick 1-3 and go deep. Method-hopping is a form of panic
- **Confirmation bias is the #1 trap** — actively try to *disprove* your hypothesis, not confirm it
- **The symptom is not the cause** — "null pointer exception" is a symptom, the cause might be upstream data quality or a race condition
- **If stuck after 2 methods** — step back and re-read Phase 1. Your problem definition might be wrong
- **For external users**: This skill provides methodology only. You decide which tools to use for actual investigation. The skill won't run commands for you.

---

**Self-optimization**: After using this skill, improve it based on what you learned — fix bugs, simplify steps, add edge cases, enhance verification.
