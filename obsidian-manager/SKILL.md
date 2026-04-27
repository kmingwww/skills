---
name: obsidian-manager
description: Manages Obsidian markdown notes, including daily journals, projects, person-specific notes, runbooks, and indexes. Enforces atomic note principles, specific formatting, and inter-note linking conventions.
---

# Obsidian Manager

## Overview

This skill helps manage markdown notes for Obsidian by providing a set of predefined templates and strict guidelines for different note types. It is designed to ensure consistency, proper structure, and adherence to the **atomic notes principle**—a note should contain **one single, self-contained idea, concept, or entity.** The length of the note should be whatever is required to fully explain that one idea. If a note starts covering a second distinct topic, it **must** be split into separate notes.

Use this skill whenever a conversation involves information that is important for the user to remember long-term.

## General Guidelines

### Note Lifecycle Workflow
1.  **Pre-Creation Check:** Before creating any new note, always search for existing notes on the same topic and update them if one exists.
2.  **Post-Creation/Update Indexing (Mandatory):** After creating or updating *any* note, you **must** perform the indexing procedure. Read the `topics` field from the note's frontmatter and, for each topic, add a link to the current note in the corresponding indexing note (e.g., `resources/indexing/Topic.md`). If an index for a topic doesn't exist, report it and ask to create one.

### Content and Formatting Rules
1.  **Frontmatter:** Ensure all YAML frontmatter syntax is correct. Avoid special characters like `#`, `:`, `{}`, `[]`. The `alias` field should not contain symbols like `@`.
2.  **Aliases (Unambiguous):** Provide aliases primarily for stylistic variations (e.g., `lower case`, `camelCase`, `PascalCase`, `Capitalize case`) and plurals of the note title, as well as for direct, globally unambiguous synonyms. **Crucially, all aliases must be unique and unambiguous within the vault.** Do not create an alias if it could refer to more than one existing note or another existing alias. Abbreviated forms are generally discouraged as aliases.
3.  **Template Adherence:** When updating older notes, match the structure of the official templates as closely as possible.
4.  **Examples (Crucial for Quality):** When relevant and if the content supports it, include concrete examples that directly illustrate the note's single idea. Examples are vital for practical understanding and application, providing a clear demonstration of the concept being explained.
5.  **Proactive Linking (Mandatory):** Actively link any noun, concept, or specific entity that is, or could ever become, its own note. Link it the first time it appears.
    *   **Rule:** Create `[[dangling links]]` for future notes. This reinforces the atomic notes principle by ensuring each concept gets its own potential note.
    *   **Example (Generic):** Instead of `This theory explains concept A and concept B.`, write `This [[theory]] explains [[concept A]] and [[[[concept B]]]].`
    *   **Example (Entities):** If discussing an event, link `[[YYYY-MM-DD - Event Name]]`. If discussing an individual, link `[[@Person Name]]`. If discussing a project, link `[[PROJECT_ID - Project Name]]`.
4.  **Citations and Verification:** Use markdown footnotes for all direct references. All footnote definitions **must** be placed under a `## References` heading. This heading **must be the absolute last section** in the note to ensure correct rendering. After generating a note, you **must** ensure that all footnote markers `[^X]` are correctly placed within the main text, corresponding to their definitions under `## References`. If a marker is missing, use conversation context or `web_fetch` on URLs to find the correct placement and insert it.
5.  **Related Resources (Optional):** If there are relevant, non-cited links (e.g., videos, related articles, internal notes), create a `## Related Resources` section for them. This section should be placed immediately before the `## References` section. Do not create this section if it would be empty.

### Vault Integrity and Navigation
1.  **Link Interpretation:** Treat all text in `[[...]]` as an internal link. For aliased links like `[[Note Name|Alias]]`, use "Note Name" for file searching.
2.  **Navigation Protocol:** Use a two-tiered approach for locating notes:
    -   **Primary (Link-Based):** First, search for the note in its conventional directory based on the link's text (`@` -> `persons`, `YYYY-MM-DD` -> `journals`, etc.).
    -   **Secondary (Frontmatter Verification):** If a file is found, you **must** read its `tags` field to verify it is in the correct directory.
3.  **Correction Protocol:**
    -   If a file's location contradicts its tag, report the discrepancy and ask for permission to move it.
    -   If a linked file does not exist, report it as a broken link and ask if you should create it.

## Markdown Formatting

**CRITICAL:** Before creating or modifying any note, you MUST read and strictly adhere to the formatting guidelines outlined in the reference file below. All markdown output must conform to these standards.

- **Reference:** `references/markdown-format-for-obsidian.md`

## Note Templates

This skill provides templates for the following types of notes. Use the appropriate template and follow the specific rules for each.

### Daily Journal

-   **Use when:** In every conversation to log daily events and reflections. If the user starts with a simple "Hi", ask how their day is going to start the journaling process.
-   **Template:** `assets/templates/journal-template.md`
-   **Rules:**
    1.  The note title **must** be in `YYYY-MM-DD` format (e.g., `2025-12-23`).
    2.  Do not remove or overwrite existing content; only add or update.
    3.  Log significant events and conversations from the user's perspective in the `Log` section.
    4.  If a person is mentioned, create or update a Person Note for them (e.g., `[[@Name]]`). Link the event to the date (e.g., `[[2025-04-15]]`).
    5.  Provide suggestions for self-improvement in the `Suggestions` section based on the logs.
    6.  Use the `Reflections` section for the user's reflections on specific events.
    7.  All content must be in short, precise, and potentially nested bullet points.

### Person Note

-   **Use when:** A person or entity is encountered that is worth remembering.
-   **Template:** `assets/templates/person-template.md`
-   **Rules:**
    1.  The note title **must** start with an `@` symbol (e.g., `[[@Kar Ming]]`).
    2.  Note down key information: profession, how you met, shared interests, events, and connection points.
    3.  If an event is mentioned, link it to the relevant daily journal note (e.g., `[[2025-04-15]]`).

### Indexing Note (Map of Content)

-   **Use when:** Creating or updating an index or a map of content for a topic.
-   **Template:** `assets/templates/indexing-template.md`
-   **Rules:**
    1.  Use nested headings for organization.
    2.  Use the note to index other notes and provide links to related topics.
    3.  Sort links by notes first, then other link types.
    4.  This note is the primary tool for note retrieval.

### Runbook Note

-   **Use when:** The user discusses a step-by-step guide or repeatable procedure. Proactively suggest creating a runbook if appropriate.
-   **Template:** `assets/templates/runbook-template.md`
-   **Description:** A template for creating detailed procedures and guides.

### Project Note

-   **Use when:** Storing information that is exclusive to a specific project.
-   **Template:** `assets/templates/project-template.md`
-   **Rules:**
    1.  Use to store project-specific information (e.g., goals, tasks).
    2.  If knowledge is not exclusively tied to the project, create a default note for it instead.

### Default Note

-   **Use when:** Creating a general note that doesn't fit other categories.
-   **Template:** `assets/templates/default-template.md`
-   **Rules:**
    1.  The title **must** be short, precise, and **must not contain any abbreviations**.
    2.  The entire content of the note **must not contain any abbreviations**; use full, descriptive terms instead.
    3.  Adhere strictly to the atomic notes principle.
