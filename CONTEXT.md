<!-- template-version: 1.1.0 -->
<!-- template-source: project-hub/_meta/templates/project-root/CONTEXT.md -->

# Project Context: ai-workflow

## Quick Facts

- **Client/Owner:** project-hub system
- **Stack:** Markdown documentation
- **Status:** Active
- **Main Instance:** `6-instances/main/ai-workflow/`

## Description

**ai-workflow** is the workflow methodology system for AI agents in project-hub. It provides:

- Core workflow concepts and protocols (CORE.md)
- Session management patterns
- Knowledge and work item structures
- Handover protocols for session continuity
- Templates for common documentation patterns

This project develops the ai-workflow system. The artifact lives in `6-instances/main/ai-workflow/` and gets copied to `project-hub/ai-workflow/` for other projects to use.

## Agent Instructions

This project lives within **project-hub**, a centralized system for managing multiple projects.

### Important: Centralized Workflow System

The workflow system (`ai-workflow/`) is **shared and read-only** for projects:

- **Location:** `../../../ai-workflow/CORE.md` (relative to this file)
- **Do NOT write to ai-workflow/** - it's a shared resource across all projects
- **Project-specific data stays HERE** in this project-root folder

### Where Things Live

| What | Where | Writable? |
|------|-------|-----------|
| Workflow methodology | `../../../ai-workflow/` | NO (read-only) |
| Project knowledge | `2-knowledge/` | YES |
| Work items & context | `5-work/` | YES |
| Concepts & designs | `1-concepts/` | YES |
| The artifact (dev) | `6-instances/main/ai-workflow/` | YES |

### Getting Started

1. **Read the workflow system:** `../../../ai-workflow/CORE.md`
2. **Read this file completely** for project-specific context
3. **Check active work:** `5-work/` for ongoing tasks
4. **Check knowledge base:** `2-knowledge/` for architecture and decisions

### Key Files to Know

| File | Purpose |
|------|---------|
| `6-instances/main/ai-workflow/CORE.md` | The artifact being developed |
| `2-knowledge/` | Development knowledge |
| `5-work/` | Current work items |

## Current Focus

**Current priority:** Continue ai-workflow methodology improvements

**Recent context:** Restructure completed - ai-workflow now uses proper project-root structure with artifact in `6-instances/main/ai-workflow/`.

## Folder Structure

```
ai-workflow-root/
├── CONTEXT.md          ← You are here
├── AI-AGENT-ORIENTATION.md
├── STATUS.md
├── CHANGELOG.md
├── HANDOVER.md
│
├── 1-concepts/         ← Design work
├── 2-knowledge/        ← Development knowledge
├── 3-inbox/            ← Incoming ideas
├── 4-workplans/        ← Development plans
├── 5-work/             ← Active tasks
└── 6-instances/
    └── main/
        └── ai-workflow/    ← THE ARTIFACT
            ├── CORE.md
            ├── protocols/
            ├── reference/
            ├── templates/
            └── feedback/
```

## Links

- **Repository:** This folder IS the repository
- **Artifact:** `6-instances/main/ai-workflow/`
- **Installed version:** `../../../ai-workflow/`
- **Project-hub docs:** `../../../README.md`
