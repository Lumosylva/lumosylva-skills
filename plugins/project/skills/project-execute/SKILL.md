---
name: project-execute
description: Generates information following the conventions defined in the general-spec. Use when the user needs execute mode.
---

# Mode 4: Execute

project-execute

Purpose: Accurately implement what was planned in Mode 3 (Plan)

Related mode references:

- This mode follows the core thinking principles, code handling guidelines, and placeholder definitions from the general-spec
- See the general-spec "Task File Template" section for the task file format
- Next mode: Review mode will verify that this mode's implementation matches the plan
- Rollback mode: If implementation deviates from the plan, return to Plan mode for readjustment

Core thinking principles:

Follow the general-spec

Core thinking application:

- Focus on accurate implementation of specifications
- Apply systematic verification during implementation
- Maintain precise adherence to the plan
- Implement complete features with proper error handling

Allowed:

- Only implement what is explicitly detailed in the approved plan
- Follow the numbered checklist exactly
- Mark completed checklist items
- Update the "Task Progress" section after each implementation (this is a standard part of execution, considered a built-in step of the plan)

Prohibited:

- Any deviation from the plan
- Improvements not specified in the plan
- Creative additions or "better ideas"
- Skipping or abbreviating code sections

Execution protocol steps:

1. Implement changes exactly as planned

2. After each implementation, append to "Task Progress" (as a standard step of plan execution):

   ```reStructuredText
   [datetime]
   - Modified: [list of files and code changes]
   - Change: [summary of the change]
   - Reason: [why this change was made]
   - Blockers: [list of factors preventing this update from succeeding]
   - Status: [unconfirmed|success|failure]
   ```

3. Ask the user for confirmation: "Status: success/failure?"

4. If failure: return to Plan mode

5. If success and more changes needed: continue to the next item

6. If all implementation is complete: switch to Review mode

Code quality standards:

- Always show full code context
- Specify language and path in code blocks
- Proper error handling
- Standardized naming conventions
- Clear and concise comments

Deviation handling:

If any issue requiring deviation is found, immediately return to Plan mode

Output format:

Start with [MODE: EXECUTE], followed only by implementation that matches the plan. Include which checklist item is being completed.
