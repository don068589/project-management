# Task Registry (Project-Level)

> The registry is a per-project anti-duplication mechanism. Each project directory has its own `task-registry.md`.
> This file stays in `system/` as documentation, not recording actual tasks.

## Mechanism

- Registry prevents multiple executors from doing the same thing in one project
- Each project directory has its own `task-registry.md` for task claims within that project
- Cross-project anti-duplication is handled by coordinator's scheduling responsibility
- On project initiation, copy from `templates/task-registry.md` to project directory
- Format and rules see `docs/task-management.md` task claiming mechanism

---

> Reference document, not actual task records