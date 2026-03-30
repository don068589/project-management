# SKILL.md - Project Management System

A comprehensive project management system for AI agents. Manage projects from initiation to delivery with structured workflows, templates, and quality gates.

## Description

A universal project management system. Covers full process management from project initiation to acceptance, including:
- Role operation manuals (Dispatcher/Executor)
- 14 rule documents
- 10 template files
- Quality assurance mechanisms
- Task state machine
- Self-loop guarantee

## When to Use

- User requests project initiation or planning
- User mentions "project management", "task dispatch", "review and acceptance"
- Multi-agent collaboration needed for complex tasks
- Need to track project progress and quality

## Installation

```bash
cd ~/.openclaw/skills
git clone https://github.com/openclaw/project-management.git
```

## Post-Installation Setup

### 1. Initialize Resource Profiles

For first use, fill in `resource-profiles.md` to record your execution resources:

```markdown
### Example: Claude Code

**Basic Information**
- Type: CLI tool
- First collaboration: 2026-03-30

**Capabilities**
- Complex code refactoring
- Multi-file modification
- Code review

**Invocation Method**
- Command: `claude --print --permission-mode bypassPermissions`
```

### 2. Optional: Add to Agent's TOOLS.md

If you want the agent to proactively use this system, add to the agent's TOOLS.md:

```markdown
## Project Management System

- **Location**: ~/.openclaw/skills/project-management/
- **Purpose**: Project initiation, task dispatch, review and acceptance
- **Trigger**: User mentions "project management", "initiate project", "dispatch task"
```

## Quick Start

### 1. Initialize

For first use, fill in `resource-profiles.md` to record your execution resources (agents, CLI tools, etc.).

### 2. Dispatcher (Project Commander)

```
Read docs/coordinator.md → Understand the complete process
Use templates/project-brief.md → Create project initiation document
Use templates/task-spec.md → Create task specification
Use templates/review-record.md → Review and acceptance
```

### 3. Executor (Task Worker)

```
Read docs/executor.md → Understand execution standards
Read task-spec → Execute according to specification
Update task status → Report progress
```

## Files Structure

```
project-management/
├── SKILL.md              # This file
├── README.md             # System outline
├── data_structure.md     # Project repository index
├── docs/                 # Detailed rule documents
│   ├── coordinator.md    # Dispatcher operation manual ⭐
│   ├── executor.md       # Executor operation manual ⭐
│   ├── philosophy.md     # Design philosophy
│   └── ...               # Other documents
├── templates/            # Template library
│   ├── project-brief.md  # Project initiation ⭐
│   ├── task-spec.md      # Task specification ⭐
│   └── ...               # Other templates
└── tools/
    ├── dashboard.py      # Project dashboard
    └── system-check.py   # Integrity check
```

## Key Workflows

### Project Lifecycle

```
Initiate project → Requirement confirmation → Break down → Dispatch → Execute → Review → Acceptance → Archive
```

### Task Status

```
Pending dispatch → In progress → Pending review → Accepted
                                  ↓
                               Rework → Pending review
```

## Customization

- `resource-profiles.md`: Fill in your execution resource information
- `templates/`: Modify templates as needed
- `improvements.md`: Record improvement suggestions

## Dependencies

- Python 3.8+ (optional, for dashboard.py)
- Git (optional, for system-check.py)

## License

MIT License

## Links

- [GitHub](https://github.com/openclaw/project-management)
- [Documentation](./docs/)
