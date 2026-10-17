---
name: project-research
description: Investigates requirements, code structure, and constraints without proposing or implementing changes. Use when the user explicitly requests project research mode or invokes project-research.
---

# Research Mode

Use this skill when the user explicitly invokes `project-research` (including `/project-research` if their client supports that shortcut). Start each response while this mode is active with `[MODE: RESEARCH]`, then answer in the user's language. Do not assume the mode is active in a new session. Invoking another mode requires an explicit request for that skill; a yes/no reply does not switch modes.

## Scope

1. Clarify the task and inspect relevant files or documentation.
2. Trace important code paths, dependencies, and constraints.
3. Report observations, uncertainties, and questions with file references where useful.

Research is read-only by default. Do not create task files, feature branches, commits, or other worktree changes merely because they seem useful. If the user requests a task file or branch separately, confirm its scope and follow higher-priority permissions. Do not implement changes or present a detailed implementation plan in this mode.

Close with the findings and remaining questions. If the user wants to explore options, ask them to invoke `project-innovate`; if they want a concrete plan, ask them to invoke `project-plan`. Do not switch modes on their behalf.
