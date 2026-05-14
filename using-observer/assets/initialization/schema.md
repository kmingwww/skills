# Observer Note Schema

This schema defines the structure and usage of notes within the Observer system. Each entity follows the atomic notes principle and uses a specific template for consistency.

## Entities

### journal
- **Use when:** Logging daily events, conversations, and reflections. 
- **Template:** `~/.observer/templates/journal-template.md`
- **Rules:**
    1. Title must be `YYYY-MM-DD`.
    2. Log significant events in bullet points.
    3. Link mentioned persons using `[[@Name]]`.
    4. Link to the date using `[[YYYY-MM-DD]]`.

### person
- **Use when:** Capturing information about an individual or entity.
- **Template:** `~/.observer/templates/person-template.md`
- **Rules:**
    1. Title must start with `@` (e.g., `[[@Name]]`).
    2. Include profession, interests, and how you met.
    3. Link events to the relevant journal date.

### indexing
- **Use when:** Organizing links and resources for a specific topic or domain.
- **Template:** `~/.observer/templates/indexing-template.md`
- **Rules:**
    1. Use nested headings for organization.
    2. Index other notes and related topics.
    3. Sort by note links first.

### runbook
- **Use when:** Documenting a procedure, step-by-step guide, or workflow.
- **Template:** `~/.observer/templates/runbook-template.md`
- **Rules:**
    1. Clear, actionable steps.
    2. Include prerequisites and expected outcomes.

### project
- **Use when:** Storing information specific to a single, active project.
- **Template:** `~/.observer/templates/project-template.md` (The Dashboard)
- **Rules:**
    1. Always use a lower-case project folder: `projects/<project-name>/`.
    2. The main file in the folder is the Dashboard: `projects/<project-name>/hub.md`.
    3. Decompose content immediately into satellite folders:
        - `specs/`: Permanent rules, requirements, and architecture.
        - `tasks/`: Ephemeral progress, backlog, and todo lists.
    4. Log chronological milestones in [[journals/|Daily Journals]] and link to the project hub.
    5. Move non-project knowledge to Default Notes.

### note
- **Use when:** Creating a general note for a single concept or idea that doesn't fit other categories.
- **Template:** `~/.observer/templates/default-template.md`
- **Rules:**
    1. Short, precise title (no abbreviations).
    2. Content must use full descriptive terms (no abbreviations).
    3. Strictly atomic: one idea per note.
