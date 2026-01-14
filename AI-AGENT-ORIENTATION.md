<!-- template-version: 1.1.0 -->
<!-- template-source: project-hub/_meta/templates/project-root/AI-AGENT-ORIENTATION.md -->

# AI Agent Orientation

Welcome! This file tells you everything you need to know to work effectively in this project.

## Quick Start

1. **Read the workflow system:** `../../../ai-workflow/CORE.md`
2. **Read project context:** `CONTEXT.md` (in this folder)
3. **Check active work:** `5-work/` for ongoing tasks

## System Overview

This project lives within **project-hub**, a centralized structure for managing multiple projects with AI collaboration.

```
project-hub/
├── ai-workflow/          <- Shared workflow system (READ-ONLY)
│   └── CORE.md           <- Start here for methodology
├── coordination/         <- Cross-project coordination
│   ├── PROJECTS.md       <- List of all projects
│   └── PORTS.json        <- Port allocations
└── projects/
    └── <group>/
        └── <project>-root/   <- YOU ARE HERE
            ├── AI-AGENT-ORIENTATION.md  <- This file
            ├── CONTEXT.md               <- Project-specific context
            ├── 1-concepts/              <- Finalized designs
            ├── 2-knowledge/             <- Project knowledge base
            ├── 3-inbox/                 <- Incoming items
            ├── 4-workplans/             <- Approved work plans
            ├── 5-work/                  <- Active work items
            └── 6-instances/             <- Dev environments
                └── <instance>/
                    ├── DB/
                    └── <source>/        <- Actual code repo
```

## Critical Rules

### 1. ai-workflow/ is READ-ONLY (with one exception)

The workflow system at `../../../ai-workflow/` is shared across ALL projects.

- **DO read** `ai-workflow/CORE.md` for methodology and protocols
- **DO NOT write** knowledge, work items, or project data to `ai-workflow/`

**Exception - Feedback:** You MAY write to `../../../ai-workflow/feedback/` to suggest improvements to the workflow system itself. This is the designated channel for agents across all projects to contribute feedback.

### 2. Project Data Stays Here

All project-specific information belongs in THIS project-root folder:

| What | Where | Notes |
|------|-------|-------|
| Knowledge & learnings | `2-knowledge/` | Architecture, decisions, domain info |
| Work items & context | `5-work/` | Active tasks with their own context |
| Concepts & designs | `1-concepts/` | Finalized specifications |
| Incoming items | `3-inbox/` | Bug reports, ideas, requirements |
| Work plans | `4-workplans/` | Approved implementation plans |

### 3. Source Code Lives in Instances

The actual code repository is in `6-instances/<instance>/<source>/`. This is typically a separate git repo.

## Your Workflow

1. **Start each session** by reading:
   - `../../../ai-workflow/CORE.md` (methodology)
   - `CONTEXT.md` (project specifics, current focus)
   - `5-work/` (any active work items)

2. **During work:**
   - Write knowledge to `2-knowledge/`
   - Track work in `5-work/`
   - Code changes go in `6-instances/<instance>/<source>/`

3. **End of session:**
   - Update relevant knowledge files
   - Leave work items in a resumable state

## Key Files to Read

| Priority | File | Purpose |
|----------|------|---------|
| 1 | `../../../ai-workflow/CORE.md` | Workflow methodology |
| 2 | `CONTEXT.md` | Project context & current focus |
| 3 | `2-knowledge/architecture.md` | System architecture |
| 4 | `5-work/` | Active work items |

## Understanding the Bigger Picture

This project is part of **project-hub**, a unified system for multi-project management with AI collaboration.

### Hub-Level Documentation

If you need to understand the overall system:

| File | Purpose |
|------|---------|
| `../../../README.md` | Project-hub overview, setup instructions, how to create projects |
| `../../../STRUCTURE.md` | Complete folder structure explanation, what's tracked by git |
| `../../../coordination/PROJECTS.md` | List of all projects in this hub |
| `../../../coordination/PORTS.json` | Port allocations (check before using ports!) |

### Key Concepts

- **project-hub** is a central place managing multiple projects
- **ai-workflow** provides shared methodology (read-only for projects)
- **coordination/** contains cross-project resources (ports, project list, workspaces)
- **projects/** contains all actual project work, grouped by owner/type
- Each **project-root** is self-contained with concepts, knowledge, work, and instances

### Detailed Specs (if needed)

For deep dives into design decisions:

| File | Purpose |
|------|---------|
| `../../../_meta/FOLDER-STRUCTURE.md` | Complete folder hierarchy spec |
| `../../../_meta/GIT-TOPOLOGY.md` | How git repos are structured |
| `../../../_meta/PORTS.md` | Port allocation system design |
| `../../../_meta/DECISIONS.md` | Design decisions and rationale |

---

*Now proceed to read `../../../ai-workflow/CORE.md` and then `CONTEXT.md`.*
