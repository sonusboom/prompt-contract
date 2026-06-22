# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/)
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [2.0.0] - 2026-06-22

### Changed

* Replaced Prompt Contract v5 with Prompt Contract v6.
* Reframed the project from a ChatGPT-specific scripting contract to a broader LLM-assisted development contract.
* Updated the contract to distinguish between planning, review, diagnosis, and execution.
* Changed the default repository-editing workflow from full-file rewrites to file editing tools when available, or unified diff/patch output when not available.
* Updated scope-control rules to emphasize small, purposeful changes and no architectural drift.
* Improved clarification behavior so the assistant asks only when required for correctness.
* Updated verification expectations for logic changes and repo quality gates.
* Refined the README to describe Prompt Contract v6, supported modes, usage, and design principles.

### Added

* Added explicit mode support:

  * `PLAN_ONLY`
  * `EXECUTE`
  * `REVIEW_ONLY`
  * `DIAGNOSE_ONLY`
* Added execution-gate rules to prevent implementation from starting before the task type is understood.
* Added workspace contract guidance for repo-specific artifacts such as code indexes.
* Added decision defaults for ambiguous implementation requests.
* Added stronger rules against inventing APIs, file contents, commands, paths, or repository facts.

### Fixed

* Corrected outdated README references to Prompt Contract v5.
* Corrected project positioning so the contract is no longer described as ChatGPT-only.
* Clarified that language guideline files are supporting examples rather than the main contract.

## [1.0.0] - 2025-11-21

### Added

* Initial public release of the Prompt Contract v5.
* Summarized `README.md` describing purpose, usage, and structure.
* `LICENSE` file using the MIT License.
* `examples/` directory with language-specific guideline files:

  * `python_guidelines.md`
  * `bash_guidelines.md`
  * `powershell_guidelines.md`
* Release notes for v1.0.0 describing scope, audience, and future direction.
