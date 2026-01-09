# Repository Guidelines

## Project Structure & Module Organization
This repository is an Obsidian vault for personal knowledge management (SimonBear PKM). Notes are stored as Markdown files under numbered top-level folders, with the primary navigation in `000_system/`. Key areas:

- `000_system/` – system notes, templates, and vault meta (e.g., `000_system/vault_readme.md`)
- `111_logs/` – time-based logs (daily/weekly/monthly/quarterly/yearly)
- `222_assets/` – linked files such as images, screenshots, and PDFs
- `333_journal/` – personal journal entries
- `888_inbox/` – raw captures and research dumps
- `910_projects/` – active deliverables
- `920_content/` – drafts, scripts, and content ideas
- `999_library/` – distilled, reusable knowledge

## Build, Test, and Development Commands
There are no build, test, or runtime commands for this vault. Editing is done directly in Obsidian or a text editor. If you add scripts later, document them here with usage examples.

## Coding Style & Naming Conventions
- Use Markdown for notes; keep content plain and readable in Obsidian.
- Prefer lowercase snake_case for new filenames (e.g., `meeting_notes.md`) except date-based notes (logs/journal) which use the date patterns below.
- Keep headings descriptive and short; use only the minimal YAML frontmatter defined below for “real” notes.
- Use standard Obsidian wikilinks for cross-references (e.g., `[[999_library]]`).
- For time-based notes, use date-based filenames so wikilinks are stable:
  - `333_journal/`: `YYYY-MM-DD_journal.md`
  - `111_logs/daily/`: `YYYY-MM-DD_ai.md`
  - `111_logs/weekly/`: `YYYY-MM-w1_ai.md` (and `w2`, `w3`, `w4`, `w5`)
  - `111_logs/monthly/`: `YYYY-MM_ai.md`
  - `111_logs/quarterly/`: `YYYY-q1_ai.md` (and `q2`, `q3`, `q4`)
  - `111_logs/yearly/`: `YYYY_ai.md`

## Testing Guidelines
No automated tests are defined. Validate changes by opening the vault in Obsidian and checking links/rendering.

## Commit & Pull Request Guidelines
No Git history or commit conventions are present in this vault. If you introduce version control, use clear, imperative commit messages and include brief context in PR descriptions (what changed, why, and which notes were touched).

---

## Agent-Specific Notes

If you are an automated agent (e.g., Codex, ChatGPT, or another LLM), follow these rules when working in this vault.

### Goals

- Keep notes clean, consistent, and local-first.
- Help capture research and chats into `888_inbox`.
- Help distill important things into `999_library`.
- Help manage active projects in `910_projects` and content in `920_content`.

### Folder Rules

- `000_system/` – system notes, rules, templates, and meta.  
  Do **not** put normal content notes here unless explicitly instructed.
- `111_logs/` – time-based logs (daily/weekly/monthly/quarterly/yearly).  
  Only create or modify log notes when explicitly asked.
- `222_assets/` – images, screenshots, PDFs, and other linked files.  
  Do **not** create files here unless asked for a specific path or filename.
- `333_journal/` – personal journal entries.  
  Only create or modify journal notes when explicitly asked.
- `888_inbox/` – raw captures, research dumps, and chat exports.  
  This is the default place for new information.
- `910_projects/` – active deliverables with clear goals and next actions only.  
  Do not create long-lived “areas” here; use it for concrete projects.
- `920_content/` – scripts, drafts, hooks, and retros for content (XHS, YouTube, articles, etc.).
- `999_library/` – distilled, reusable knowledge (methods, topics, frameworks).  
  Only promote notes here once they are summarized and cleaned up.

### General Rules

- Use **lowercase snake_case** for all new filenames, except date-based logs/journal which use the naming conventions above.
- Never create or rename folders unless explicitly asked.
- Never delete or modify existing files unless explicitly asked.
- Prefer updating existing notes over creating new ones if the user says “add to” or “update”.
- Do **not** invent new top-level folders.
- When unsure where something belongs, default to `888_inbox` and clearly label the context.

### YAML frontmatter

- All “real” notes in these folders must have minimal YAML frontmatter at the top:
  - `111_logs/*`
  - `333_journal/*`
  - `888_inbox/*`
  - `910_projects/*`
  - `920_content/*`
  - `999_library/*`
- YAML schema:

  ```yaml
  ---
  title: ""
  date: YYYY-MM-DD
  tags: []
  ---
  ```

