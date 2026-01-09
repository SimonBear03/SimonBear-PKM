---
title: "ai_second_brain – inbox_research"
date: 2026-01-09
tags: []
---

# ai_second_brain – inbox_research

## context
- what am I trying to understand or decide?
  - how to build a long-term, AI-integrated second brain that I fully own (SimonBear PKM).
  - how to combine Obsidian + local files + AI agents (ChatGPT/Cursor/Codex, maybe local LLMs later).
- why does this matter / where does it fit (project, content, life)?
  - this will be the backbone for all future projects (Zillion Visionary, Daily Blob, Toolipie, etc.).
  - I want one durable place where my knowledge, research, and AI-assisted thinking live together.

## key_questions
- how ould the vault be structured so it can last for years and stay understandable?
- how do I integrate AI agents safely (no chaos, no random file spam)?
- where do chats/research go vs distilled knowledge vs active projects?
- how can this later connect to a web interface / NAS / Tailscale setup?

## snapshot
- decided that the vault is my personal second brain: **SimonBear PKM**, not “just Zillion Visionary.”
- agreed on a numbered folder structure:
  - `000_system`, `111_logs`, `222_assets`, `888_inbox`, `910_projects`, `920_content`, `999_library`.
- created:
  - [[000_system/home]] as a simple dashboard.
  - [[000_system/vault_readme]] describing structure + workflow.
  - [[AGENTS]] at root with rules for how AI agents should operate.
  - [[000_system/templates/inbox_research_template]] for research notes.
  - [[000_system/templates/library_note_template]] for distilled knowledge.
- clarified that AI notes are **not separate**; they’re just normal notes in Inbox / Library / Projects.
- decided ttually self-host a web interface (possibly on NAS + Tailscale) that reads the same vault.
- set up a minimal `.gitignore` and a `README.md` for GitHub, while keeping vault-specific docs in `000_system/`.

## notes
- vault is local-first, with the option to sync via iCloud / NAS; Git is used for versioning the markdown notes.
- Zillion Visionary is an “area/domain” inside the vault, not the vault itself.
- `910_projects/` is for **finite** deliverables (Daily Blob MVP, second brain interface, etc.), not broad themes.
- `999_library/` is for distilled, reusable knowledge (frameworks, topics, methods).
- `888_inbox/` is the default landing zone for research dumps and chat summaries.
- [[AGENTS]] tells AI agents:
  - use snake_case filenames,
  - don’t touch folders without permission,
  - use templates,
  - default to Inbox when unsure.
- templates are the **single source of truth** for note structure; [[AGENTS]] only points agents to them instead of duplicating headings.

## evidence_and_sourmain “source” is this ChatGPT conversation and my own design decisions.
- no external articles or books referenced yet for PKM design; this is mostly custom to my workflow.

## ideas_and_hypotheses
- if I keep all system rules in `000_system/` + [[AGENTS]], I can safely use AI agents (Codex, ChatGPT) to manipulate the vault without chaos.
- using Tailscale + NAS for self-hosting a web interface will solve “access anywhere” while keeping data private.
- having a dedicated templates folder and explicit workflows will make scaling this system easier as I add more projects and tools.

## decisions_or_conclusions
- the vault identity is **SimonBear PKM**: a long-term personal second brain, not tied to one brand.
- I will:
  - keep system docs in `000_system/` (including `vault_readme.md`, templates, AGENTS).
  - use `888_inbox` for all new research/chat notes.
  - promote only *distilled* ideas into `999_library`.
  - use `910_projects` only for real, finite deliverables.
- AI agents must:
  - follow `A`,
  - use the templates instead of inventing their own formats,
  - avoid restructuring folders unless I explicitly ask.

## open_questions
- how to best implement long-term AI memory beyond the vault structure (embedding DB? RAG? periodic summaries?).
- when/how to build the local or self-hosted web interface:
  - tech stack (Next.js? simple Flask/FastAPI?),
  - where exactly to run it (NAS, mini PC, etc.).
- how much of the vault to expose to AI at once (privacy vs convenience).
- whether to version-control large assets in `222_assets` or rely solely on NAS/iCloud.

## next_steps
- start using `000_system/templates/inbox_research_template.md` for real research sessions (e.g., image restoration, Daily Blob).
- create the first library note in `999_library/frameworks/` once the PKM design feels stable (e.g., `ai_augmented_pkm_system.md`).
- define a simple section structure for project notes in `910_projects/` (goal, current_status, next_actions, linked_notes).
- later: experiment with a small local web interface that reads the vault and uses OpenAI API with the same rules as [[AGENTS]].

## candidates_for_library
- [ ] `ai_augmented_pkm_system` (target: `999_library/frameworks/`)
- [ ] `obsidian_vault_structure_simonbear_pkm` (target: `999_library/frameworks/`)
- [ ] `ai_agent_guidelines_for_pkm` (target: `999_library/methods/`)

## related_notes
- [[2026-01-09_journal]] – personal reflection on setting up the SimonBear PKM and AI second brain.
- [[2026-01-09_ai]] – daily_ai log summarizing the structural decisions made for the vault and AI workflows on the same day.
