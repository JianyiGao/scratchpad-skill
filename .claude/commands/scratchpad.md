---
description: Manage the scratchpad and todo list for this conversation
argument-hint: [show|refresh|add todo <item>|resolve todo <item>|drop todo <item>|reopen todo <item>|compact]
---

Use the workflow in `@scratchpad-workflow.md`.

Manage the scratchpad state for this conversation based on `$ARGUMENTS`.

## Requirements
- Default to creating or refreshing the scratchpad when no action is provided.
- `show`: show the current Scratchpad and Todo List without changing them.
- `refresh`: create or refresh the Scratchpad for the current topic.
- `add todo <item>`: add `<item>` to the Todo List with `open` state.
- `resolve todo <item>`: mark the matching Todo List item as `resolved`.
- `drop todo <item>`: mark the matching Todo List item as `dropped`.
- `reopen todo <item>`: mark the matching Todo List item as `open` again.
- `compact`: refresh the Scratchpad and Todo List first, then compact.
- Keep the Scratchpad under 10 bullets when possible.
- Include goal, constraints, current focus, decisions, open questions, and next steps when refreshing.
- If the conversation changed topic, refresh around the current topic while preserving still-relevant decisions and unresolved todos.
- Preserve existing unresolved todo items.
- Keep resolved or dropped todo items visible unless the user explicitly asks to remove them.
- Rewrite summaries for clarity instead of appending redundant details.
- Keep the scratchpad state in the conversation by default.
- Do not create or update a scratchpad file unless the user explicitly asks for a file-backed scratchpad.
- Treat the resulting Scratchpad as the source of truth for the current topic.
