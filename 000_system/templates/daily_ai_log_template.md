---
title: ""
date: YYYY-MM-DD
tags: []
---

%% ai_instructions
Goal:
- Create a compact, link-heavy daily memory entry for this date using existing notes in the vault, without relying on past chat logs.

Assumptions:
- A higher-level task (see 000_system/ai_tasks.md, task: daily_ai_log_for_date) has already:
  - decided to create or update the daily AI log for a specific date,
  - provided or confirmed the date.

Primary_sources:
- 333_journal/<date>_journal.md if it exists.
- Inbox research notes in 888_inbox/ with matching date in YAML.
- Project notes in 910_projects/ that clearly reference this date in their logs or updates (if available).

Process:
1. Use the provided date (or ask the caller/task if it is missing).
2. If a journal exists for that date:
   - Read it, and only extract structural information relevant for memory:
     - what Simon worked on or moved forward,
     - notable events or decisions,
     - important linked notes.
   - Do NOT bring emotional details into this daily_ai note.
3. Look for inbox research notes and project updates from that date:
   - Use their titles/headings and any log sections to identify what changed or what they are about.
   - Plan to link to them in work_summary or notable_notes.
4. Write a compact entry:
   - One line for focus_of_the_day,
   - 3–7 bullets under work_summary with [[links]] where possible,
   - 1–3 bullets under key_decisions if applicable,
   - 1–5 items under notable_notes linking to important notes with a short reason.

YAML_rules:
- Set date to the day this log describes (YYYY-MM-DD).
- Set title to the H1 of the note (default: `<date> – daily_ai`).
- Leave tags as [] unless Simon specifies tags.
%%

# <date> – daily_ai

## focus_of_the_day
- ...

## work_summary
- ...

## key_decisions
- ...

## notable_notes
- [[some_note]] – why it matters
- [[another_note]] – why it matters
