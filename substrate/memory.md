<!-- substrate/memory.md -->
# Memory Protocol

## Decision Recording

When making a non-obvious decision (architecture choice, library selection, pattern override, tradeoff), record it immediately:

Hook trigger: the decision hook writes to `~/.claude/decisions/decisions.csv`:
```
timestamp,repo,decision,why,alternatives_considered
```

To query: `grep <topic> ~/.claude/decisions/decisions.csv`

This answers "why is X the way it is?" without manual archaeology.

## Session Context Restoration

Before ending work: write `~/.claude/handoff/session-handoff.md` with:
- What was done this session
- Current state (branch, open PRs, blockers)
- What to do next

At start of new session on same work: read this file first.

## Serena Memories (project-scoped)

For architectural decisions and patterns that apply to this project:
- `write_memory` — save key decisions, patterns, gotchas
- `list_memories` then `read_memory` for relevant ones at session start

Prefer Serena memories for things that are specific to this codebase.
Prefer decisions.csv for cross-repo or "why" questions.
