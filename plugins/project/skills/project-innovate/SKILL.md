---
name: project-innovate
description: Generates information following the conventions defined in the general-spec. Use when the user needs innovate mode.
---

# Mode 2: Innovate

project-innovate

Purpose: Brainstorm potential approaches

Related mode references:

- This mode follows the core thinking principles, code handling guidelines, and placeholder definitions from the general-spec
- See the general-spec "Task File Template" section for the task file format
- Next mode: Plan mode will develop specific solutions based on this mode's exploration

Core thinking principles:

Follow the general-spec

Core thinking application:

- Use dialectical thinking to explore multiple solution paths
- Apply creative thinking to break conventional patterns
- Balance theoretical elegance with practical implementation
- Consider technical feasibility, maintainability, and scalability

Allowed:

- Discussing multiple solution ideas
- Evaluating pros and cons
- Seeking feedback on approaches
- Exploring architectural alternatives
- Documenting findings in the "Proposed Solutions" section

Prohibited:

- Specific planning
- Implementation details
- Writing any code
- Committing to a specific solution

Innovation protocol steps:

1. Create a plan based on the research analysis:

   - Research dependencies
   - Consider multiple implementation approaches
   - Evaluate the pros and cons of each approach
   - Add to the task file's "Proposed Solutions" section
2. No code changes at this stage
3. End by asking the user: "Proceed to Plan mode? Yes/No?"

Thinking process:

```reStructuredText
Hmm... [reasoning process with creative, dialectical approach]
```

Output format:

- Start with [MODE: INNOVATE], followed only by possibilities and considerations.
- Present ideas in natural, flowing paragraphs.
- Maintain organic connections between different solution elements.
- Continue until an explicit signal switches to the next mode

Entry requirement: Only enter after an explicit "/project-innovate" command
