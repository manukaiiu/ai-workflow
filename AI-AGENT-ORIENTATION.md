<!-- template-version: 1.0.0 (customized for ai-workflow) -->

# AI Agent Orientation: ai-workflow Development

Welcome! You are working on **ai-workflow**, the workflow methodology system for AI agents in project-hub.

## Quick Start

1. **Read project context:** `CONTEXT.md` (in this folder)
2. **Check status:** `STATUS.md` for current progress
3. **Check active work:** `5-work/` for ongoing tasks
4. **Understand the handover:** `HANDOVER.md` explains what happened and what remains

## System Overview

This is a **special project-root** within project-hub. Unlike other projects:
- This project IS the ai-workflow system itself
- The workflow content lives directly in this folder (after flattening meta/)
- An installed copy exists at `project-hub/ai-workflow/` for other projects to read

```
project-hub/
├── ai-workflow/              <- INSTALLED VERSION (copy from here)
│   ├── CORE.md               <- Entry point for project agents
│   ├── protocols/
│   ├── reference/
│   ├── templates/
│   └── feedback/             <- Writable by project agents
│
└── projects/
    └── system/
        └── ai-workflow-root/     <- YOU ARE HERE (DEVELOPMENT)
            ├── AI-AGENT-ORIENTATION.md  <- This file
            ├── CONTEXT.md
            ├── STATUS.md
            ├── CHANGELOG.md
            ├── HANDOVER.md              <- Transition instructions
            │
            │   (Workflow content - will be copied to installed)
            ├── CORE.md
            ├── FOR-HUMANS.md
            ├── protocols/
            ├── reference/
            ├── templates/
            ├── feedback/
            │
            │   (Development artifacts - stay here)
            ├── 1-concepts/
            ├── 2-knowledge/
            ├── 3-inbox/
            ├── 4-workplans/
            └── 5-work/
```

## Critical Rules

### 1. This IS the Development Environment

You are in the development version of ai-workflow. Changes here need to be released to the installed version:

```bash
# From project-hub root
rm -rf ai-workflow
cp -r projects/system/ai-workflow-root/ai-workflow ai-workflow
```

Wait - that's the future state. First, you need to complete the restructure (see HANDOVER.md).

### 2. Separate Development from Distribution

| What | Where | Notes |
|------|-------|-------|
| Workflow content (CORE.md, protocols/, etc.) | This folder (root) | Gets copied to installed |
| Development knowledge | `2-knowledge/` | Stays here |
| Work items | `5-work/` | Stays here |
| Concepts & designs | `1-concepts/` | Stays here |
| Incoming feedback | `feedback/` | Gets copied to installed |

### 3. feedback/ is Special

The `feedback/` folder receives contributions from project agents across the hub. It must:
- Exist in both dev and installed versions
- Be writable in the installed version
- Be reviewed periodically and incorporated into improvements

## Your Workflow

1. **Start each session** by reading:
   - `CONTEXT.md` (project identity)
   - `STATUS.md` (current progress)
   - `HANDOVER.md` (if transitioning)
   - `5-work/` (active work items)

2. **During work:**
   - Write knowledge to `2-knowledge/`
   - Track work in `5-work/`
   - Modify workflow content (CORE.md, protocols/, etc.) directly

3. **After significant changes:**
   - Update `STATUS.md`
   - Consider releasing to installed version
   - Update `CHANGELOG.md`

## Key Files to Read

| Priority | File | Purpose |
|----------|------|---------|
| 1 | `CONTEXT.md` | Project identity & current focus |
| 2 | `STATUS.md` | Current progress |
| 3 | `HANDOVER.md` | Transition instructions (if present) |
| 4 | `CORE.md` | The actual workflow methodology |

## Understanding the Bigger Picture

This project is part of **project-hub**, a unified system for multi-project management with AI collaboration.

### Hub-Level Documentation

| File | Purpose |
|------|---------|
| `../../../README.md` | Project-hub overview |
| `../../../STRUCTURE.md` | Complete folder structure explanation |
| `../../../_meta/FOLDER-STRUCTURE.md` | Detailed folder spec |

---

*Now proceed to read `CONTEXT.md` and `STATUS.md`.*
