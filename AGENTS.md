# Repository Guidelines

## Project Structure & Module Organization
This repository is an Obsidian vault for personal knowledge management (SimonBear PKM). Notes are stored as Markdown files under numbered top-level folders, with the primary navigation in `000_system/`. Key areas:

- `000_system/` – system notes, templates, and vault meta (e.g., `000_system/vault_readme.md`)
- `111_logs/` – time-based logs (daily/weekly/monthly/quarterly/yearly)
- `222_assets/` – linked files such as images, screenshots, and PDFs
- `888_inbox/` – raw captures and research dumps
- `910_projects/` – active deliverables
- `920_content/` – drafts, scripts, and content ideas
- `999_library/` – distilled, reusable knowledge

## Build, Test, and Development Commands
There are no build, test, or runtime commands for this vault. Editing is done directly in Obsidian or a text editor. If you add scripts later, document them here with usage examples.

## Coding Style & Naming Conventions
- Use Markdown for notes; keep content plain and readable in Obsidian.
- Prefer lowercase snake_case for new filenames (e.g., `meeting_notes.md`).
- Keep headings descriptive and short; avoid YAML frontmatter unless a template explicitly requires it.
- Use standard Obsidian wikilinks for cross-references (e.g., `[[999_library]]`).

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
- `888_inbox/` – raw captures, research dumps, and chat exports.  
  This is the default place for new information.
- `910_projects/` – active deliverables with clear goals and next actions only.  
  Do not create long-lived “areas” here; use it for concrete projects.
- `920_content/` – scripts, drafts, hooks, and retros for content (XHS, YouTube, articles, etc.).
- `999_library/` – distilled, reusable knowledge (methods, topics, frameworks).  
  Only promote notes here once they are summarized and cleaned up.

### General Rules

- Use **lowercase snake_case** for all new filenames.
- Never create or rename folders unless explicitly asked.
- Never delete or modify existing files unless explicitly asked.
- Prefer updating existing notes over creating new ones if the user says “add to” or “update”.
- Do **not** invent new top-level folders.
- When unsure where something belongs, default to `888_inbox` and clearly label the context.

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

- use standard Obsidian wikilinks: `[[note_name]]` or `[[note_name|alias]]`.
- before creating a new concept note, first search for an existing file whose name or title is close to the concept.
  - priority search order:
    1. `999_library/` (long-term knowledge)
    2. `910_projects/` (active work)
    3. `888_inbox/` (recent research)
- if a suitable existing note is found, link to it instead of creating a new one.

- when editing **inbox research notes**:
  - it is optional to use wikilinks in the main `notes` section.
  - in `candidates_for_library`, always use `[[...]]` when proposing future library notes if the note already exists.
  - if the note does not exist yet, you may write the plain text title without creating a stub, unless I explicitly ask for stubs.

- when editing **library notes** created from `library_note_template.md`:
  - always populate `## related_notes` with wikilinks to:
    - the inbox research note(s) that fed this note (from `888_inbox/`)
    - any project notes in `910_projects/` that use this idea
    - any other relevant library notes in `999_library/`.
  - do not add random links; only link when there is a clear relationship (uses, extends, contrasts, or summarises).

- when editing **project notes** in `910_projects/`:
  - in `linked_notes` (or similar section), add wikilinks to:
    - relevant library notes (methods, frameworks, topics)
    - important inbox research notes that are still “live”.
  - this creates a bidirectional graph: projects point to knowledge, knowledge points back to key projects.

- do **not** create empty stub notes just to “satisfy” a wikilink, unless I explicitly ask you to create a stub.
  - if you must reference a concept that has no note yet, write it as plain text or add a todo in `candidates_for_library`.

- in system/meta files (like this `AGENTS.md` or `vault_readme.md`), `[[999_library]]`, `[[910_projects]]`, etc. may be used as navigational links.
  - in normal notes, prefer linking to specific notes rather than top-level folders.