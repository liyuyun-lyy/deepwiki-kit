# Contract: Dynamic Index Generation

## Purpose

Define inputs and outputs for generating a dynamic `deepwiki/INDEX.md`.

## Inputs

- Repository structure and discovered modules
- Generated deepwiki page inventory
- Existing `deepwiki/INDEX.md` (if present) for update workflows

## Outputs

- `deepwiki/INDEX.md` with deterministic sections and links
- Summary of included sections and entries
- No `deepwiki/TOC.md` output for this feature

## Error Reporting

- Report when generated pages cannot be placed into a section
- Report when indexing yields empty output
