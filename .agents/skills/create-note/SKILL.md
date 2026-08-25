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
2. Match the note type to its template:
   - inbox → Templates/Inbox Note.md
   - project → Templates/Project Note.md
   - area → Templates/Area Note.md
   - resource → Templates/Resource Note.md
   - moc → Templates/MOC Note.md
3. Create the new note file in the destination folder:
   - Use title case with spaces for the filename
   - Run `obsidian templater:create-from-template template="Templates/<Type> Note.md" file="<destination path>"` — this resolves `<% %>` Templater syntax and fills in dates automatically.
     - `tp.file.cursor(N)` placeholders are left as literal text (they mark cursor position for interactive use, not a value) — replace them with real content in the next step.
   - Fill in frontmatter fields from the user's request with `obsidian property:set` (falls back to the Edit tool if Obsidian isn't running — see AGENTS.md's Obsidian CLI section), and replace any leftover `tp.file.cursor(N)` text in the body with an Edit.
4. Add the new note to the destination folder's CONTEXT.md.
5. Update the root CONTEXT.md note count.
6. Report the created note's filename and location.

## When Not to Use

- Do not create notes directly in 04 Archive — that folder is for moved items only.
- Do not create notes in Templates/ — those are read-only.
