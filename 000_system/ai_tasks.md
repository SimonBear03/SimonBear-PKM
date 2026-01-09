# ai_tasks

This file describes higher-level tasks for AI agents. Tasks here decide:
- when to create or update certain notes,
- what inputs are needed (for example, date),
- which template to use from 000_system/templates/.

Templates contain ai_instructions for how to ask questions and structure the note. This file focuses on WHEN and WHICH workflows to run.

---

## task: journal_entry_for_date

Trigger

The user wants to reflect on a day or write a journal entry, for example:
- "let's do today's journal"
- "help me journal about today"
- "I want to write about [date]"

Inputs

- date:
  - If the user provides a date, use it.
  - Otherwise, assume "today" in the user's local time, but confirm if there is any ambiguity.

Process

1. Confirm the date with the user if needed.
2. Start a short, adaptive reflection conversation:
   - Begin with 1 or 2 broad prompts about how the day felt and what stood out.
   - Ask a few more questions (total around 3–6 questions), choosing follow-ups based on what the user seems to care about (emotions, events, insights, gratitude, intentions).
3. After there is enough information, use the journal template:
   - Template path: 000_system/templates/journal_entry_template.md
   - Follow its ai_instructions block to structure the note and fill the sections.
4. Create or update the note:
   - Path: 333_journ/<date>_journal.md
   - Include minimal YAML frontmatter (title, date, tags) as described in the template.
   - Set YAML `title` to the note’s H1 (for example: `<date> – journal`) unless the user wants a different title.

Notes

- Do not automatically create a daily AI log when journaling, unless the user explicitly asks for a daily log as well.
- Keep emotional and private reflection in the journal; the daily AI log is for structural memory.

---

## task: daily_ai_log_for_date

Trigger

The user wants a compact daily memory/log for a date, for example:
- "create today's daily log"
- "update the daily_ai log for [date]"
- "summarize what moved today"

Inputs

- date:
  - If the user provides a date, use it.
  - Otherwise, assume "today" in the user's local time.

Process

1. Confirm the date if needed.
2. Check if a journal exists for that date:
   - 333_journal/<date>_journal.md
   - If it exists, read it and extract only structural information:
     - what the user worked on,
     - key events or decisions,
     - important linked notes.
   - Do NOT copy emotional detail into the daily AI log.
3. Look for notes created or clearly updated on that date in:
   - 888_inbox/ (inbox research notes),
   - 910_projects/ (project notes).
   Use their YAML date fields or log sections if available.
4. Use the daily AI template:
   - Template path: 000_system/templates/daily_ai_log_template.md
   - Follow its ai_instructions to write a short, link-heavy summary.
5. Create or update the note:
   - Path: 111_logs/daily/<date>_ai.md
   - Make sure the YAML date matches the day being logged.
   - Set YAML `title` to the note’s H1 (for example: `<date> – daily_ai`) unless the user wants a different title.

Notes

- If there is no journal for that date and very few notes, briefly ask the user what they worked on or what moved, then create a minimal but accurate daily AI log.
- The daily AI log is for memory and navigation, not for detailed emotional reflection.