- When creating a new note in these folders, agents MUST:
  - include this YAML block at the top,
  - set `date` to the actual date of the note (`YYYY-MM-DD`),
  - set `title` to match the note’s H1 heading (or a clear default like `YYYY-MM-DD – journal`, `YYYY-MM-DD – daily_ai`, `<topic> – inbox_research`),
  - keep `tags` as `[]` unless the user specifies tags.
- System notes in `000_system/` and raw assets in `222_assets/` do NOT require YAML unless explicitly requested.

### Workflows

#### 1. Capturing a research/chat session

When the user is exploring a topic or having a long chat:

- Create a new note in `888_inbox/`.
- Filename pattern:  
  `"<topic>_inbox_research_yyyy_mm_dd.md"`  
  (Example: `ai_second_brain_inbox_research_2026_01_09.md`)
- If `000_system/templates/inbox_research_template.md` exists, copy that template to create the new note and then fill in its headings.
- Do not rename or remove headings from the template unless the user explicitly asks.
- It is okay to leave some sections empty if they are not relevant to this session.
- Aim to capture at least:
  - why this research matters (context),
  - the main questions being asked,
  - what has been learned so far (a brief snapshot),
  - key notes and evidence/sources,
  - next steps and any candidates for future distilled notes in `999_library`.

#### 2. Promoting to the Library

Only promote when the user explicitly asks for a summary/distilled note, or clearly wants a reusable concept captured.

- Create a note in one of:
  - `999_library/methods/`
  - `999_library/topics/`
  - `999_library/frameworks/`
- Filename: short, clear, snake_case describing the concept  
  (e.g., `ai_second_brain_setup.md`, `image_restoration_workflow.md`)
- If `000_system/templates/library_note_template.md` exists, copy that template to create the new library note and then fill in all of its headings.
- Do not rename or remove headings from the template unless the user explicitly asks.
- At minimum, make sure the note includes:
  - a clear summary of the idea,
  - context for when and why to use it,
  - the key points,
  - and at least one concrete item in `how_to_use` describing how the user can apply it in projects, content, or decisions.
- Use `related_notes` to add wikilinks back to the inbox research note(s), relevant project notes, and any closely related library notes.
- Use `source` to briefly describe where the idea came from (chatgpt / gemini / web / book / self, plus more specific citation if helpful).

#### 3. Projects

When the user describes a concrete deliverable (e.g., “build daily blob MVP”, “set up second brain interface”):

- Create or update a note in `910_projects/`.
- Suggested sections:
  - **goal** – what success looks like
  - **current_status**
  - **next_actions** – clear, small tasks
  - **linked_notes** – relevant inbox/library notes

Do **not** treat broad areas (e.g., “zillion visionary”) as a project; those should be library/framework notes, not `910_projects` entries.

#### 4. Journal & Daily AI

Only create these notes when the user explicitly asks.

- For daily logs under `111_logs/daily/`, name files `YYYY-MM-DD_ai.md` and use `000_system/templates/daily_ai_log_template.md` if applicable.
- For journal entries under `333_journal/`, name files `YYYY-MM-DD_journal.md` and use `000_system/templates/journal_entry_template.md` if applicable.
- Do not rename or remove headings from templates unless the user explicitly asks.

### When a New Chat Starts

If the user says something like “we’re working inside my vault” or “use my PKM system,” you should:

1. Use these rules to decide where to create or update notes.
2. Ask what the current topic or project is **if it’s not clear**.
3. Help the user:
   - create or update an inbox note in `888_inbox`, or
   - update a project note in `910_projects`, or
   - create/update a library note in `999_library`.
4. Always follow the Folder Rules and General Rules above.

### wikilink_rules

