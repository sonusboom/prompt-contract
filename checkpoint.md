---
description: Capture key decisions, findings, and incomplete work from this session into a committed file in the repo. Run at the end of any session with significant decisions or discoveries.
---

# WORKFLOW — /checkpoint

You are writing a session checkpoint to `docs/decisions/` in the repo and committing it.

## Purpose

Preserve institutional knowledge that would otherwise be lost to context compaction:
- Architectural decisions and the reasoning behind them
- Incomplete implementations and their intended design
- Bug findings and root causes
- Deferred work and why it was deferred

This is NOT a summary of what was coded — the git log covers that.
This IS a record of **why**, **what was intended but not finished**, and **what was discovered**.

## Steps

1. Review the current conversation for:
   - Decisions made (architectural, design, behavioral)
   - Incomplete implementations — what was started, what remains, what the intent was
   - Findings — bugs discovered, root causes identified, surprising behaviors
   - Deferred items — what was consciously left out and why

2. Write a file to `docs/decisions/YYYY-MM-DD-<slug>.md` using today's date and a short kebab-case slug describing the session topic (e.g. `2026-04-06-schema-migration-design.md`).

3. Use this format:

```markdown
# <Session Topic> — <YYYY-MM-DD>

## Decisions

### <Decision title>
**What:** <what was decided>
**Why:** <the reason — constraint, tradeoff, user preference>
**Alternatives rejected:** <if any>

(repeat for each decision)

## Incomplete Implementations

### <Feature/area name>
**Intended design:** <what was being built and how it was supposed to work>
**What exists:** <what's in the codebase now>
**What's missing:** <what wasn't implemented and why the session stopped there>
**Pickup point:** <file:line or function where work should resume>

(repeat for each incomplete item)

## Findings

### <Finding title>
**What:** <what was discovered>
**Root cause:** <if diagnosed>
**Status:** <fixed / deferred / won't fix / needs decision>

(repeat for each finding)

## Deferred Work

- **<Item>** — <why deferred, what would be needed to resume>

## Notes
<anything that doesn't fit above but shouldn't be lost>
```

4. Only include sections that have content. Omit empty sections.

5. After writing the file, run:
   ```
   git add docs/decisions/<filename>.md
   git commit -m "docs: session checkpoint — <slug>"
   ```

6. Confirm to the user: "Checkpoint committed: docs/decisions/<filename>.md"

## Rules
- Be specific. Vague entries ("we discussed schema migration") are useless. Name the files, functions, and design choices.
- Capture intent, not implementation. The code captures what was done; this captures why and what was left.
- If something was left incomplete, say exactly where to pick it up.
- Do not pad. A checkpoint with 3 precise entries is better than one with 10 vague ones.
