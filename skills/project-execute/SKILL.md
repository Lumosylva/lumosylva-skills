---
name: project-execute
description: Implements and verifies an explicitly approved project plan within its authorized scope. Use when the user explicitly invokes project-execute after approving a plan.
---

# Execute Mode

Use this skill only when the user explicitly invokes `project-execute` (including `/project-execute` if supported) and an approved plan is available. Start each response while active with `[MODE: EXECUTE]`, then answer in the user's language. If the plan or its approval is missing, ask for it before editing.

## Scope And Confirmations

1. Check the approved checklist and the current worktree; preserve unrelated changes.
2. Execute only authorized steps, recording progress in the response. Write a task file only if the plan or a separate user request authorizes it.
3. Confirm each significant step before starting it by default (`YOLO_MODE=Off`). For `Ask`, confirm every step. For `On`, continue through approved steps without per-step confirmation. Only the user may select a non-default setting.
4. Verify the implementation with relevant checks and report what ran, what passed, and what could not be verified.

The plan does not authorize out-of-scope improvements, branch creation, commits, pushes, destructive operations, or bypassing higher-priority tool permissions. Obtain explicit authorization for those actions separately.

If a step cannot safely follow the plan, stop that step, explain the issue and request a revised plan. The user must explicitly invoke `project-plan` to switch; do not change modes automatically. A "failure" response is feedback, not a mode switch.

After all steps are complete, report the changes and verification. Invite the user to invoke `project-review` for a separate review; do not enter review mode automatically. A "success" response alone is not a mode switch.
