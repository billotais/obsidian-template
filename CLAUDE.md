# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Obsidian vault template for daily professional use. Combines folder-based organization with a link-based knowledge graph. The vault lives in the `notes/` directory and is opened directly in Obsidian.

There are no build, test, or lint commands — this is a content/configuration project consisting of markdown files, YAML frontmatter, Templater JavaScript templates, and Obsidian Bases (`.base` files).

## Information Architecture (PAKMAT)

- **Projects/** — One folder per project (`ClientName - ProjectName`), containing Meetings/, Notes/, Topics/, Tasks/ subfolders
- **Archives/** — Completed projects moved here
- **Knowledge/** — Reusable across projects: Companies/, Concepts/, People/
- **Agenda/** — Daily notes (`YYYY-MM-DD`)
- **Bases/** — Obsidian native database views with dropdown helpers
- **Templates/** — Templater-powered templates for all note types

## Cross-Linking Model

Everything links together via YAML frontmatter properties:
- Projects link to a Client (Company) and Team (People)
- Meetings link to a Project, Participants (People), and Topics
- Notes link to a Project and Topics
- People link to a Company
- Daily notes are referenced by date links (`[[YYYY-MM-DD]]`)

## Naming Conventions

| Type | Pattern | Example |
|------|---------|---------|
| Project | `ClientName - ProjectName` | `Company X - Internal Activities` |
| Person | `FirstName LASTNAME` | `John DOE` |
| Meeting | `Code - MeetingType - YYYY-MM-DD` | `CX - Weekly - 2026-01-15` |
| Note | `Code - NoteName` | `CX - Architecture Review` |
| Topic | `Code - TopicName` | `CX - Data Migration` |
| Task | `Code - TaskName - YYYY-MM-DD` | `CX - Fix bug - 2026-01-15` |
| Daily | `YYYY-MM-DD` | `2026-01-15` |

## Frontmatter Conventions

All notes use a `tags` property for type identification: `Type/Project`, `Type/Meeting/Weekly`, `Type/Note/Topic`, `Type/Person`, `Type/Company`, `Type/Concept`, etc.

Projects use numbered stages for ordering (e.g., `"40. Ongoing"`, `"50. Finished"`).

Link properties use Obsidian wiki-link syntax in YAML: `Client: '[[CompanyName]]'`, `Team: [[[Person1]], [[Person2]]]`.

## Templates (Templater Plugin)

Templates in `notes/Templates/` use Templater's JavaScript/EJS syntax (`<% ... %>`). They:
- Prompt for input using `tp.system.suggester()` and `tp.system.prompt()`
- Auto-suggest existing items (Companies, Projects, People) from the vault
- Move created files to the correct path with `tp.file.move()`
- Use `moment()` for date handling

## Bases (.base files)

Bases are JSON files defining database views over vault notes. Key patterns:
- Filter by tags: `file.tags.contains("Type/Project")`
- Filter by properties: `Active == true`, `not: Departed == true`
- Link-based filters: `file.links.contains(this.file)`
- Formulas: `link()`, `split()`, `if()`, `contains()`, date comparisons
- Dropdown helpers in `Bases/Dropdown helpers/` define select options

## Key Plugin Dependencies

- **Templater** — Template creation with JS scripting
- **Dataview** — SQL-like queries for note relationships
- **Obsidian Bases** — Native database/table views (requires Obsidian v3+)
- **Calendar** — Daily note quick access
- **Tasks** — Task tracking with due dates
