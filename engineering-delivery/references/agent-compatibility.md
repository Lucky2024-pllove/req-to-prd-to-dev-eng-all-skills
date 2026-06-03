# Agent Compatibility

Use this reference to keep engineering-delivery outputs portable across Codex, Claude Code, Cursor, and similar agents.

## Portable Formats

Prefer:

- Markdown headings
- Markdown tables
- Checklists
- Mermaid diagrams
- ASCII sketches
- Code blocks for pseudocode, SQL drafts, prompt packages, config examples

Avoid requiring:

- Proprietary task boards
- Proprietary design tools
- Proprietary prompt managers
- Agent-specific command syntax

If the user wants integration with a specific tool, keep the Markdown source of truth and treat the tool integration as an export target.

## Portable Artifact Rules

| Artifact | Portable Form |
|----------|---------------|
| Team assignments | Markdown table |
| RACI | Markdown table |
| Todolist | Markdown checkbox list |
| DoD/gates | Markdown checklist/table |
| Pseudocode | Language-neutral code block |
| Agent workflow | Markdown table + Mermaid flowchart/sequenceDiagram |
| Prompt package | Markdown + code blocks |
| Diagrams | Mermaid |
| SQL scripts | `.sql` code blocks or files, marked draft/not executed |
| AI Agent task cards | Markdown table + checklist + code blocks for commands |

## Agent Limit Fallback

- If an agent cannot read references, inline the needed rules.
- If an agent cannot write files, output file names and bodies in chat.
- If an agent cannot render Mermaid, still output Mermaid source.
- If an agent cannot run commands, leave validation commands as suggested manual steps.
- If an agent cannot edit files, use the task card as a human execution checklist.

## Mermaid Compatibility

All Mermaid diagrams must follow [mermaid-compatibility.md](mermaid-compatibility.md):

- Use English/digit/underscore IDs.
- Put Chinese in node labels, aliases, notes, or nearby tables.
- Avoid high-risk edge-label syntax such as `-.label.->`.
- Use `participant Agent as 建模 Agent` style aliases in `sequenceDiagram`.
- Use English entity IDs in `erDiagram`.
