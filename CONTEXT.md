<!-- template-version: 1.0.0 (customized for ai-workflow) -->

# Project Context: ai-workflow

## Quick Facts

- **Owner:** project-hub system
- **Stack:** Markdown documentation
- **Status:** Active (undergoing restructure)
- **Type:** Workflow methodology system for AI agents

## Description

**ai-workflow** is the shared workflow methodology system for AI collaboration within project-hub. It provides:

- Core workflow concepts and protocols (CORE.md)
- Session management patterns
- Knowledge and work item structures
- Handover protocols for session continuity
- Templates for common documentation patterns

This is a meta-project: it defines how AI agents work across ALL projects in the hub. The methodology documented here is consumed by project agents as a read-only resource.

## Current State: Restructure Complete

This project-root was converted from a dual-purpose repo to a proper project-root structure. The transition is **complete**.

**What was done:**
- The ai-workflow repo was moved from `project-hub/ai-workflow/` to `projects/system/ai-workflow-root/`
- Project-root template files were added (CONTEXT.md, STATUS.md, CHANGELOG.md, numbered folders)
- `meta/` folder flattened to root level
- `meta-meta/` content relocated (feedback/ to root, dev docs to 2-knowledge/)
- Installed version created at `project-hub/ai-workflow/`
- All internal references updated

**See:** `HANDOVER.md` for historical transition documentation.

## Folder Structure

After restructure completes, this will be the structure:

```
ai-workflow-root/
├── AI-AGENT-ORIENTATION.md  <- Start here
├── CONTEXT.md               <- You are here
├── STATUS.md
├── CHANGELOG.md
├── HANDOVER.md              <- Transition instructions
│
│   (Workflow content - copied to installed version)
├── CORE.md                  <- Main entry for project agents
├── FOR-HUMANS.md            <- Human-readable overview
├── protocols/               <- Detailed protocols
├── reference/               <- Reference documentation
├── templates/               <- Workflow templates
├── feedback/                <- Receives feedback from projects
│
│   (Development artifacts - stay here)
├── 1-concepts/              <- Finalized designs for ai-workflow
├── 2-knowledge/             <- Development knowledge
├── 3-inbox/                 <- Incoming ideas
├── 4-workplans/             <- Development plans
└── 5-work/                  <- Active development work
```

## Key Concepts

### Dual Nature

This project has two aspects:
1. **Development:** Where ai-workflow is improved (this project-root)
2. **Distribution:** The installed copy at `project-hub/ai-workflow/` that projects read

### Release Process

After making changes:

```bash
# From project-hub root
rm -rf ai-workflow
cp -r projects/system/ai-workflow-root/CORE.md ai-workflow/
cp -r projects/system/ai-workflow-root/FOR-HUMANS.md ai-workflow/
cp -r projects/system/ai-workflow-root/protocols ai-workflow/
cp -r projects/system/ai-workflow-root/reference ai-workflow/
cp -r projects/system/ai-workflow-root/templates ai-workflow/
cp -r projects/system/ai-workflow-root/feedback ai-workflow/
```

(Or a more elegant script once the structure is finalized.)

### feedback/ is Bidirectional

- Project agents write feedback to `project-hub/ai-workflow/feedback/`
- During development, review this feedback and incorporate improvements
- The feedback folder exists in both dev and installed versions

## Current Focus

**Immediate priority:** Complete the restructure transition (see HANDOVER.md)

**After restructure:**
- Review and incorporate any pending feedback
- Continue methodology improvements
- Document the release process

## Links

- **Repository:** This folder IS the repository (git repo at root)
- **Installed version:** `../../../ai-workflow/` (after restructure)
- **Project-hub docs:** `../../../README.md`
