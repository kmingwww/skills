# Observer Conventions

This document outlines the specific formatting and structural conventions enforced within the Observer system. These conventions complement the general [[markdown-format-for-obsidian|Markdown Formatting Guide]].

## Mandatory External Link Format

To maintain a clean, high-signal, and distraction-free content area, **all external links (URLs) must be moved to the References section.**

1. **No Inline Links:** Do not use inline external links `[Title](URL)` within the main body of a note.
2. **Footnote Definitions:** Define all external links as footnote definitions (`[^X]: [Title](URL)`) at the end of the file.
3. **References Section:** All footnote definitions **must** be placed under a `## 📚 References` heading, which is always the final section of the note.
4. **Referencing:**
   - For specific citations, place a footnote marker `[^X]` immediately after the referenced text.
   - For general bookmarks or related resources, simply define the footnote in the `## 📚 References` section; an in-text marker is not required.

### Exception: Indexing Notes (MoCs)
Indexing notes (notes with the `indexing` tag) are exempt from the mandatory footnote format. Since their primary purpose is to aggregate and organize links, inline external links `[Title](URL)` are permitted within the main sections for better readability and scanning.

**Example:**
```md
The project uses the standard data ingestion protocol.

## 📚 References
[^1]: [Protocol Documentation](https://example.com/protocol)
[^2]: [General Project FAQ](https://example.com/faq)
```

## Internal Linking

Internal links `[[Note Name]]` or `[[Note Name|Alias]]` **must** remain inline within the content to ensure strong connectivity and visibility of the knowledge graph. Do not move internal links to the References section unless they are specifically being cited as a source.

## List Formatting

To maintain visual consistency across all notes:
1. **Dashes only:** Always use a hyphen/dash `-` for unordered lists. 
2. **No Asterisks:** Do not use asterisks `*` for bullet points.
