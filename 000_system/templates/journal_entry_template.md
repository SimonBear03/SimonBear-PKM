---
title: ""
date: YYYY-MM-DD
tags: []
---

%% ai_instructions
Goal:
- Turn Simon's reflections for a specific date into a concise, structured journal entry.

Assumptions:
- A higher-level task (see 000_system/ai_tasks.md, task: journal_entry_for_date) has already:
  - determined the date of this entry,
  - decided that a journal should be created or updated now.

Inputs:
- The date to journal about.
- Simon's answers to a small number of open reflection questions asked in this session.

Question_strategy:
- Ask questions in small batches, adapting as you go.
- Start broad (for example, how the day felt, what stood out, or what is still on his mind).
- Based on his answers, choose follow-ups from:
  - emotions (what felt good, hard, or lingering),
  - events or highlights (what actually happened),
  - insights or meaning (what he realized or learned),
  - optional gratitude,
  - optional intentions for tomorrow.
- Avoid asking every possible question mechanically.
- Aim for about 3–6 questions total.
- Prefer short, open prompts over yes/no questions.

Output_rules:
- Create or update 333_journal/<date>_journal.md using this template.
- Fill the mood and thoughts sections using Simon's own words where important.
- You may lightly summarize or group highlights, but do NOT invent events or feelings.
- Do not copy this whole journal into any 111 daily log; that log is for structural memory only.

YAML_rules:
- Set date to the journal date (YYYY-MM-DD).
- Set title to the H1 of the note (default: `<date> – journal`).
- Keep tags as [] unless Simon explicitly specifies tags.
%%

# <date> – journal

## mood
- ...

## highlights
- ...

## thoughts
- ...

## gratitude (optional)
- ...

## questions_to_self (optional)
- ...

## tomorrow_intentions (optional)
- ...
