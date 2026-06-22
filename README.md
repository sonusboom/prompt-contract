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
* inventing files, APIs, commands, or repo behavior
* over-engineering simple changes
* refactoring unrelated code
* skipping verification
* producing vague explanations instead of usable patches
* treating planning, diagnosis, review, and implementation as the same task

Prompt Contract exists to reduce that friction.

It gives the assistant a clear operating model: understand the task, respect the repo, keep changes scoped, verify what changed, and avoid unnecessary complexity.

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
README.md                      # Project overview and usage
CHANGELOG.md                   # Release history
LICENSE                        # MIT License

examples/
  ├── python_guidelines.md      # Python style examples
  ├── bash_guidelines.md        # Bash style examples
  └── powershell_guidelines.md  # PowerShell style examples
```

The language guideline files provide examples for Python, Bash, and PowerShell output style. The main contract defines assistant behavior across planning, execution, review, diagnosis, patching, and verification.

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

For Claude Code-style workflows, a repo-level `CLAUDE.md` can be used to load these rules as workspace guidance.

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

**Keywords:** prompt engineering, LLM-assisted development, AI coding assistant, prompt contract, Claude Code, ChatGPT, coding workflow, hallucination control, scope control, developer tools, AI code generation.
