# project

A set of structured expert programming skills that guide AI through five collaborative modes for rigorous software development workflows, preventing unauthorized modifications and destructive changes.

## Design Philosophy

AI coding tools tend to be overly eager—making changes without explicit permission and assuming they know better than the user. This skill enforces mandatory mode declarations and strict responsibility boundaries to ensure AI always does the right thing at the right stage.

## Project Structure

```
skills/
├── project-skill/         # General spec (foundation for all modes)
├── project-research/      # Mode 1: Research
├── project-innovate/      # Mode 2: Innovate
├── project-plan/          # Mode 3: Plan
├── project-execute/       # Mode 4: Execute
└── project-review/        # Mode 5: Review
```

## Five Modes

| Mode | Command | Purpose | Core Capabilities |
|------|---------|---------|-------------------|
| Research | `/project-research` | Information gathering and deep understanding | Read files, analyze architecture, identify technical debt |
| Innovate | `/project-innovate` | Brainstorm potential approaches | Explore multiple solutions, weigh pros and cons, document findings |
| Plan | `/project-plan` | Create detailed technical specifications | File paths, function signatures, checklist generation |
| Execute | `/project-execute` | Accurately implement the approved plan | Follow checklist item by item, track progress |
| Review | `/project-review` | Verify implementation matches the plan | Line-by-line comparison, flag deviations, prepare commits |

## Workflow

```
Research → Innovate → Plan → Execute → Review
  ^                              |
  └───── Rollback on issues ─────┘
```

Each new session starts in **Research mode** by default. Switch to the next phase using explicit signal commands.

## Core Protocol

- **Mode Declaration**: Every response must begin with `[MODE: XXX]` declaring the current mode
- **Responsibility Isolation**: Each mode may only perform actions allowed at that stage
- **Rollback Mechanism**: When issues are discovered during execution, automatically return to Plan mode for readjustment
- **Mode Switching**: Must be triggered by explicit signals (e.g., `/project-execute`); never switch on your own
- **No Emojis**: Output must not use emojis unless explicitly requested

## Installation

Copy the folders under the `skills/` directory into your skills directory (e.g., `.claude/skills/` or the corresponding skill path for your AI tool).

## Placeholders

| Placeholder | Description | Example |
|-------------|-------------|---------|
| `TASK_FILE_NAME` | Task file name | `2025-01-14_1` |
| `TASK_IDENTIFIER` | Short task identifier | `fix-cache-bug` |
| `MAIN_BRANCH` | Main branch name | `main` |
| `YOLO_MODE` | Confirmation mode | `Ask` / `On` / `Off` |

### Yolo Mode

- **Ask**: Prompt the user for confirmation before each step
- **On**: Execute all steps automatically (high risk)
- **Off** (default): Require user confirmation for every significant step

## License

MIT
