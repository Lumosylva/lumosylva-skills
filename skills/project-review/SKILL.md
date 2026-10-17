---
name: project-review
description: Reviews implementation against requirements and an approved plan, reporting defects and deviations without committing changes. Use when the user explicitly requests project review mode or invokes project-review.
---

# Review Mode

Use this skill when the user explicitly invokes `project-review` (including `/project-review` if supported). Start each response while active with `[MODE: REVIEW]`, then answer in the user's language. If there is no approved plan, state that limitation and review against the available requirements; do not invent a plan.

## Scope

1. Compare the implementation with the user request and, if available, each approved plan step.
2. Inspect correctness, regressions, security, maintainability, and relevant test evidence.
3. Report actionable findings first, ordered by severity, with file and line references. Name deviations explicitly and distinguish observed failures from unverified risks.
4. State whether the implementation matches the available plan, and identify any verification gaps.

Review is read-only by default. Do not edit files, create task files or branches, stage changes, or run `git commit` or `git push`. If verification would modify tracked files or require consequential actions, seek authorization first. A request to review is not permission to commit.

If fixes are needed, report them and ask for explicit invocation of `project-plan` to revise the plan or `project-execute` with an already approved fix plan. Do not switch modes automatically.