Use Obsidian wikilinks not just as a convenience, but as a way to grow a useful graph over time. When you create or edit any "real" note in:
- 111_logs/*
- 333_journal/*
- 888_inbox/*
- 910_projects/*
- 920_content/*
- 999_library/*

you should actively look for reasonable opportunities to add wikilinks.

#### general_principles

- Use standard Obsidian wikilinks: `[[note_name]]` or `[[note_name|alias]]`.
- Think: "I am weaving this note into the graph" whenever you write.
- Prefer short, stable, lowercase snake_case names for concepts and projects (for example, `[[ai_second_brain]]`, `[[daily_blob]]`, `[[zillion_visionary]]`).
- Link the first meaningful mention of a concept or project in a paragraph/section; you do not need to link every repetition.
- Only link when there is a clear and useful relationship (same concept, used by, extended by, contrasted with). Do not spam random links.

#### choosing_what_to_link

When writing or editing a note, look for:
- **Projects and products** (for example, Daily Blob, Zillion Visionary, Toolipie) and link them to their project or library notes.
- **Major recurring concepts** (for example, AI second brain, PKM system design, image restoration) and link them to their main library notes.
- **Specific notes** that you reference by name (for example, a previous inbox research session or a project log) and link them directly.

Before creating a new concept note, first search for an existing file whose name or title is close to the concept.
- Priority search order:
  1. 999_library/ (long-term knowledge)
  2. 910_projects/ (active work)
  3. 888_inbox/ (recent research)
- If a suitable existing note is found, link to it instead of creating a new one.
- Do **not** create empty stub notes just to satisfy a wikilink, unless Simon explicitly asks for a stub.

#### per_folder_behaviour

- **888_inbox (inbox research):**
  - In the main notes/body, you may use wikilinks when it helps connect to existing concepts or projects.
  - In any "candidates_for_library" or similar section, always use `[[...]]` when referring to library notes that already exist.
  - For concepts that might become library notes but do not exist yet, you may write the candidate title as plain text or a TODO, without creating a stub.

- **999_library (knowledge):**
  - Always use `## related_notes` (or equivalent) to add wikilinks to:
    - source inbox research notes in 888_inbox/ that fed this note,
    - project notes in 910_projects/ that use this idea,
    - other library notes that are closely related.
  - When introducing a core concept in the library, prefer to make that the canonical link target for that concept (for example, `[[ai_second_brain]]`).

- **910_projects (projects):**
  - Maintain a section (for example, `linked_notes` or `context`) with wikilinks to:
    - relevant library notes (methods, frameworks, topics),
    - important inbox research notes that are still active.
  - When journaling progress or writing logs inside a project note, link back to key days in 111_logs/daily or notable journal entries in 333_journal if clearly relevant.

- **111_logs (daily/weekly/etc. AI logs):**
  - In `work_summary` and `notable_notes`, prefer to reference other notes using wikilinks rather than plain text.
  - The goal is for 111_logs entries to act as a navigational hub for what happened that day/week.

- **333_journal (personal journal):**
  - Use links sparingly and only when it feels clearly useful (for example, linking to a project, a decision note, or a key method that the reflection is about).
  - Do not over-link emotional or private content.

- **920_content (content drafts):**
  - Link to library notes for ideas/frameworks you are using.
  - Link to project notes for series, campaigns, or recurring content themes.

#### system_and_meta

- In system/meta files (like this AGENTS.md or vault_readme.md), `[[999_library]]`, `[[910_projects]]`, etc. may be used as navigational links.
- In normal notes, prefer linking to specific notes rather than top-level folders.

By following these rules, agents help ensure that every new or edited note gently strengthens the Obsidian graph, even if Simon forgets to add wikilinks manually.

## task_catalogue_and_templates

For higher-level tasks (journaling, daily logs, inbox research, project updates, content drafting, etc.), use the task catalogue and templates instead of guessing the workflow.

- Task catalogue: 000_system/ai_tasks.md
  - This file describes WHEN to use which workflow (for example: "journal_entry_for_date", "daily_ai_log_for_date"), what inputs are needed (like dates), and which template to apply.
- Templates: files in 000_system/templates/
  - Each template can include an ai_instructions block (inside Obsidian comments, like %% ... %%) that describes how to ask questions, how to extract information, and how to fill the sections of that note.
  - The template assumes a higher-level task has already been chosen and necessary inputs (like the date) have been decided.

General rules for real notes:
- All "real" notes in these folders must have minimal YAML frontmatter at the top:
  - 111_logs/*
  - 333_journal/*
  - 888_inbox/*
  - 910_projects/*
  - 920_content/*
  - 999_library/*
- The YAML schema is:

  Line 1: ---
  Line 2: title: ""
  Line 3: date: YYYY-MM-DD
  Line 4: tags: []
  Line 5: ---
Remember to add the actual title of the note into the title in YAML.

- System notes in 000_system/ and raw assets in 222_assets/ do NOT require YAML unless explicitly requested.

When handling a user request:
1. Decide what task it corresponds to (for example: journaling about a date, creating a daily log).
2. Look up the task in 000_system/ai_tasks.md.
3. Follow the process there and then follow the relevant template’s ai_instructions to create or update the note.
