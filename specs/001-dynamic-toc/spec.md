# Feature Specification: Dynamic Deepwiki Index

**Feature Branch**: `001-dynamic-toc`  
**Created**: 2026-01-04  
**Status**: Draft  
**Input**: User description: "[index.jpg 682x1552] 请参考这个图片中的目录，我觉得目前的目录太死板和简单了，我希望更加动态地根据实际仓库来生成目录。"

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Dynamic Index Reflects Repo Structure (Priority: P1)

As a documentation reader, I want the generated INDEX to reflect the actual repository structure so I can navigate to the sections that matter most for this codebase.

**Why this priority**: The current TOC is too static; accurate navigation is the core value of a deepwiki.

**Independent Test**: Generate deepwiki for a repo with multiple modules and verify INDEX sections mirror those modules.

**Acceptance Scenarios**:

1. **Given** a repository with multiple top-level modules, **When** the deepwiki INDEX is generated, **Then** the INDEX includes module-specific entries grouped under appropriate sections.
2. **Given** a repository with minimal structure, **When** the INDEX is generated, **Then** the INDEX includes only relevant sections and avoids empty placeholders.

---

### User Story 2 - Hierarchical Grouping in Index (Priority: P2)

As a documentation reader, I want a hierarchical INDEX grouped by themes (overview, build, architecture, modules) so I can quickly scan and jump to a topic.

**Why this priority**: The screenshot indicates a multi-level TOC that helps users scan large repos.

**Independent Test**: Generate deepwiki for a repo with build scripts and services and confirm INDEX groups those topics under their sections.

**Acceptance Scenarios**:

1. **Given** a repository with build and runtime artifacts, **When** the INDEX is generated, **Then** entries are grouped under sections like Build/Development and Architecture.

---

### User Story 3 - Deterministic Index Ordering (Priority: P3)

As a documentation maintainer, I want INDEX generation to be deterministic so it remains stable across repeated runs on the same repo.

**Why this priority**: Stable output avoids noisy diffs and builds trust in the generator.

**Independent Test**: Run generation twice on the same repo snapshot and verify the INDEX is identical.

**Acceptance Scenarios**:

1. **Given** the same repo snapshot, **When** INDEX generation runs multiple times, **Then** the INDEX order and grouping are identical.

---

### Edge Cases

- What happens when a repo has only a README and no recognizable modules?
- How does the system handle very large repos with dozens of modules?
- What happens when module detection yields ambiguous groupings?

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: System MUST generate INDEX sections based on detected repository structure and content.
- **FR-002**: System MUST omit INDEX sections that have no relevant content for the repo.
- **FR-003**: System MUST group INDEX entries under thematic headings (e.g., overview, build, architecture, modules) when applicable.
- **FR-004**: System MUST include links to all generated deepwiki pages in the INDEX.
- **FR-005**: System MUST produce a deterministic INDEX for the same repo snapshot.
- **FR-006**: System MUST preserve spec-kit command workflow and update behavior for `/deepwiki:index`.
- **FR-007**: System MUST keep output source-anchored with citations in generated pages.
- **FR-008**: System MUST generate a validation checklist confirming deepwiki.org parity sections.
- **FR-009**: System MUST update deepwiki skill docs and examples when INDEX behavior changes.

### Key Entities *(include if feature involves data)*

- **Index Entry**: A link to a deepwiki page with display label and hierarchy.
- **Index Section**: A grouping of index entries based on repository themes.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: For repos with modules, 100% of generated module pages appear in the INDEX.
- **SC-002**: INDEX generation produces identical output across repeated runs on the same repo snapshot.
- **SC-003**: At least 90% of users report the INDEX reflects the repo structure and is easy to navigate (survey).
- **SC-004**: INDEX generation completes within 2 seconds for repos up to 1M LOC.

## Assumptions

- The generator can detect modules and build artifacts using repository file structure and existing indexing outputs.
- The INDEX remains Markdown-based and lives at `deepwiki/INDEX.md`.

## Notes

- The deepwiki parity checklist must explicitly confirm dynamic INDEX coverage and omit TOC requirements.
