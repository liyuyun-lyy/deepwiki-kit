---

description: "Task list for Dynamic Deepwiki Index"
---

# Tasks: Dynamic Deepwiki Index

**Input**: Design documents from `/specs/001-dynamic-toc/`
**Prerequisites**: plan.md (required), spec.md (required), research.md, data-model.md, contracts/, quickstart.md

**Tests**: Not requested in the feature specification.

**Organization**: Tasks are grouped by user story to enable independent implementation and testing of each story.

## Format: `[ID] [P?] [Story] Description`

- **[P]**: Can run in parallel (different files, no dependencies)
- **[Story]**: Which user story this task belongs to (e.g., US1, US2, US3)
- Include exact file paths in descriptions

## Path Conventions

- Skill and template work lives under `skills/deepwiki/`
- Spec updates remain under `specs/001-dynamic-toc/`

## Phase 1: Setup (Shared Infrastructure)

**Purpose**: Align scope to INDEX-only output and remove TOC expectations

- [x] T001 Confirm INDEX-only scope in `specs/001-dynamic-toc/spec.md`
- [x] T002 [P] Update plan summary and constraints for INDEX-only output in `specs/001-dynamic-toc/plan.md`
- [x] T003 [P] Update research decisions for INDEX-only output in `specs/001-dynamic-toc/research.md`

---

## Phase 2: Foundational (Blocking Prerequisites)

**Purpose**: Update skill contract to reflect dynamic INDEX generation

**⚠️ CRITICAL**: No user story work can begin until this phase is complete

- [x] T004 Remove TOC requirements and emphasize INDEX-only output in `skills/deepwiki/SKILL.md`
- [x] T005 Define dynamic INDEX sectioning rules in `skills/deepwiki/SKILL.md`

**Checkpoint**: Foundation ready - user story implementation can now begin in parallel

---

## Phase 3: User Story 1 - Dynamic Index Reflects Repo Structure (Priority: P1) 🎯 MVP

**Goal**: Generate an INDEX that reflects repository structure and content.

**Independent Test**: Generate INDEX for a repo with multiple modules and verify module entries are present and grouped.

### Implementation for User Story 1

- [x] T006 [US1] Update INDEX template guidance in `skills/deepwiki/SKILL.md`
- [x] T007 [US1] Update overview template guidance to reference dynamic INDEX sections in `skills/deepwiki/templates/overview.md`
- [x] T008 [US1] Update architecture template guidance to align with dynamic INDEX grouping in `skills/deepwiki/templates/architecture.md`
- [x] T009 [US1] Add dynamic INDEX example snippet in `skills/deepwiki/examples/overview-example.md`

**Checkpoint**: User Story 1 should be fully functional and testable independently

---

## Phase 4: User Story 2 - Hierarchical Grouping in Index (Priority: P2)

**Goal**: Provide hierarchical INDEX grouping by themes.

**Independent Test**: Verify INDEX example shows sections like Build/Development and Architecture when applicable.

### Implementation for User Story 2

- [x] T010 [US2] Document thematic grouping rules in `skills/deepwiki/SKILL.md`
- [x] T011 [US2] Update data-flow template to reference thematic grouping in `skills/deepwiki/templates/data-flow.md`
- [x] T012 [US2] Add grouped INDEX example in `skills/deepwiki/examples/overview-example.md`

**Checkpoint**: User Stories 1 AND 2 should both work independently

---

## Phase 5: User Story 3 - Deterministic Index Ordering (Priority: P3)

**Goal**: Ensure INDEX order is deterministic for identical repo snapshots.

**Independent Test**: Verify documented ordering rules and confirm examples use stable ordering.

### Implementation for User Story 3

- [x] T013 [US3] Document deterministic ordering rules in `skills/deepwiki/SKILL.md`
- [x] T014 [US3] Add ordering note to `specs/001-dynamic-toc/quickstart.md`

**Checkpoint**: All user stories should now be independently functional

---

## Phase 6: Polish & Cross-Cutting Concerns

**Purpose**: Consistency across docs and parity checks

- [x] T015 [P] Update `README.md` to remove TOC references and note dynamic INDEX behavior
- [x] T016 [P] Update parity checklist note in `specs/001-dynamic-toc/spec.md`
- [x] T017 [P] Add contract notes for INDEX-only output in `specs/001-dynamic-toc/contracts/index-generation.md`

---

## Dependencies & Execution Order

### Phase Dependencies

- **Setup (Phase 1)**: No dependencies - can start immediately
- **Foundational (Phase 2)**: Depends on Setup completion - BLOCKS all user stories
- **User Stories (Phase 3+)**: All depend on Foundational phase completion
- **Polish (Final Phase)**: Depends on all desired user stories being complete

### User Story Dependencies

- **User Story 1 (P1)**: Can start after Foundational (Phase 2) - No dependencies on other stories
- **User Story 2 (P2)**: Can start after Foundational (Phase 2) - Builds on US1 INDEX scope
- **User Story 3 (P3)**: Can start after Foundational (Phase 2) - Shares ordering rules across INDEX

### Within Each User Story

- Update skill rules before examples
- Examples and templates must align with skill guidance

### Parallel Opportunities

- T002 and T003 can run in parallel
- T006 and T008 can run in parallel
- T015, T016, T017 can run in parallel

---

## Parallel Example: User Story 1

```bash
Task: "Update overview template guidance to reference dynamic INDEX sections in skills/deepwiki/templates/overview.md"
Task: "Update architecture template guidance to align with dynamic INDEX grouping in skills/deepwiki/templates/architecture.md"
```

---

## Implementation Strategy

### MVP First (User Story 1 Only)

1. Complete Phase 1: Setup
2. Complete Phase 2: Foundational
3. Complete Phase 3: User Story 1
4. **STOP and VALIDATE**: Confirm INDEX reflects repo structure

### Incremental Delivery

1. Complete Setup + Foundational → Foundation ready
2. Add User Story 1 → Validate INDEX structure → Demo
3. Add User Story 2 → Validate hierarchical grouping
4. Add User Story 3 → Validate deterministic ordering rules
5. Final polish for docs and parity
