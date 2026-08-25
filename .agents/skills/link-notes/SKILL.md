---
name: link-notes
description: Find and create wikilinks between related notes in the vault. Use when asked to link notes, connect notes, find related notes, or build connections.
---

# Link Notes

## Steps

1. Read the root CONTEXT.md to get an overview of all folders and note counts.
2. Read each folder's CONTEXT.md to build a full list of notes with their summaries and tags.
3. Identify related notes by matching:
   - Shared tags across notes in different folders — cross-check with `obsidian tags counts` for tags that span folders
   - Similar keywords in summaries — `obsidian search query=<keyword>` can surface matches CONTEXT.md summaries miss
   - Explicit references (a project note mentioning a resource topic)
4. For each pair of related notes:
   a. Read both notes to confirm the relationship.
   b. Check `obsidian backlinks path=<target note>` first — skip adding the link if it's already there.
   c. Add a wikilink `[[Note Name]]` in the appropriate section:
      - In project notes: add to the `## Notes` section
      - In area notes: add to `## Active Projects` or `## Notes`
      - In resource notes: add to `## My Thoughts`
      - In MOC notes: add to `## Key Notes`
   d. Update the `modified` date on both notes with `obsidian property:set` (falls back to the Edit tool if Obsidian isn't running).
5. If three or more notes share a topic and no MOC exists for it:
   - Create a new MOC note in 03 Resources using the MOC Note template
   - Link all related notes in the MOC's `## Key Notes` section
   - Add the MOC to 03 Resources/CONTEXT.md
   - Update the root CONTEXT.md note count
6. Report all links created and any new MOCs generated.

## When Not to Use

- Do not link notes that are in 04 Archive — archived notes should not gain new connections.
- Do not create duplicate wikilinks — check with `obsidian backlinks` before adding.
