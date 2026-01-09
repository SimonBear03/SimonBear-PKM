# simonbear_pkm

this vault is my personal second brain. it is meant to last for years and stay local-first. default flow: capture in inbox → distill into library → use in projects and content.

## folder_structure

- `000_system/` – system notes, rules, templates, meta
- `111_logs/` – time-based logs (daily, weekly, monthly, quarterly, yearly) when I choose to use them
- `222_assets/` – images, screenshots, pdfs and other files linked from notes
- `333_journal/` – personal journal entries (optional)
- `888_inbox/` – raw captures, research dumps, chat exports; first stop for new information
- `910_projects/` – active deliverables with clear goals
- `920_content/` – scripts, drafts, ideas, and retros for XHS, YouTube, articles, etc.
- `999_library/` – distilled, reusable knowledge (methods, topics, frameworks)

## naming_conventions

- journal (`333_journal/`): `YYYY-MM-DD_journal.md`
- ai logs (`111_logs/`):
  - daily: `YYYY-MM-DD_ai.md`
  - weekly: `YYYY-MM-w1_ai.md` (and `w2`, `w3`, `w4`, `w5`)
  - monthly: `YYYY-MM_ai.md`
  - quarterly: `YYYY-q1_ai.md` (and `q2`, `q3`, `q4`)
  - yearly: `YYYY_ai.md`

## yaml_frontmatter

all actual notes in:
- `111_logs`, `333_journal`, `888_inbox`, `910_projects`, `920_content`, `999_library`
use minimal yaml frontmatter at the top:

```yaml
---
title: ""
date: YYYY-MM-DD
tags: []
---
```

system notes in `000_system/` and files under `222_assets/` normally do not use yaml.
templates in `000_system/templates/` include this frontmatter stub so new notes start with the correct structure.

## basic_workflow

- capture first: new research, ideas, and chat summaries go to [[888_inbox]]
- distill later: when something is useful long-term, promote it into [[999_library]]
- do work in projects: only create notes in [[910_projects]] for real, active deliverables
- publish from content: use [[920_content]] for posts, scripts, hooks, performance notes
- logs are optional: use [[111_logs]] only when time-based reflection is helpful
- journal is optional: use `333_journal/` for personal journaling when helpful

## notes_for_ai

- when reading this vault, treat 999_library as long-term knowledge
- treat 910_projects as current work context
- treat 111_logs as time-based memory (if present)
- treat 333_journal as personal reflection (if present)
- inbox notes are noisy; prefer distilled notes in library when available

## yaml_and_ai_tasks

Most "real" notes in this vault (logs, journal, inbox research, projects, content, library) share a minimal YAML frontmatter so they can be used later by scripts or a web UI:

---
title: ""
date: YYYY-MM-DD
tags: []
---

This applies to notes under:
- 111_logs
- 333_journal
- 888_inbox
- 910_projects
- 920_conten- 999_library

System notes under 000_system/ and assets under 222_assets/ typically do not use YAML.

AI workflows are organized in:
- AGENTS.md for global rules and conventions.
- 000_system/ai_tasks.md as a task catalogue (for example: journaling, daily logs).
- 000_system/templates/ for note-level templates that include ai_instructions comments to explain how an agent should ask questions and structure each type of note.
