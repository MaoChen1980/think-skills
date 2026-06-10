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

## Skill Anatomy

Each `SKILL.md` follows this structure:

1. **Frontmatter** — `name` (used to invoke via `/`), `description` (trigger conditions)
2. **When to Use** — situations that warrant this skill
3. **Steps** — phased procedure with verification checkpoints
4. **Pitfalls** — common mistakes to avoid
5. **`Self-optimization` footer** — iterate on the skill after each use

Reference files go under `references/` within the skill's directory.

## Creating a New Skill

- Create `skills/<skill-name>/SKILL.md` with frontmatter (`name`, `description`), procedure steps, verification criteria, and pitfalls
- Add reference materials under `<skill-name>/references/` if needed
- Each skill should be self-contained — the SKILL.md is loaded atomically by Claude Code

## No Build / Test Tooling

This repo is pure documentation. There is no build system, package manager, linter, or test runner. No commands to run.
