<!--
Sync Impact Report
- Version change: 0.1.0 -> 0.2.0
- Modified principles: Added Continuous Skill Evolution
- Added sections: None
- Removed sections: None
- Templates requiring updates:
  - ✅ .specify/templates/plan-template.md
  - ✅ .specify/templates/spec-template.md
  - ✅ .specify/templates/tasks-template.md
  - ✅ .specify/templates/checklist-template.md
- Follow-up TODOs:
  - TODO(RATIFICATION_DATE): original adoption date not recorded
-->
# deepwiki-kit Constitution

## Core Principles

### I. Spec-Kit Compatible Workflow
Every workflow and artifact MUST align with spec-kit conventions (command naming,
template usage, and feature lifecycle). The kit MUST remain interoperable with
spec-kit-style prompts and templates unless a breaking change is explicitly
ratified. Rationale: users should be able to reuse spec-kit habits and assets
without relearning the flow.

### II. Incremental CLI Commands
The Codex CLI MUST expose `/deepwiki` and progressive subcommands such as
`/deepwiki:index`, `/deepwiki:init`, and `/deepwiki:update`. Each command MUST be
idempotent, composable, and safe to run repeatedly; `/deepwiki:index` MUST
produce the inputs required for `/deepwiki:init` and `/deepwiki:update`.
Rationale: users need a predictable, stepwise path for indexing, generation, and
updates.

### III. Config-Driven Initialization
Initialization MUST add or update Codex configuration automatically with clear,
reversible changes and no silent overwrites. If existing config is present, the
init flow MUST merge safely or require explicit confirmation. Rationale: safe,
repeatable onboarding is required for a kit meant to be installed by end users.

### IV. Deterministic, Source-Anchored Generation
Deepwiki output MUST be derived from repository sources and MUST cite the source
paths that support each generated section. The generator MUST be deterministic
given the same repository snapshot and configuration; missing information MUST
be surfaced as TODOs instead of invented content. Rationale: trust and
repeatability are core to documentation generation.

### V. Quality Parity with deepwiki.org
Generated content MUST target the structure and clarity of deepwiki.org,
including an index, architecture overview, module or service breakdowns, API or
contract summaries, and usage guides as applicable. A validation checklist MUST
be produced to confirm coverage and highlight gaps. Rationale: output quality
defines adoption and credibility.

### VI. Continuous Skill Evolution
The deepwiki skill definition and supporting assets MUST stay synchronized with
actual CLI behavior, templates, and expected outputs. Any behavior change MUST
update the skill documentation and examples before release. Rationale: users
depend on the skill as the authoritative workflow and it must remain current.

## Scope & Deliverables
The kit MUST deliver a documented installation flow, an init command that wires
Codex configuration, and CLI commands to index, generate, and update deepwiki
content. Output MUST be written to a single, documented root (for example,
`deepwiki/` or `docs/deepwiki/`) and updates MUST be applied in place with clear
diffs. The generator MUST operate on local repository content by default and
MUST NOT require network access unless explicitly configured.

## Workflow & Quality Gates
Development MUST follow the sequence: install kit → run init → run
`/deepwiki:index` → run `/deepwiki:init` → iterate with `/deepwiki:update`.
Each generation run MUST emit a summary of inputs, outputs, and any TODOs.
Before release, validate that: command re-runs are idempotent, configuration
changes are safe, and generated content includes source citations and parity
sections. Any deviations from the constitution MUST be documented in the plan's
Constitution Check and reviewed.

## Governance
This constitution supersedes all other development guidance. Amendments MUST be
proposed via PR, include a rationale and migration notes, and receive maintainer
approval. Versioning follows semantic versioning: MAJOR for breaking governance
changes, MINOR for new principles or requirements, PATCH for clarifications.
All PRs MUST include a Constitution Check in the plan or checklist, and reviews
MUST confirm compliance before merge.

**Version**: 0.2.0 | **Ratified**: TODO(RATIFICATION_DATE): original adoption date not recorded | **Last Amended**: 2026-01-04
