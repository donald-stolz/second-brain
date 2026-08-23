---
name: create-note
description: Create a new note in the vault using the correct PARA template. Use when asked to create a note, add a note, start a new project, or capture something.
---

# Create Note

## Steps

1. Determine the note type from the user's request:
   - Quick capture → inbox (place in 00 Inbox)
   - Has outcome and deadline → project (place in 01 Projects)
   - Ongoing responsibility → area (place in 02 Areas)
   - Reference material → resource (place in 03 Resources)
   - Topic index → moc (place in 03 Resources)
2. Read the matching template from Templates/ to get the correct structure:
   - inbox → Templates/Inbox Note.md
   - project → Templates/Project Note.md
   - area → Templates/Area Note.md
   - resource → Templates/Resource Note.md
   - moc → Templates/MOC Note.md
3. Create the new note file in the destination folder:
   - Use title case with spaces for the filename
   - Replace Templater syntax with actual values:
     - `<% tp.date.now("YYYY-MM-DD") %>` → today's date
     - `<% tp.file.cursor(1) %>` → leave blank for user
     - `<% tp.file.cursor(2) %>` → leave blank for user
     - `<% "---" %>` → `---`
   - Fill in frontmatter fields from the user's request
4. Add the new note to the destination folder's CONTEXT.md.
5. Update the root CONTEXT.md note count.
6. Report the created note's filename and location.

## When Not to Use

- Do not create notes directly in 04 Archive — that folder is for moved items only.
- Do not create notes in Templates/ — those are read-only.
