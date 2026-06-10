# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Structure

This is a collection of **Claude Code skills** — markdown files loaded via `Skill` tool. Each skill lives in its own directory with `SKILL.md` as the entry point.

```
think-skills/
├── assess-me/                  # Self-cognition audit — catch blind spots
│   └── SKILL.md
├── reframe/                    # Problem reframing — fresh perspective on stuck problems
│   └── SKILL.md
└── debug-root-cause/           # Systematic root cause analysis methodology
    ├── SKILL.md
    └── references/
        └── rca-methods.md      # 20 RCA methods reference
```

## Auto-Trigger Rules (MANDATORY)

These rules apply to every session. Follow them without waiting for user instructions.

### Rule 1: Error → debug-root-cause
When any tool (Bash/Read/Write/Edit) returns an error or unexpected result:
1. STOP — do NOT retry, grep, or guess
2. Call `Skill({skill: "debug-root-cause"})`
3. Follow the skill's steps to investigate systematically

### Rule 2: Checkpoint → assess-me
Every 15 tool calls:
1. Pause
2. Call `Skill({skill: "assess-me"})`
3. Do the write-read-analyze cycle
4. Continue based on findings

### Rule 3: Stuck → reframe
When 3+ consecutive attempts fail with the same result or you're going in circles:
1. Call `Skill({skill: "reframe"})`
2. Write compressed summary, read it back, do fresh analysis
3. Continue with the reframe's conclusion

### Rule 4: Chain triggering
- After assess-me: if blocker is "unclear root cause" → run debug-root-cause next
- After assess-me: if blocker is "confused direction" → run reframe next
- After reframe: if root cause is still unclear → run debug-root-cause next
- After debug-root-cause: if investigation stalls → run reframe next

## Skill Anatomy

Each `SKILL.md` follows this structure:

1. **Frontmatter** — `name` (used to invoke via `/`), `description` (trigger conditions)
2. **Action** — the write-temp-file → read-back mechanism
3. **Instructions** — specific phases and questions
4. **Pitfalls** — common mistakes to avoid

## Creating a New Skill

- Create `<skill-name>/SKILL.md` with frontmatter (`name`, `description`), action (write-read cycle), instructions, and pitfalls
- Add reference materials under `<skill-name>/references/` if needed
- Each skill should be self-contained — loaded atomically by the Skill tool

## No Build / Test Tooling

This repo is pure documentation. No build system, package manager, linter, or test runner.
