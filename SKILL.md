---
name: scratchpad
description: Maintain a compact conversation scratchpad, todo list, and memory checkpoint for long AI chats. Use when the user wants to remember decisions, preserve context through auto-compaction, track revisit items, resume a thread, or avoid losing important details in long-running Codex or Claude Code sessions.
---

# Scratchpad

Use this skill when a conversation is getting long enough that the current topic, decisions, or revisit items should stay easy to recover after auto-compaction or resume.

Read `references/scratchpad.md` and follow it.

## Examples

```text
$scratchpad show
$scratchpad add todo revisit this after the first pass
$scratchpad resolve todo add the missing test
$scratchpad compact
```

Natural language also works:

```text
keep this in mind: we decided not to change the UI in this pass
come back to this later
mark this todo resolved
refresh scratchpad and compact
```

The shared workflow is the source of truth for:

- the Scratchpad and Todo List format
- trigger phrases like "keep this in mind" and "add this to todo"
- todo state changes such as `open`, `resolved`, and `dropped`
- compaction behavior
- when to keep state in conversation versus file-backed memory
