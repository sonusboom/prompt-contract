![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)
![LLM Contract](https://img.shields.io/badge/Prompt%20Contract-Strict-orange.svg)
![Status](https://img.shields.io/badge/Maintained-yes-blue.svg)

# Prompt Contract

Prompt Contract is a lightweight ruleset for disciplined LLM-assisted development.

It defines how an AI coding assistant should plan, execute, patch, verify, and avoid scope drift while working in a codebase. The goal is simple: make LLM coding help more predictable, conservative, and useful.

This project started from my own need to communicate more clearly with AI coding assistants while learning and building scripts. I wanted outputs that felt closer to what a careful developer would produce: small changes, clear reasoning, no invented repo facts, no unnecessary abstractions, and no walls of filler text.

Prompt Contract v6 moves the project from a ChatGPT-specific scripting contract to a broader development workflow contract that can be used with different LLM coding tools.

---

## Why This Exists

LLM coding assistants can be powerful, but they often drift in ways that create extra work:

* implementing before understanding the request
* inventing files, APIs, commands, paths, or repo behavior
* over-engineering simple changes
* refactoring unrelated code
* skipping verification
* producing vague explanations instead of usable patches
* treating planning, diagnosis, review, and implementation as the same task
* losing important decisions when the session context gets compacted or reset

Prompt Contract exists to reduce that friction.

It gives the assistant a clear operating model: understand the task, respect the repo, keep changes scoped, verify what changed, and preserve important development context when needed.

---

## What Prompt Contract v6 Emphasizes

Prompt Contract v6 focuses on development behavior more than style alone.

Core expectations include:

* determine whether the request is analysis, planning, diagnosis, review, or execution before acting
* prefer correctness and maintainability over cleverness
* do not invent APIs, file contents, paths, commands, or repo facts
* keep changes small and purposeful
* avoid architectural drift
* avoid speculative abstractions for hypothetical future needs
* use file editing tools when available
* otherwise provide a unified diff or patch
* always list touched files
* avoid unrelated formatting or cosmetic churn
* include deterministic verification commands when logic changes
* prefer the repo’s canonical quality gate when available

---

## Supported Modes

Prompt Contract v6 supports explicit modes for controlling assistant behavior.

```text
MODE: PLAN_ONLY
```

Scope the request, identify assumptions, ask only required questions, present options, and recommend a path. Do not implement.

```text
MODE: EXECUTE
```

Implement the requested change. Still ask for clarification if required for correctness.

```text
MODE: REVIEW_ONLY
```

Review existing code, docs, or design. Do not implement unless explicitly requested.

```text
MODE: DIAGNOSE_ONLY
```

Debug or root-cause an issue and provide next steps. Do not implement unless explicitly requested.

If no mode is provided and the intent is ambiguous, the assistant should default to planning first rather than implementing immediately.

---

## What’s Included

```text
prompt_contract_v6.md          # Main LLM-assisted development contract
checkpoint.md                  # Claude workflow for saving session decision checkpoints
README.md                      # Project overview and usage
CHANGELOG.md                   # Release history
LICENSE                        # MIT License

examples/
  ├── python_guidelines.md      # Python style examples
  ├── bash_guidelines.md        # Bash style examples
  └── powershell_guidelines.md  # PowerShell style examples
```

The main contract defines assistant behavior across planning, execution, review, diagnosis, patching, and verification.

The `checkpoint.md` file is a standalone Claude workflow for preserving important session context that should not be lost between development sessions.

The language guideline files provide examples for Python, Bash, and PowerShell output style.

---

## How to Use It

### General LLM Use

Paste the contents of `prompt_contract_v6.md` into a new LLM session before starting development work.

Then provide your task and, when useful, include a mode:

```text
MODE: PLAN_ONLY

Review this repo structure and recommend how to organize the CLI commands.
```

```text
MODE: EXECUTE

Patch the argument parsing bug and provide verification commands.
```

```text
MODE: REVIEW_ONLY

Review this script for maintainability and scope drift.
```

### Repo or Workspace Use

For tools that support persistent project instructions, place the contract in the expected workspace instruction file or reference it from that file.

For Claude Code-style workflows, a repo-level instruction file can be used to load these rules as workspace guidance.

The contract is most useful when paired with a real repository, because it tells the assistant to read repo facts instead of inventing them.

---

## Checkpoint Workflow

`checkpoint.md` provides a standalone Claude workflow called `/checkpoint`.

Use it at the end of a meaningful development session when important decisions, findings, incomplete work, or deferred items need to be preserved in the repository.

This workflow captures context that the git log does not explain.

The git history records what changed.

The checkpoint records why decisions were made, what was discovered, what remains unfinished, and where future work should resume.

### What It Captures

The checkpoint workflow is intended to preserve:

* architectural, design, or behavioral decisions
* reasoning behind those decisions
* alternatives that were considered or rejected
* incomplete implementations and intended design
* current pickup points for unfinished work
* bug findings and root causes
* consciously deferred work and why it was deferred
* important notes that should survive context loss or session compaction

It is not intended to summarize every code change.

A short checkpoint with a few precise entries is better than a long vague summary.

### How It Works

When invoked, `/checkpoint` writes a Markdown file to:

```text
docs/decisions/YYYY-MM-DD-<slug>.md
```

The generated checkpoint includes only the sections that have useful content:

```text
Decisions
Incomplete Implementations
Findings
Deferred Work
Notes
```

After writing the checkpoint file, the workflow stages and commits it with a message like:

```text
docs: session checkpoint — <slug>
```

### When to Use It

Use `/checkpoint` after sessions that include meaningful context worth preserving, such as:

* choosing one design path over another
* deciding not to implement something yet
* stopping in the middle of an implementation
* discovering the root cause of a bug
* identifying a future pickup point in a specific file or function
* documenting why a behavior, workflow, or architecture choice exists

Do not use it for routine summaries of every small code change. The git log already covers that.

### Requirements

The checkpoint workflow assumes the assistant is operating in an environment that can:

* read the current conversation
* write files into the repository
* create files under `docs/decisions/`
* run `git add`
* run `git commit`

If you are only editing files through the GitHub website, you can still store `checkpoint.md` in the repo, but the workflow itself needs a Claude/code-agent workspace with file and git access to run automatically.

---

## Design Principles

Prompt Contract is intentionally conservative.

It is not meant to turn an LLM into an autonomous developer that redesigns your project. It is meant to keep the assistant bounded, useful, and predictable.

The contract favors:

* small patches over large rewrites
* explicit assumptions over hidden guesses
* repo facts over hallucinated context
* verification over confidence
* maintainability over cleverness
* direct answers over filler
* planning before execution when intent is unclear
* preserving important decisions before session context is lost

---

## Relationship to Language Guidelines

Prompt Contract v6 defines how the assistant should behave.

The example guideline files define what good output should look like for specific languages.

Python examples emphasize:

* `snake_case`
* focused functions
* `argparse`
* `main()` entrypoints

Bash examples emphasize:

* `set -euo pipefail`
* short lowercase variables
* simple functions
* flag-based behavior instead of menus

PowerShell examples emphasize:

* approved verbs
* typed parameters
* structured output
* clear `param()` blocks

These examples are supporting guidance, not a replacement for the main contract.

---

## Important Note

Prompt Contract is a user/workspace-level ruleset. It does not override higher-priority system, platform, safety, tool, or environment constraints used by a given LLM provider.

The contract should be treated as the expected working agreement for the assistant within the limits of the tool or platform being used.

---

## License

MIT License.

See the `LICENSE` file for details.

---

## Contributions

Pull requests and refinements are welcome.

Good contributions should preserve the project’s core goals:

* keep the contract concise
* avoid unnecessary complexity
* prefer practical rules over theory
* do not add model-specific claims unless clearly documented
* preserve the plan-first, low-drift development workflow
* keep standalone workflows focused and purpose-built

**Keywords:** prompt engineering, LLM-assisted development, AI coding assistant, prompt contract, Claude Code, ChatGPT, coding workflow, hallucination control, scope control, checkpoint workflow, development notes, developer tools, AI code generation.
