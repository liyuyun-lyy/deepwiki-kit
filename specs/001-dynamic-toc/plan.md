# Implementation Plan: Dynamic Deepwiki Index

**Branch**: `001-dynamic-toc` | **Date**: 2026-01-04 | **Spec**: `specs/001-dynamic-toc/spec.md`
**Input**: Feature specification from `/specs/001-dynamic-toc/spec.md`

**Note**: This template is filled in by the `/speckit.plan` command. See `.specify/templates/commands/plan.md` for the execution workflow.

## Summary

Replace the static TOC approach with a dynamic INDEX that reflects repository
structure and content, grouped under thematic headings and ordered
deterministically. The approach is to derive Index sections and entries from
existing deepwiki page outputs and repository structure signals, omitting empty
sections and stabilizing ordering for repeatable results.

## Technical Context

<!--
  ACTION REQUIRED: Replace the content in this section with the technical details
  for the project. The structure here is presented in advisory capacity to guide
  the iteration process.
-->

**Language/Version**: N/A (spec-only repository; implementation resides elsewhere)  
**Primary Dependencies**: N/A  
**Storage**: Files (Markdown output and index artifacts)  
**Testing**: N/A (no test harness in this repo)  
**Target Platform**: Local CLI execution (offline)  
**Project Type**: Single (documentation/spec repo)  
**Performance Goals**: INDEX generation completes within 2 seconds for repos up to 1M LOC  
**Constraints**: Deterministic output; no empty placeholder sections; offline-capable  
**Scale/Scope**: Repositories with diverse module structures and sizes

## Constitution Check

*GATE: Must pass before Phase 0 research. Re-check after Phase 1 design.*

- Spec-kit workflow compatibility is preserved (commands, templates, and
  lifecycle match the kit). Status: Pass.
- `/deepwiki` commands are incremental and idempotent (`index` → `init` →
  `update`). Status: Pass.
- Init config updates are safe and reversible; no silent overwrites. Status: Pass.
- Generated content is deterministic and source-anchored with citations. Status: Pass.
- Output includes deepwiki.org parity sections and a validation checklist. Status: Pass.
- Deepwiki skill docs and examples are updated for any behavior changes. Status: Pass.

**Post-Phase 1 Re-check**: Pass. No constitution violations introduced by design artifacts.

## Project Structure

### Documentation (this feature)

```text
specs/[###-feature]/
├── plan.md              # This file (/speckit.plan command output)
├── research.md          # Phase 0 output (/speckit.plan command)
├── data-model.md        # Phase 1 output (/speckit.plan command)
├── quickstart.md        # Phase 1 output (/speckit.plan command)
├── contracts/           # Phase 1 output (/speckit.plan command)
└── tasks.md             # Phase 2 output (/speckit.tasks command - NOT created by /speckit.plan)
```

### Source Code (repository root)
<!--
  ACTION REQUIRED: Replace the placeholder tree below with the concrete layout
  for this feature. Delete unused options and expand the chosen structure with
  real paths (e.g., apps/admin, packages/something). The delivered plan must
  not include Option labels.
-->

```text
.specify/
skills/
specs/
README.md
```

**Structure Decision**: Documentation/spec-only repository. Primary delivery is
the deepwiki skill definition and assets under `skills/deepwiki/`; no
application source code is present here.
