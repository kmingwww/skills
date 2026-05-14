---
name: using-observer
description: Use when explicitly asked to "remember" or "lookup" information for the shared Second Brain.
---

# using-observer

## Initialization
Before using this skill, ensure `~/.observer` is initialized. If it doesn't exist, run:

```bash
mkdir -p ~/.observer/templates
cp -r assets/initialization/* ~/.observer/
```

*Note: `assets/initialization/` is relative to the skill directory.*

## Overview
Manages a collaborative "Second Brain" in an Obsidian vault using flattened entities and link-first discovery.

## High-Signal Filters (What to Skip)
- **Trivial/Obvious:** Skip vague session summaries (e.g., "User asked about X").
- **Static/Searchable:** Skip general documentation or web-searchable facts (e.g., library syntax).
- **Raw Data:** Skip large logs or code blocks > 20 lines (link instead).
- **Ephemera:** Skip temp paths and one-off debug context.
- **Redundancy:** Skip what's already in README.md or existing project files.

## Red Flags - STOP and Start Over
- Creating a note for "User asked about X".
- Overwriting person/project info without asking.
- Storing code blocks > 20 lines.
- Storing facts that are easily found on Wikipedia or official docs.
- Duplicating specs or tasks in the project Hub file (use subdirectories instead).

| Excuse | Reality |
|--------|---------|
| "It's better to have it than not" | Bloat kills discovery. Skip trivial info. |
| "I'm just updating the profile" | Conflicts require user intent. Ask first. |
| "This code is important" | If it's > 20 lines, link to the file. Don't bloat the vault. |
| "A summary in the Hub is helpful" | The Hub is a dashboard, not a storage for duplicate content. Link to the satellite folders. |

## Storage Structure
The vault path is defined in `~/.observer/config.json`. **If this file is missing, refer to the Initialization section.**

- `/indexing/`: Topics and MoCs.
- `/persons/`: Profiles (e.g., [[@Name]]).
- `/projects/`: Active work organized in lower-case project folders:
  - `/<project-name>/hub.md` (The Dashboard).
  - `/<project-name>/specs/` (Permanent requirements/architecture).
  - `/<project-name>/tasks/` (Ephemeral progress/backlog).
- `/journals/`: Daily records. (Note: Log project milestones here and link to the project hub for discoverability).
- `/runbooks/`: Procedures.
- `/notes/`: Atomic fragments of knowledge.
- `/_attachments/`: Media.

## Implementation
1. **Search First:** Always check for existing notes using grep/glob.
2. **Link Proactively:** Use [[internal links]] and create [[dangling links]].
3. **Cite Source:** Use footnotes [^1] and a ## 📚 References section for external links.
4. **Ask on Conflict:** If info contradicts a note, ask: "Merge, Overwrite, or Create New?".
5. **Formatting:** Follow the [Markdown Formatting Guide](references/markdown-format-for-obsidian.md) for Obsidian-flavored syntax (callouts, footnotes, mermaid).


## Self-Evolution
The `observer` system is designed to evolve:
- **Monitor Patterns:** Watch for Saturation (topic bloat), Repetition (redundant facts), or Clusters (related notes needing an index).
- **Propose Growth:** Propose new entities or templates in `~/.observer/schema.md` and `~/.observer/templates/` when patterns are identified.
- **Maintain Schema:** Update `~/.observer/schema.md` to track the system's evolution logic and structural changes.
- **Saturation:** When a note or index becomes too large (> 100 lines), split it into smaller atomic units.
- **Repetition:** When a fact is repeated across 3+ notes, centralize it into a new note and link to it.
- **Clusters:** When 5+ related notes exist without an Indexing Note, create a new Map of Content.
