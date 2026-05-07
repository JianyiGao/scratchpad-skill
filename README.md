# Scratchpad

A tiny scratchpad for AI chats that are getting a little too long to hold in your head.
Scratchpad is a lightweight AI chat memory skill for preserving decisions, todos, and context across long Codex or Claude Code sessions.

Sometimes a conversation starts with one clear task, and then a few extra tabs open in your brain:

- Midway through one bug fix, you somehow find two new bugs 🫠
- A complex plan hits the "oh wait, we should come back to that later" point
- The chat accidentally wanders into a new topic
- The context window is getting full, and now we are just crossing our fingers hoping auto-compaction keeps all the useful bits 🤞

Scratchpad is for those moments.

It gives you and the agent one small shared note:

- **Scratchpad**: the current topic, useful context, and decisions that should survive auto-compaction
- **Todo List**: things to revisit later, marked as `open`, `resolved`, or `dropped`

This works best for chats that may need a couple of compacts. If the work needs to live longer than that, probably keep the context in separate files or docs.


## What It Helps With

- Remembering decisions after context gets long or auto-compacted
- Tracking side quest items without interrupting the current task
- Updating the core context when the chat accidentally changes topic
- Proactively saving useful context before auto-compaction happens at a bad moment
- Making it easier to resume a thread without asking the agent to re-explain the whole context

## Quick Usage

One command, depending on where you are:

- **Claude Code**: `/scratchpad`
- **Codex**: `$scratchpad`

Examples:

```text
/scratchpad add todo revisit this idea after the first pass
/scratchpad show
/scratchpad compact
```

```text
$scratchpad add todo check the old behavior before changing this
$scratchpad resolve todo add the missing test
$scratchpad compact
```

You can also just say things naturally:

```text
keep this in mind: we decided not to change the UI in this pass
```

## Install For Claude Code

Clone this repo somewhere first:

```bash
git clone git@github.com:JianyiGao/scratchpad-skill.git
cd scratchpad-skill
```

Then run both copy commands:

```bash
mkdir -p ~/.claude/commands
cp .claude/commands/scratchpad.md ~/.claude/commands/scratchpad.md
cp references/scratchpad.md ~/.claude/scratchpad-workflow.md
```

Restart Claude Code after copying the files, then use `/scratchpad`.

Claude Code details:

- [Custom slash command](.claude/commands/scratchpad.md)
- [Supporting file](references/scratchpad.md)

## Install For Codex

Clone this repo into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone git@github.com:JianyiGao/scratchpad-skill.git ~/.codex/skills/scratchpad
```

Restart Codex after cloning the skill, then use `$scratchpad`.

Codex details:

- [Codex skill](SKILL.md)
- [Shared workflow](references/scratchpad.md)
