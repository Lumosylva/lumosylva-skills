---
name: general-spec
description: Explains the five-stage project workflow, optional task-file template, and approval settings. Use when the user asks for the overall workflow or a task-file template; each mode skill also works independently.
---

# Project Workflow Reference

This skill is a reference, not an always-on rule or a default session mode. Installing it does not activate the other skills. Each mode skill contains its own essential instructions and can be used alone.

## Modes

| Skill | Purpose | Default file access |
|-------|---------|---------------------|
| `project-research` | Investigate requirements and existing code | Read-only |
| `project-innovate` | Compare possible approaches | Read-only |
| `project-plan` | Specify an implementation and request approval | Read-only |
| `project-execute` | Implement an approved plan | Approved changes only |
| `project-review` | Compare results with requirements and plan | Read-only |

An agent uses a mode only when the user explicitly invokes that skill by name or through the agent's skill interface. A client may expose `/project-plan`-style shortcuts, but installation alone does not guarantee slash commands. Do not assume a mode is active at the start of a new session.

While a mode is active, start replies with `[MODE: RESEARCH]`, `[MODE: INNOVATE]`, `[MODE: PLAN]`, `[MODE: EXECUTE]`, or `[MODE: REVIEW]` as appropriate. Use the user's language for the rest of the reply. A simple "yes", "no", "success", or "failure" is feedback, not an instruction to change modes. Switch modes only when the user explicitly invokes the next skill; do not switch automatically on completion or error. Follow any higher-priority instructions and tool permissions.

## Authorization

- Research, innovate, plan, and review do not create or edit files, branches, or commits by default. Ask for explicit authorization before persisting a task file or making other state changes.
- Execute requires both an approved plan and an explicit request to use `project-execute`. The plan's approval authorizes only its stated scope; new work requires revised approval.
- Creating a branch, making a commit, pushing, deleting data, or performing other consequential actions requires explicit authorization for that action, even in execute mode.
- Report findings and verification results directly. Do not expose private reasoning or fabricate test results.

## Optional Task File

Only create a task file when the user explicitly requests one. Choose its path with the user or follow the repository's conventions; do not assume a branch name or hard-code `main`. A compact template is:

```markdown
# Task

## Request
[User requirements]

## Findings
[Relevant observations]

## Options
[Considered approaches]

## Approved Plan
[Steps and approval status]

## Progress
[Changes and verification]

## Review
[Findings and outcome]
```

## Step Confirmations

`YOLO_MODE` controls confirmations *within an already approved execute plan*. It is a conversational preference for one `project-execute` invocation, not an operating-system environment variable or persistent client setting. To select a non-default value, the user includes `YOLO_MODE=Ask` or `YOLO_MODE=On` when explicitly invoking `project-execute`. If omitted, use `Off`. Only the user may change it.

- `Off` (default): Ask and wait for approval before each top-level item in the approved checklist. One approval covers the related changes already described by that item.
- `Ask`: Ask and wait before each separately reviewable change group within a checklist item. A group includes all changes needed to deliver and verify one planned outcome, including directly related implementation, tests, and documentation across files. Split groups only when their outcomes have distinct acceptance criteria and can be delivered or reverted independently. Confirm independent groups separately, but do not split by file, code line, or tool call. Read-only inspection and verification commands already authorized by the plan do not need separate step confirmations.
- `On`: Proceed through all steps in the approved plan without intermediate confirmations.

When confirmation is required, state the next action and pause until the user approves. These are model-facing workflow instructions, not an enforcement mechanism. The setting never authorizes scope expansion, commits, pushes, destructive actions, or bypassing client/tool permission prompts; obtain separate authorization where required.
