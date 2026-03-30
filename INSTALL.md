# Installation Guide

## Prerequisites

- **OpenClaw** installed and configured (optional for standalone use)
- **Python 3.8+** (optional, for dashboard tool)
- **Git** (optional, for system-check.py)

## Step 1: Download

### Method A: Clone from GitHub

```bash
git clone https://github.com/openclaw/project-management.git
cd project-management
```

### Method B: Install as OpenClaw Skill

```bash
cd ~/.openclaw/skills
git clone https://github.com/openclaw/project-management.git
```

### Method C: Download ZIP

Download and extract from [GitHub Releases](https://github.com/openclaw/project-management/releases).

## Step 2: Configure Resources

Fill in `resource-profiles.md` to record your execution resources:

```markdown
### Example: Your Agent Team

**Basic Information**
- Type: AI Agent
- First collaboration: YYYY-MM-DD

**Capabilities**
- Task type A
- Task type B
- Task type C

**Invocation Method**
- Method: sessions_send(agentId="xxx", message="...")
```

## Step 3: Read Documentation

According to your role:

| Role | First Read |
|------|------------|
| Project Commander | `docs/coordinator.md` |
| Task Executor | `docs/executor.md` |
| Dual Role | `docs/philosophy.md` |

## Step 4: Start Using

1. Create project initiation: `templates/project-brief.md`
2. Break down tasks: `templates/task-spec.md`
3. Dispatch to execution resources
4. Review and acceptance: `templates/review-record.md`

## Verify Installation

Check system file integrity:

```bash
python3 tools/system-check.py
```

On Windows:

```bash
python tools/system-check.py
```

## Optional: Project Dashboard

View project status:

```bash
python3 tools/dashboard.py --project your-project-name
```

## Post-Installation Directory Structure

```
project-management/
├── docs/                 # Read by role
├── templates/            # Copy and use
├── tools/                # Optional tools
├── resource-profiles.md  # Your resources (needs to be filled!)
├── SKILL.md              # Skill definition
└── README.md             # Documentation
```

## Updates

```bash
git pull origin main
```

## Common Issues

### "Module not found"
Python scripts are optional. The core system does not depend on them.

### "Where to put project data?"
Create a separate `projects-data/` directory outside the system directory.

## Next Steps

- Read your role's operation manual
- Try the templates with a simple project
- Update `resource-profiles.md` as resources increase
