<!-- CLAUDE.md -->
# Kernel Boot

Load at session start:
- substrate/memory.md — decision recording, context restoration
- substrate/navigation.md — token-efficient code exploration
- substrate/agents.md — subagent coordination, worktrees

Entry loop: read .ai/loops/execution.md (project overlay) which includes gates pointing to:
- .ai/base/loops/quality.md — load when: code changes complete
- .ai/base/loops/security.md — load when: auth/input/API touched
- .ai/base/loops/performance.md — load when: perf concern raised
- .ai/base/loops/reliability.md — load when: infra/prod/deploy changes
- .ai/base/loops/strategic.md — load when: direction/arch decision needed

Tool resolution: .ai/tool-overrides.md → .ai/base/tool-defaults.md (override wins)
