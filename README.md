# Project Management System

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.8+](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![OpenClaw Compatible](https://img.shields.io/badge/OpenClaw-Compatible-blue.svg)](https://openclaw.ai)

> A comprehensive project management framework for AI agents. Manage projects from initiation to delivery with structured workflows, templates, and quality gates.

## Overview

Project Management System is a **production-ready workflow orchestration framework** designed specifically for AI agent teams. It provides structured processes, role-based operation manuals, and quality assurance mechanisms for managing projects from start to finish.

### The Problem It Solves

AI agents working on complex projects need:
- **Clear role definitions** - Who does what, when
- **Structured workflows** - Step-by-step processes
- **Quality gates** - Built-in review and acceptance criteria
- **Task tracking** - State machine for task lifecycle
- **Communication protocols** - How agents coordinate

This system provides all of the above, battle-tested in real multi-agent projects.

## Platform Compatibility

| Platform | Support | Notes |
|----------|---------|-------|
| **OpenClaw** | ✅ Native | Designed for OpenClaw agent teams |
| **Claude Code** | ✅ Compatible | Works with Claude's project workflows |
| **Cursor** | ✅ Compatible | Adaptable to Cursor's task system |
| **Generic LLM** | ✅ Compatible | Works with any agent team |

### System Requirements

- **Optional**: Python 3.8+ (for dashboard tools)
- **Optional**: OpenClaw >= 2026.3.0 (for skill integration)
- **Primary**: Markdown-based, works with any text editor

## Architecture

\\\
┌─────────────────────────────────────────────────────────────┐
│                    Project Lifecycle                         │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  Initiate → Define → Dispatch → Execute → Review → Accept   │
│      ↑                                              │        │
│      └────────────── Rework Loop ───────────────────┘        │
│                                                              │
├─────────────────────────────────────────────────────────────┤
│  ROLES: Decision Maker | Dispatcher | Executor              │
├─────────────────────────────────────────────────────────────┤
│  GATES: Quality Review | Acceptance Criteria | Sign-off     │
└─────────────────────────────────────────────────────────────┘
\\\

## Core Components

### Documentation (14 files)

| Document | Purpose | Audience |
|----------|---------|----------|
| \philosophy.md\ | Design principles | All roles |
| \coordinator.md\ | Dispatcher operations | Project leads |
| \executor.md\ | Executor operations | Task executors |
| \	ask-management.md\ | Task state machine | All roles |
| \quality.md\ | Quality assurance | Reviewers |
| \communication.md\ | Communication protocols | All roles |
| \governance.md\ | Decision governance | Decision makers |
| \self-loop.md\ | Runtime recovery | System operators |
| \untime.md\ | Runtime behavior | All roles |
| \lifecycle.md\ | Project phases | All roles |
| \scheduling.md\ | Task scheduling | Dispatchers |
| \knowledge.md\ | Knowledge management | All roles |
| \decision-guide.md\ | Decision making | Decision makers |
| \collaboration.md\ | Multi-agent collaboration | All roles |

### Templates (10 files)

| Template | Purpose | When to Use |
|----------|---------|-------------|
| \project-brief.md\ | Project initiation | Starting new project |
| \	ask-spec.md\ | Task specification | Dispatching tasks |
| \eview-record.md\ | Review documentation | Reviewing deliverables |
| \cceptance-record.md\ | Acceptance proof | Accepting deliverables |
| \change-request.md\ | Scope change | Requesting changes |
| \milestone-report.md\ | Progress update | Milestone completion |
| \inal-report.md\ | Project delivery | Project completion |
| \isk-register.md\ | Risk tracking | Throughout project |
| \	ask-registry.md\ | Task tracking | Throughout project |
| \status.md\ | Status updates | Regular reporting |

## Task State Machine

\\\
                    ┌──────────────┐
                    │   PENDING    │
                    └──────┬───────┘
                           │ Dispatch
                           ▼
                    ┌──────────────┐
         ┌──────────│ IN_PROGRESS  │──────────┐
         │          └──────────────┘          │
         │                   │ Complete       │
         │                   ▼                │
         │          ┌──────────────┐          │
         │          │  COMPLETED   │          │
         │          └──────┬───────┘          │
         │                 │ Review           │
         │                 ▼                  │
         │          ┌──────────────┐          │
         │          │   ACCEPTED   │◄─────────┘
         │          └──────────────┘
         │
         │ Rework
         ▼
  ┌──────────────┐
  │    REWORK    │
  └──────┬───────┘
         │ Resubmit
         └──────────► COMPLETED
\\\

## Installation

### Quick Start

\\\ash
# Clone repository
git clone https://github.com/don068589/project-management.git
cd project-management

# Fill in your resources
# Edit resource-profiles.md to record your agents and tools
\\\

### For OpenClaw Users

\\\ash
# Install as skill
cd ~/.openclaw/skills
git clone https://github.com/don068589/project-management.git
\\\

## Usage

### Role Selection

| Your Role | Start With |
|-----------|------------|
| Project Lead | \docs/coordinator.md\ |
| Task Executor | \docs/executor.md\ |
| Decision Maker | \docs/decision-guide.md\ |
| New to system | \docs/philosophy.md\ |

### Typical Workflow

1. **Start a project** → Use \	emplates/project-brief.md\
2. **Break down tasks** → Use \	emplates/task-spec.md\
3. **Dispatch to executors** → Follow \docs/coordinator.md\
4. **Execute tasks** → Follow \docs/executor.md\
5. **Review deliverables** → Use \	emplates/review-record.md\
6. **Accept or reject** → Update task state
7. **Deliver project** → Use \	emplates/final-report.md\

### Dashboard (Optional)

\\\ash
# View project dashboard
python tools/dashboard.py

# System health check
python tools/system-check.py
\\\

## Quality Gates

### Review Criteria

- [ ] Deliverable matches task specification
- [ ] No critical defects
- [ ] Documentation complete
- [ ] Tests passing (if applicable)
- [ ] Reviewer sign-off

### Acceptance Criteria

- [ ] All review criteria met
- [ ] Integration tested (if applicable)
- [ ] Stakeholder approval
- [ ] Final documentation

## Self-Loop Guarantee

The system includes a **runtime recovery mechanism** (\docs/self-loop.md\) that ensures:

- Agents can recover from interruptions
- Task state is preserved
- No work is lost
- Seamless handoff between agents

## File Structure

\\\
project-management/
├── SKILL.md              # OpenClaw skill definition
├── README.md             # This file
├── CHANGELOG.md          # Version history
├── LICENSE               # MIT license
├── resource-profiles.md  # Executor resources (fill this!)
├── docs/                 # Detailed documentation
│   ├── philosophy.md     # Start here
│   ├── coordinator.md    # For project leads
│   ├── executor.md       # For task executors
│   └── ...               # 14 documents total
├── templates/            # Ready-to-use templates
│   ├── project-brief.md
│   ├── task-spec.md
│   └── ...               # 10 templates total
└── tools/                # Optional utilities
    ├── dashboard.py      # Visual dashboard
    └── system-check.py   # Health check
\\\

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

MIT License - Free to use, modify, and distribute.

## Acknowledgments

Built for the OpenClaw Agent team. Battle-tested in real multi-agent projects.