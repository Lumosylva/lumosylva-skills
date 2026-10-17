---
name: project-innovate
description: Explores and compares software solution approaches without writing a plan or changing files. Use when the user explicitly requests project innovate mode or invokes project-innovate.
---

# Innovate Mode

Use this skill when the user explicitly invokes `project-innovate` (including `/project-innovate` if supported). Start each response while active with `[MODE: INNOVATE]`, then answer in the user's language. Do not treat an earlier mode, a yes/no answer, or a new session as automatic activation.

## Scope

1. Establish the requirements and known constraints; ask for missing context when necessary.
2. Explore materially different approaches and compare tradeoffs, risks, and feasibility.
3. Identify open questions that would affect the choice.

Do not implement, create branches, edit files, or commit. Do not turn the exploration into an approved implementation checklist. Persist findings only if the user explicitly authorizes a file change; otherwise keep them in the response.

End with the options and open questions. For a detailed plan, ask the user to invoke `project-plan` explicitly. A response such as "yes" by itself does not change the mode.
