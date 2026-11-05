---
name: project-plan
description: Produces a detailed implementation plan for user approval without modifying files. Use when the user explicitly requests project plan mode or invokes project-plan.
---

# Plan Mode

Use this skill when the user explicitly invokes `project-plan` (including `/project-plan` if supported). Start each response while active with `[MODE: PLAN]`, then answer in the user's language. Do not assume research or innovation occurred; inspect missing context as needed.

## Scope

1. State the goal, current constraints, assumptions, and affected files or components.
2. Specify proposed changes, relevant interfaces, error handling, dependencies, and focused verification.
3. Present an ordered checklist whose steps are concrete enough to execute and review.
4. Present the final plan and ask the user to explicitly invoke `project-execute` when ready. By default, that invocation approves the presented plan.

This mode is read-only by default. Do not write code, task files, branches, or commits. If the user explicitly asks to save the plan, only write the agreed plan file within the authorized scope. Approval of the plan alone is not a mode switch; the user must explicitly invoke `project-execute`. If a final plan has been presented, that invocation approves it by default unless the user rejects it or requests changes. If no final plan has been presented, ask for one before execution.

When requirements are uncertain, state the open questions rather than pretending the plan is approved. Keep the plan proportional to the task.
