---
name: update-index
description: Regenerate all CONTEXT.md files by scanning every note's frontmatter. Use when the index is out of sync, after manual edits, or when asked to rebuild the index.
---

# Update Index

## Steps

1. For each PARA folder (00 Inbox, 01 Projects, 02 Areas, 03 Resources, 04 Archive):
   a. List all Markdown files in the folder (excluding CONTEXT.md and README.md).
   b. For each file, read the YAML frontmatter and extract: type, status, summary.
   c. Build a Markdown table with columns: Filename, Type, Status, Summary.
   d. Write the table to that folder's CONTEXT.md, replacing the existing table content.
   e. Count the total number of notes in the folder.
2. Update the root CONTEXT.md:
   a. For each folder row, update the Notes count column with the actual count from step 1e.
   b. Update the "Last updated" date to today.
3. Report:
   - Total notes per folder
   - Any notes found with missing or malformed frontmatter (list filenames)
   - Total notes across the vault

## When Not to Use

- Do not run on a vault with no notes — the result would be empty tables, which is valid but pointless.
