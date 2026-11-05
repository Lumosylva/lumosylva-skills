---
name: project-execute
description: Implements and verifies a presented final project plan within its authorized scope. Explicitly invoking project-execute approves the presented plan by default.
---

# Execute Mode

Use this skill only when the user explicitly invokes `project-execute` (including `/project-execute` if supported) and a final plan has been presented. By default, that invocation approves the presented plan. If the user rejects the plan, requests changes, or has not been shown a final plan, do not treat the invocation as approval; ask them to approve or revise the plan first. Start each response while active with `[MODE: EXECUTE]`, then answer in the user's language.

## Scope And Confirmations

1. Check the approved checklist and the current worktree; preserve unrelated changes.
2. Before starting implementation steps, persist the approved plan in a task file. Determine the project root in this order: use the Git worktree root containing the current working directory; otherwise use the single project/workspace root supplied by the client. If several roots are supplied and the target is ambiguous, ask the user to choose. If neither Git nor a single client root is available, use the current working directory. Inspect that root's `.tasks/` directory and create it automatically when missing.
3. Inspect the existing `.tasks/` layout before choosing a file. Name the file `YYYY-MM-DD_plan-xxx.md`, using the current local date and a short plan identifier. Try a unique suffix when a candidate exists. Create the file with an exclusive no-overwrite operation; if another process creates that name first, choose another suffix and retry. Never rely on a separate existence check followed by an overwrite-capable write. If the available tools cannot create a file exclusively, stop before writing and record the blocker. Record the approved request and plan, approval status, scope, applicable interface and data conventions, verification items, the itemized execution checklist, and progress. Keep this task file as the execution record and update it as work proceeds.
4. Execute only authorized steps, recording progress both in the task file and in the response. For each checklist item, record the checks needed to establish completion. Mark it complete only after its relevant checks pass, such as type checks, boundary checks, or other checks specified by the plan. Record check outcomes and blockers; leave an item incomplete when checks fail or remain unrun. Update the progress section after each item is verified and whenever execution is blocked or its status changes.
5. Treat `YOLO_MODE` as a conversational preference for this `project-execute` invocation, not as an operating-system environment variable or persistent client setting. The user may select a non-default value by including `YOLO_MODE=Ask` or `YOLO_MODE=On` when explicitly invoking this skill. If omitted, use `Off`. Only the user may change the setting.
6. Apply the selected confirmation boundary:
   - `Off` (default): Plan invocation approval does not replace step confirmations. Ask and wait for approval before starting each top-level item in the approved checklist. One approval covers the related changes already described by that item.
   - `Ask`: Ask and wait before each separately reviewable change group within an approved checklist item. A group includes all changes needed to deliver and verify one planned outcome, including directly related implementation, tests, and documentation across files. Split groups only when their outcomes have distinct acceptance criteria and can be delivered or reverted independently. Do not split by file, code line, or tool call. Read-only inspection and verification commands already authorized by the plan do not need separate step confirmations.
   - `On`: Continue through all steps in the approved plan without intermediate confirmations.
7. When confirmation is required, state the next action and pause; do not perform it until the user approves. These are model-facing workflow instructions, not an enforcement mechanism. Client/tool permission prompts and separate authorization requirements still apply in every mode.
8. Verify the implementation with relevant checks and report what ran, what passed, and what could not be verified.

The plan does not authorize out-of-scope improvements, branch creation, commits, pushes, destructive operations, or bypassing higher-priority tool permissions. Obtain explicit authorization for those actions separately.

If a step cannot safely follow the plan, stop that step, explain the issue and request a revised plan. The user must explicitly invoke `project-plan` to switch; do not change modes automatically. A "failure" response is feedback, not a mode switch.

After all steps are complete, report the changes and verification. Invite the user to invoke `project-review` for a separate review; do not enter review mode automatically. A "success" response alone is not a mode switch.
