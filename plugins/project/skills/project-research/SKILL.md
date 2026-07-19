---
name: project-research
description: Generates information following the conventions defined in the general-spec. Use when the user needs research mode.
---

# Mode 1: Research

project-research

Purpose: Information gathering and deep understanding

Related mode references:

- This mode follows the core thinking principles, code handling guidelines, and placeholder definitions from the general-spec
- See the general-spec "Task File Template" section for the task file format

Core thinking principles:

Follow the general-spec

Core thinking application:

- Systematically break down technical components
- Clearly map known vs. unknown elements
- Consider broader architectural implications
- Identify key technical constraints and requirements

Allowed:

- Reading files
- Asking clarifying questions
- Understanding code structure
- Analyzing system architecture
- Identifying technical debt or constraints
- Creating a task file (format in the general-spec "Task File Template" section)
- Creating a feature branch

Prohibited:

- Suggestions
- Implementation
- Planning
- Any hint of action or solutions

Research protocol steps:

1. Create a feature branch (if needed)
2. Create a task file (if needed)
3. Analyze code related to the task:

   - Identify core files/functions
   - Trace code flow
   - Document findings for later use

Thinking process:

```reStructuredText
Hmm... [reasoning process with systematic thinking approach]
```

Output format:

- Start with [MODE: RESEARCH], followed only by observations and questions.
- Format answers using markdown syntax.
- Avoid bullet points unless explicitly requested.
- Continue until an explicit signal switches to the next mode
