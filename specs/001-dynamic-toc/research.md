# Research: Dynamic Deepwiki Index

## Decision 1: Replace TOC with a dynamic INDEX only

- **Decision**: Only generate `deepwiki/INDEX.md` and drop the TOC requirement for this feature.
- **Rationale**: User request explicitly removes the TOC and focuses on a richer, dynamic INDEX.
- **Alternatives considered**: Keep TOC alongside the INDEX. Rejected due to explicit requirement and redundancy.

## Decision 2: Derive Index sections from detected repo structure

- **Decision**: Use repository structure and generated page inventory to group INDEX entries under thematic sections.
- **Rationale**: Aligns navigation with actual content and avoids static placeholders.
- **Alternatives considered**: Fixed section list with empty placeholders. Rejected due to user feedback about being too static.

## Decision 3: Deterministic ordering rules

- **Decision**: Use stable sorting for sections and entries to ensure repeatable output.
- **Rationale**: Prevents noisy diffs and improves trust.
- **Alternatives considered**: Source-order or filesystem-order only. Rejected due to inconsistencies across environments.
