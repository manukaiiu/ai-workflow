# AI Workflow

A structured meta-documentation system for human-AI collaboration on software projects.

## What is this?

A workflow system that helps AI agents and humans work together effectively. The system provides:

- **Multiple work types** - Features, maintenance, bugs, and concept work (analysis/planning)
- **Knowledge retention** - AI builds and maintains project knowledge across sessions
- **Clear workflows** - Simple `>>` commands that expand to full protocols
- **Zero context loss** - Resume work quickly with self-documenting work items
- **Hierarchical documentation** - Minimal always-loaded core, details loaded on-demand
- **Dual-mode operation** - Works within a project-hub or standalone in any project

## Deployment Modes

This system supports two deployment modes:

| Mode | Location | Outputs go to |
|------|----------|---------------|
| **Project-Hub** | `project-hub/ai-workflow/` | Project's folders (`5-work/`, `2-knowledge/`, etc.) |
| **Standalone** | `<project>/ai-workflow/` | ai-workflow's folders (`work/`, `knowledge/`, etc.) |

See [meta/MODE.md](meta/MODE.md) for full details on mode detection and path resolution.

---

## Quick Start: Project-Hub Mode

If ai-workflow is part of a project-hub (shared across projects):

### 1. Clone into project-hub

```bash
cd project-hub
git clone <ai-workflow-remote> ai-workflow
```

### 2. Point the agent to the system

Tell the agent:

    Please read ai-workflow/meta/CORE.md - this explains our workflow system.

### 3. The agent detects mode automatically

The agent sees `coordination/` and `projects/` in the parent folder and knows outputs go to the project's folders.

### 4. Start work

    Human: >>start feat my-first-feature
    AI: [Creates work item in projects/<group>/<project>-root/5-work/]

---

## Quick Start: Standalone Mode

If ai-workflow is embedded in a single project:

### 1. Copy to your project

```bash
cd your-project
git clone <ai-workflow-remote> ai-workflow
# Or: cp -r /path/to/ai-workflow ./ai-workflow
```

### 2. Point the agent to the system

Tell the agent:

    Please read ai-workflow/meta/CORE.md - this explains our workflow system.

The agent reads the core documentation and loads protocol details on-demand.

### 3. Initialize knowledge

    Human: >>init-knowledge
    AI: [Asks questions, creates ai-workflow/knowledge/SYSTEM-OVERVIEW.md]

    Human: >>scan-repo
    AI: [Scans your codebase]

### 4. Start work

    Human: >>start feat my-first-feature
    AI: [Creates work item in ai-workflow/work/]

## Work Types

| Type | Command | Use For |
|------|---------|---------|
| Feature | >>start feat name | New functionality |
| Maintenance | >>start maint name | Updates, refactoring |
| Bug | >>start bug name | Fixing defects |
| Concept | >>start concept name | Analysis, planning, roadmaps |

## Core Commands

| Command | Purpose |
|---------|---------|
| >>start [type] name | Begin new work |
| >>continue | Resume existing work |
| >>wrap | End session (save progress) |
| >>pause | Interrupt with context saved |
| >>status | Quick status check |
| >>archive | Complete and archive work |

Concept work has additional phases: >>extract, >>conceptualize, >>plan, >>roadmap, >>finalize

## Documentation

| Audience | File |
|----------|------|
| Humans | meta/FOR-HUMANS.md |
| AI Agents | meta/CORE.md |
| Reference | meta/reference/ |

## Architecture

The system uses hierarchical loading to minimize context usage:

1. **CORE.md** (~250 lines) - Always loaded, navigation hub
2. **MODE.md** - Mode detection and path resolution
3. **protocols/** - Loaded on-demand when commands are used
4. **reference/** - Consulted as needed for conventions

## Folder Structure

### Project-Hub Mode (ai-workflow is read-only, outputs go to project)
```
project-hub/
├── coordination/           # Hub orchestration
├── ai-workflow/            # THIS REPO (shared, read-only except feedback)
│   └── meta/
│       ├── CORE.md
│       ├── MODE.md
│       ├── protocols/
│       ├── reference/
│       ├── templates/
│       └── meta-feedback/  # Workflow feedback (write OK)
└── projects/<group>/<project>-root/
    ├── CONTEXT.md          # Project entry point
    ├── 1-concepts/
    ├── 2-knowledge/
    ├── 3-inbox/
    ├── 4-workplans/
    ├── 5-work/             # Work items go here
    └── 6-instances/
```

### Standalone Mode (ai-workflow contains everything)
```
<project>/
├── ai-workflow/            # THIS REPO (embedded)
│   ├── meta/
│   │   ├── CORE.md
│   │   ├── MODE.md
│   │   ├── protocols/
│   │   ├── reference/
│   │   ├── templates/
│   │   └── meta-feedback/
│   ├── work/               # Work items go here
│   ├── knowledge/
│   ├── concepts/
│   ├── workplans/
│   └── inbox/
└── <source>/               # Project source code
```

## License

Free to use and modify for your projects.
