# Lumosylva Skills

A collection of Claude Code plugins providing structured expert programming skill workflows.

## Design Philosophy

AI coding tools tend to be overly eager—making changes without explicit permission and assuming they know better than the user. Lumosylva Skills enforces mandatory mode declarations and strict responsibility boundaries to ensure AI always does the right thing at the right stage, preventing unauthorized modifications and destructive changes.

## Plugin List

| Plugin | Description | Path |
|--------|-------------|------|
| [project](plugins/project) | Structured expert programming skills with five collaborative modes for rigorous software development workflows | `plugins/project` |

## Workflow Overview

```
Research → Innovate → Plan → Execute → Review
  ^                              |
  └───── Rollback on issues ─────┘
```

Each new session starts in **Research mode** by default. Switch to the next phase using explicit signal commands.

## Five Collaborative Modes

| Mode | Command | Purpose | Core Capabilities |
|------|---------|---------|-------------------|
| Research | `/project-research` | Information gathering and deep understanding | Read files, analyze architecture, identify technical debt |
| Innovate | `/project-innovate` | Brainstorm potential approaches | Explore multiple solutions, weigh pros and cons, document findings |
| Plan | `/project-plan` | Create detailed technical specifications | File paths, function signatures, checklist generation |
| Execute | `/project-execute` | Accurately implement the approved plan | Follow checklist item by item, track progress |
| Review | `/project-review` | Verify implementation matches the plan | Line-by-line comparison, flag deviations, prepare commits |

## Installation

### Install from GitHub

```bash
# Claude Code
claude plugin install Lumosylva/lumosylva-skills

# MiMoCode
mimo plugin install Lumosylva/lumosylva-skills
```

### Manual Installation

Copy the plugin folders from the `plugins/` directory into your skills directory:

- Claude Code: `.claude/skills/`
- MiMoCode: `.mimocode/skills/`

## Core Protocol

- **Mode Declaration**: Every response must begin with `[MODE: XXX]` declaring the current mode
- **Responsibility Isolation**: Each mode may only perform actions allowed at that stage
- **Rollback Mechanism**: When issues are discovered during execution, automatically return to Plan mode for readjustment
- **Mode Switching**: Must be triggered by explicit signals (e.g., `/project-execute`); never switch on your own

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

## Contributing

Issues and pull requests are welcome.

## License

MIT License - see [LICENSE](LICENSE)
