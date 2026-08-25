---
name: weekly-review
description: Run the weekly review checklist for the vault. Use when asked to do a weekly review, maintain the vault, or check vault health.
---

# Weekly Review

## Steps

1. **Empty the Inbox**: Read 00 Inbox/CONTEXT.md's top-level note table. For each note listed, run the inbox-triage procedure (read the inbox-triage skill for detailed steps). Report how many notes were triaged and where they went. This does not include `00 Inbox/Daily Plan/` — see step 2.

2. **Summarize the week's Daily Plan notes**: Read `00 Inbox/Daily Plan/CONTEXT.md` and identify Todo notes created in the last 7 days. For each, read its `## Top 3` and `## Regular Checklist` sections and report a summary-only rollup:
   - Top 3 completion rate across the week (e.g. "9/12 completed")
   - Which Regular Checklist items were skipped repeatedly
   - Do not flag, carry forward, or archive anything here — this step just reports.

3. **Review active projects**: Read 01 Projects/CONTEXT.md. For each note with status "active":
   - Read the note and check if the Outcome section is filled in
   - Check if Next Actions has at least one item
   - Flag any project missing an outcome or next actions

4. **Check areas**: Read 02 Areas/CONTEXT.md. For each area note:
   - Check the modified date — flag areas not updated in over 30 days
   - Check if Active Projects section has links — flag areas with no linked projects

5. **Archive stale items**: Scan 01 Projects for notes with status "done". Move them to 04 Archive, update their status to "archived", and update both CONTEXT.md files.

6. **Report summary**: List all changes made during the review:
   - Notes triaged from Inbox (count and destinations)
   - Daily Plan weekly rollup (Top 3 completion rate, frequently skipped checklist items)
   - Projects flagged for missing outcomes or next actions
   - Areas flagged as neglected
   - Notes archived
   - Updated CONTEXT.md files

## When Not to Use

- Do not run a weekly review on a vault with no notes — there is nothing to review.
