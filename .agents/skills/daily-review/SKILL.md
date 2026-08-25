---
name: daily-review
description: Review today's (or the most recent) daily Todo note and help plan tomorrow's. Use when asked to do a daily review, check today's todos, review the day, or plan tomorrow.
---

# Daily Review

## Steps

1. **Find the target note**: List `00 Inbox/Daily Plan/` for files matching `Todo-YYYY-MM-DD.md`.
   - If a file for today's date exists, that's the target.
   - Otherwise, use the most recent file by date.
   - If the folder has no Todo notes at all, skip straight to step 4 and create **today's** note instead of tomorrow's — there is nothing to review yet.

2. **Review (read-only)**: Read the target note and report to the user:
   - Which `## Top 3` items are checked vs. still open
   - Which `## Regular Checklist` items are checked vs. still open
   - Do not edit the note in this step — checkboxes reflect what the user ticked during the day, not something the agent infers or corrects.

3. **Ask if they want to plan tomorrow.** If yes, continue; if not, stop after the review report.

4. **Plan tomorrow**: Create `Todo-{tomorrow's date}.md` in `00 Inbox/Daily Plan/` from `Templates/Todo Note.md`:
   - Run `obsidian templater:create-from-template template="Templates/Todo Note.md" file="00 Inbox/Daily Plan/Todo-{tomorrow's date}.md"` — this resolves the Templater date syntax automatically (falls back to a manual copy via the Edit/Write tools if Obsidian isn't running — see AGENTS.md's Obsidian CLI section).
   - Fill `created`/`modified` with tomorrow's date if the template command didn't already, `status: active`, leave `summary`/`tags` for the user — use `obsidian property:set` for these.
   - Ask the user for any calendar events or other Todos they want to flag for tomorrow — this vault doesn't track a calendar, so the user tells you these directly. Capture what they give you as additional candidates.
   - For `## Top 3`: propose the incomplete Top 3 items carried over from the reviewed note (step 2), plus any events/Todos the user just gave you, as suggestions in chat. Only write them into the file once the user confirms or edits them — never write suggestions silently.
   - Once the user confirms that initial batch, offer to scan for more candidates: read `01 Projects/CONTEXT.md`, check notes with `status: active`, and pull from their `## Next Actions` sections as additional suggestions. Only do this scan if the user accepts the offer.
   - Fill `## Events` with any calendar events the user gave you (plain list, not checkboxes — they're fixed-time items, not tasks to check off).
   - Reset `## Regular Checklist` to the template's placeholder items, plus any confirmed Todos from the scan/conversation.
   - Leave `## Notes` blank, aside from any flagged follow-ups (e.g. overdue items surfaced during the scan) the user wants noted.

5. **Close out the reviewed note**: Once tomorrow's note is written, update the reviewed note's `status` to `done` and bump its `modified` field to today's date, using `obsidian property:set` (falls back to the Edit tool if Obsidian isn't running). This is the only write to the reviewed note in the whole flow.

6. **Update indices**:
   - Add a row for the new note to `00 Inbox/Daily Plan/CONTEXT.md`.
   - Update the reviewed note's row status in the same file.
   - Update the note count in the "Subfolders" table of `00 Inbox/CONTEXT.md`.

7. **Report a summary**: what was reviewed (completion counts), and what got planned for tomorrow.

## When Not to Use

- Do not archive or move Todo notes out of `00 Inbox/Daily Plan/` — they stay there permanently as a running log (see `weekly-review`'s inbox sweep, which explicitly skips this folder).
- Do not run this against `00 Inbox/daily-notes/` — that's a separate, unstructured capture folder unrelated to Todo notes.
