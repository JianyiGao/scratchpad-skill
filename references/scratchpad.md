# Scratchpad Workflow

Use this workflow when a conversation may grow long and a small amount of important context should remain easy to recover without depending on the full chat history.

The core model is simple:

- **Scratchpad**: current topic, useful context, decisions, and anything that should survive auto-compaction.
- **Todo List**: things to revisit later, with explicit state.

## Maintain two blocks

### 1. Scratchpad

Keep a compact summary of the active topic:
- Goal
- Constraints
- Current focus
- Decisions
- Open questions
- Next steps

If the conversation accidentally changes topic, refresh the Scratchpad around the current topic. Preserve still-relevant decisions and unresolved todos instead of blindly carrying the old topic forward.

### 2. Todo List

Track items discovered during the conversation that should not be forgotten but are not active yet.
Each item can optionally carry a simple state:
- `open`: still needs follow-up
- `resolved`: addressed, but worth retaining briefly for auditability
- `dropped`: intentionally not pursuing

Use the Todo List for:
- follow-up investigations
- possible separate fixes
- risks worth re-checking later
- ideas the user explicitly wants to keep in mind

## Rules

- Keep the Scratchpad under 10 bullets when possible.
- Prefer rewriting summaries over endlessly appending detail.
- Add newly discovered important items to the Todo List immediately.
- New todo items should default to `open` unless the user explicitly says otherwise.
- Default to conversation-only scratchpad state.
- Do not create or update a scratchpad file unless the user explicitly asks for a file-backed scratchpad.
- Refresh the Scratchpad after long detours, topic changes, or major decisions.
- If the user explicitly asks to compact, refresh the Scratchpad and Todo List first so the important context survives auto-compaction, then compact.
- Do not compact automatically or assume auto-compaction is wanted unless the user asks for it.
- Do not silently remove Todo List items. Prefer updating their state to `resolved` or `dropped`, and only remove them when the user explicitly asks to clean them up.
- Treat the Scratchpad as the source of truth for the current topic.

## State updates

Keep state updates lightweight and easy to invoke.

Interpret simple phrases like:
- mark this resolved
- resolve this todo
- mark this todo resolved
- drop this todo
- remove this from todo
- reopen this todo

as requests to update the matching item in the Todo List.

When an item changes state:
- keep the wording short
- preserve the item unless the user explicitly asks to remove it
- prefer `resolved` over deletion when the user may want to refer back to it later

When helpful, show the Todo List in a compact format like:

```text
Todo List

- [open] investigate X
- [resolved] confirm Y
- [dropped] pursue Z
```

## Trigger phrases

When the user says things like:
- keep this in mind
- pin this
- add this to todo
- add this to todo later
- come back to this
- do not forget this
- save this for later in the thread
- mark this resolved
- mark this todo resolved
- drop this todo
- reopen this todo
- refresh scratchpad and compact

then update the Scratchpad or Todo List as appropriate.
