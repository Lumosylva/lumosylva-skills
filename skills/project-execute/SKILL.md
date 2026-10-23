---
name: project-execute
description: Implements and verifies an explicitly approved project plan within its authorized scope. Use when the user explicitly invokes project-execute after approving a plan.
---

# Execute Mode

Use this skill only when the user explicitly invokes `project-execute` (including `/project-execute` if supported) and an approved plan is available. Start each response while active with `[MODE: EXECUTE]`, then answer in the user's language. If the plan or its approval is missing, ask for it before editing.

## Scope And Confirmations

1. Check the approved checklist and the current worktree; preserve unrelated changes.
2. Execute only authorized steps, recording progress in the response. Write a task file only if the plan or a separate user request authorizes it.
3. Treat `YOLO_MODE` as a conversational preference for this `project-execute` invocation, not as an operating-system environment variable or persistent client setting. The user may select a non-default value by including `YOLO_MODE=Ask` or `YOLO_MODE=On` when explicitly invoking this skill. If omitted, use `Off`. Only the user may change the setting.
4. Apply the selected confirmation boundary:
   - `Off` (default): Ask and wait for approval before starting each top-level item in the approved checklist. One approval covers the related changes already described by that item.
   - `Ask`: Ask and wait before each separately reviewable change group within an approved checklist item. If an item contains multiple independent change groups, confirm each one separately. Do not ask for each code line or tool call. Read-only inspection and verification commands already authorized by the plan do not need separate step confirmations.
   - `On`: Continue through all steps in the approved plan without intermediate confirmations.
5. When confirmation is required, state the next action and pause; do not perform it until the user approves. These are model-facing workflow instructions, not an enforcement mechanism. Client/tool permission prompts and separate authorization requirements still apply in every mode.
6. Verify the implementation with relevant checks and report what ran, what passed, and what could not be verified.

The plan does not authorize out-of-scope improvements, branch creation, commits, pushes, destructive operations, or bypassing higher-priority tool permissions. Obtain explicit authorization for those actions separately.

If a step cannot safely follow the plan, stop that step, explain the issue and request a revised plan. The user must explicitly invoke `project-plan` to switch; do not change modes automatically. A "failure" response is feedback, not a mode switch.

After all steps are complete, report the changes and verification. Invite the user to invoke `project-review` for a separate review; do not enter review mode automatically. A "success" response alone is not a mode switch.
