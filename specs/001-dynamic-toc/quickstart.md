# Quickstart: Dynamic Deepwiki Index

## Goal

Verify that `deepwiki/INDEX.md` is dynamically generated based on repository structure and is deterministic across runs.

## Prerequisites

- A repository with multiple modules or distinct areas (build, runtime, services)
- Deepwiki generation enabled

## Steps

1. Run `/deepwiki:index` on a repo with multiple modules.
2. Open `deepwiki/INDEX.md` and confirm sections match repository structure.
3. Ensure no empty placeholder sections are present.
4. Run `/deepwiki:index` again without changes and verify the INDEX is identical.

## Expected Results

- INDEX contains grouped sections and links relevant to the repo.
- Output is deterministic across runs.
- Section and entry ordering remains stable for identical repo snapshots.
