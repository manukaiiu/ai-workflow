# Handover: ai-workflow Restructure

This document explains the structure and how to work with ai-workflow development.

---

## Structure

```
ai-workflow-root/                    <- THE GIT REPO (project-root)
├── AI-AGENT-ORIENTATION.md          <- Agent entry point
├── CONTEXT.md                       <- Project identity
├── STATUS.md                        <- Current progress
├── CHANGELOG.md                     <- Milestones
├── HANDOVER.md                      <- This file
├── .gitignore
│
├── 1-concepts/                      <- Design work for ai-workflow
├── 2-knowledge/                     <- Development knowledge
├── 3-inbox/                         <- Incoming ideas
├── 4-workplans/                     <- Development plans
├── 5-work/                          <- Active development tasks
└── 6-instances/
    └── main/
        └── ai-workflow/             <- THE ARTIFACT
            ├── CORE.md              <- Main entry for consumers
            ├── FOR-HUMANS.md
            ├── MODE.md
            ├── README.md
            ├── protocols/
            ├── reference/
            ├── templates/
            ├── feedback/            <- Receives feedback from projects
            └── archive/
```

## Key Concepts

### 1. Project-Root vs Artifact

- **Project-root level** (`ai-workflow-root/`): Development metadata - CONTEXT.md, STATUS.md, numbered folders
- **Artifact** (`6-instances/main/ai-workflow/`): The actual workflow system that gets distributed

### 2. Single Repo, No Nesting

The ai-workflow-root IS the git repo. The artifact inside `6-instances/main/ai-workflow/` is just a folder, not a separate repo.

### 3. Release Process

To release changes to the installed version:

```bash
# From project-hub root
rm -rf ai-workflow
cp -r projects/system/ai-workflow-root/6-instances/main/ai-workflow ai-workflow
```

### 4. feedback/ is Bidirectional

- Project agents write feedback to `project-hub/ai-workflow/feedback/`
- During development, review this feedback in `6-instances/main/ai-workflow/feedback/`
- On release, updated feedback folder gets copied to installed version

## Development Workflow

1. **Read the installed ai-workflow** (`../../../ai-workflow/CORE.md`) for methodology
2. **Work on the artifact** in `6-instances/main/ai-workflow/`
3. **Track development** in `2-knowledge/`, `5-work/`
4. **Release** by copying artifact to installed location

---

*This handover documents the ai-workflow development structure.*
