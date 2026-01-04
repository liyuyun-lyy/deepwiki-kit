# Data Model: Dynamic Deepwiki Index

## Entities

### IndexSection

- **Description**: A thematic grouping of INDEX entries derived from repo structure.
- **Fields**:
  - `title`: Display label for the section.
  - `order`: Deterministic order value.
  - `entries`: Collection of `IndexEntry` items.
- **Validation Rules**:
  - Sections with no entries are omitted.

### IndexEntry

- **Description**: A link to a deepwiki page within the INDEX.
- **Fields**:
  - `label`: Display label for the entry.
  - `path`: Relative path to the deepwiki page.
  - `order`: Deterministic order value.
- **Validation Rules**:
  - All generated deepwiki pages must appear in at least one section.

## Relationships

- **IndexSection** 1 → N **IndexEntry**
