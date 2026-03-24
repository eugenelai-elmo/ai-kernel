<!-- substrate/agents.md -->
# Agent Coordination

## When to use subagents

Use a subagent when:
- The task is independent (doesn't share state with current work)
- The task would pollute the current context window (research, large reads)
- You need parallelism (2+ independent tasks)

Do NOT use a subagent when:
- You need the result immediately to continue
- The task is a single tool call
- Spawning overhead exceeds the benefit

## Git worktrees for isolation

Non-trivial features get a worktree:
```bash
git worktree add ~/Projects/<repo>-worktrees/<ISSUE-ID> -b <branch> origin/main
```

This isolates changes from the main working tree. The agent working in the worktree
can build, test, and commit without touching your current work.

## Work reconciliation

When multiple agents work in parallel:
1. Each agent works in its own worktree/branch
2. Reconciler agent reviews all outputs before merge
3. Conflicts resolved by the reconciler — never silently dropped
4. Main agent reviews reconciler output before committing

## Agent handoff

When handing off context to a subagent, provide:
- Specific task (not "help with X")
- Relevant file paths (not "look around")
- Expected output format
- What NOT to do (saves iteration)
