# Dual-Mode Operation

The ai-workflow system supports two deployment modes. Detect your mode at session start to resolve paths correctly.

---

## Mode Detection

**Check the parent directory structure to determine mode:**

```
ai-workflow/..        ← Look here
```

| If parent contains... | Mode | You are at... |
|-----------------------|------|---------------|
| `coordination/` + `projects/` | **Project-Hub** | `project-hub/ai-workflow/` |
| Neither | **Standalone** | `<project>/ai-workflow/` |

### Quick Detection Command

```bash
# Run from ai-workflow folder
ls .. | grep -E "^(coordination|projects)$" | wc -l
# Result: 2 = Project-Hub mode, <2 = Standalone mode
```

---

## Mode Comparison

| Aspect | Project-Hub Mode | Standalone Mode |
|--------|------------------|-----------------|
| ai-workflow location | `project-hub/ai-workflow/` | `<project>/ai-workflow/` |
| ai-workflow access | **Read-only** (shared system) | **Read-write** (embedded) |
| Project context | Via `CONTEXT.md` in project-root | Via codebase exploration |
| Work outputs | Project's folders | ai-workflow's folders |

---

## Path Resolution

### Project-Hub Mode

The ai-workflow system is shared. Outputs go to the **active project's folders**.

**Project root location:** `project-hub/projects/<group>/<project>-root/`

| Content Type | Path (relative to project-root) |
|--------------|--------------------------------|
| Work items | `5-work/NNN-TYPE-name/` |
| Knowledge | `2-knowledge/` |
| Concepts | `1-concepts/` |
| Workplans | `4-workplans/` |
| Inbox | `3-inbox/` |
| Instances | `6-instances/` |

**Workflow feedback:** `project-hub/ai-workflow/feedback/`
(This is the one exception - feedback about the workflow system itself goes here)

### Standalone Mode

The ai-workflow system is embedded. Outputs go to **ai-workflow's own folders**.

**ai-workflow location:** `<project>/ai-workflow/`

| Content Type | Path (relative to ai-workflow) |
|--------------|-------------------------------|
| Work items | `work/NNN-TYPE-name/` |
| Knowledge | `knowledge/` |
| Concepts | `concepts/` |
| Workplans | `workplans/` |
| Inbox | `inbox/` |

**Workflow feedback:** `<project>/ai-workflow/feedback/`

---

## Session Start by Mode

### Project-Hub Mode

1. **Detect mode** (you're here if parent has `coordination/` + `projects/`)
2. **Read project orientation:**
   - `projects/<group>/<project>-root/AI-AGENT-ORIENTATION.md` (agent entry point)
3. **Read project context:**
   - `<project>-root/CONTEXT.md` (project identity & setup)
4. **Check current status:**
   - `<project>-root/STATUS.md` (living progress doc)
5. **Check for active work:**
   - List `<project>-root/5-work/`
   - Read active work item's `00-OVERVIEW.md` if exists
6. **Reference this system:** Read `ai-workflow/CORE.md` for protocols

### Standalone Mode

1. **Detect mode** (you're here if parent lacks project-hub structure)
2. **Check for active work:**
   - List `ai-workflow/work/`
   - Read active work item's `00-OVERVIEW.md` if exists
3. **Follow standard session start** from `CORE.md`

---

## Folder Structure Comparison

### Project-Hub Mode
```
project-hub/
├── coordination/           ← Hub-level orchestration
├── ai-workflow/            ← Shared workflow system (YOU ARE HERE)
│   ├── CORE.md
│   ├── MODE.md             ← This file
│   └── feedback/           ← Workflow feedback goes here
└── projects/
    └── <group>/
        └── <project>-root/
            ├── AI-AGENT-ORIENTATION.md  ← Agent entry point (read first)
            ├── CONTEXT.md               ← Project identity & setup
            ├── STATUS.md                ← Current progress (living doc)
            ├── CHANGELOG.md             ← Milestones & releases
            ├── 1-concepts/
            ├── 2-knowledge/
            ├── 3-inbox/
            ├── 4-workplans/
            ├── 5-work/                  ← Work items go here
            └── 6-instances/
```

### Standalone Mode
```
<project>/
├── ai-workflow/            ← Embedded workflow system (YOU ARE HERE)
│   ├── CORE.md
│   ├── MODE.md             ← This file
│   ├── feedback/           ← Workflow feedback
│   ├── work/               ← Work items go here
│   ├── knowledge/
│   ├── concepts/
│   ├── workplans/
│   └── inbox/
└── <project-source>/       ← Actual project code
```

---

## Commands Work the Same

All `>>commands` work identically in both modes. The only difference is **where outputs are written**.

| Command | Project-Hub Output | Standalone Output |
|---------|-------------------|-------------------|
| `>>start feat X` | `<project>-root/5-work/NNN-feat-X/` | `ai-workflow/work/NNN-feat-X/` |
| `>>init-knowledge` | `<project>-root/2-knowledge/` | `ai-workflow/knowledge/` |
| `>>finalize` | `<project>-root/1-concepts/` or `4-workplans/` | `ai-workflow/concepts/` or `workplans/` |
| `>>feedback` | `ai-workflow/feedback/` | `ai-workflow/feedback/` |

---

## Variable Reference

When reading protocols, substitute these variables based on mode:

| Variable | Project-Hub Mode | Standalone Mode |
|----------|------------------|-----------------|
| `{WORK_ROOT}` | `<project>-root/5-work/` | `ai-workflow/work/` |
| `{KNOWLEDGE_ROOT}` | `<project>-root/2-knowledge/` | `ai-workflow/knowledge/` |
| `{CONCEPTS_ROOT}` | `<project>-root/1-concepts/` | `ai-workflow/concepts/` |
| `{WORKPLANS_ROOT}` | `<project>-root/4-workplans/` | `ai-workflow/workplans/` |
| `{INBOX_ROOT}` | `<project>-root/3-inbox/` | `ai-workflow/inbox/` |
| `{FEEDBACK_ROOT}` | `ai-workflow/feedback/` | `ai-workflow/feedback/` |

---

## Switching Between Projects (Project-Hub Mode Only)

When working in project-hub mode, you may switch between projects:

1. **Confirm with user** before switching project context
2. **Read new project's `AI-AGENT-ORIENTATION.md`** (entry point)
3. **Read `CONTEXT.md`** and **check `STATUS.md`**
4. **Check for active work** in the new project's `5-work/`
5. **Update your mental model** of paths accordingly

---

## Summary

1. **Detect mode** at session start by checking parent folder structure
2. **Resolve paths** based on mode (project folders vs ai-workflow folders)
3. **Commands work the same** - only output locations differ
4. **Feedback always goes to ai-workflow** regardless of mode
