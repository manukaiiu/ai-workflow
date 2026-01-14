# Output Location Guidelines

When and where to create/edit files during work.

---

## Deployment Modes

First, understand which deployment mode you're in. See [../MODE.md](../MODE.md) for detection.

| Mode | ai-workflow is... | Outputs go to... |
|------|-------------------|------------------|
| **Project-Hub** | Shared, read-only | Project's folders |
| **Standalone** | Embedded, read-write | ai-workflow's folders |

### Path Variables

Use these variables in your mental model (resolve based on mode):

| Variable | Project-Hub | Standalone |
|----------|-------------|------------|
| `{WORK_ROOT}` | `<project>-root/5-work/` | `ai-workflow/work/` |
| `{KNOWLEDGE_ROOT}` | `<project>-root/2-knowledge/` | `ai-workflow/knowledge/` |
| `{CONCEPTS_ROOT}` | `<project>-root/1-concepts/` | `ai-workflow/concepts/` |
| `{WORKPLANS_ROOT}` | `<project>-root/4-workplans/` | `ai-workflow/workplans/` |
| `{INBOX_ROOT}` | `<project>-root/3-inbox/` | `ai-workflow/inbox/` |

---

## The Two Work Modes

### 1. Work Item Mode (Default)

When a work item exists in `{WORK_ROOT}/NNN-TYPE-name/`:
- All work happens within that folder
- Outputs go to `90-OUTPUTS/` subfolder
- Finalization promotes to top-level folders
- Progress tracked in work item docs

**This is the preferred mode** - it provides:
- Traceability
- Version control
- Clear workflow stages
- Easy rollback

### 2. Direct Edit Mode (Exception)

When user explicitly requests edits to files outside work items:
- User specifies exact location
- Agent confirms before proceeding
- No work item tracking

**Use sparingly** - appropriate for:
- Quick fixes to existing files
- Updates unrelated to any work item
- Explicit user override

---

## Decision Tree

```
User requests file creation/edit
          │
          ▼
┌─────────────────────────┐
│ Is there an active      │
│ work item for this?     │
└─────────────────────────┘
          │
    ┌─────┴─────┐
    │           │
   YES          NO
    │           │
    ▼           ▼
┌─────────┐  ┌─────────────────┐
│ Work in │  │ Ask user:       │
│ work/   │  │ - Create work   │
│ folder  │  │   item? (>>start)│
└─────────┘  │ - Or direct     │
             │   edit? (confirm │
             │   location)      │
             └─────────────────┘
```

---

## Location Matrix

| File Type | During Work | After Finalize | Direct Edit OK? |
|-----------|-------------|----------------|-----------------|
| Concept drafts | `{WORK_ROOT}/NNN/03-CONCEPT*.md` | `{CONCEPTS_ROOT}/name/vN/` | Ask first |
| Work plans | `{WORK_ROOT}/NNN/04-WORKPLAN.md` | `{WORKPLANS_ROOT}/name/vN/` | Ask first |
| Roadmaps | `{WORK_ROOT}/NNN/05-ROADMAP*.md` | `{WORKPLANS_ROOT}/name/vN/` | Ask first |
| Deliverables | `{WORK_ROOT}/NNN/90-OUTPUTS/` | User decides | Yes, with confirmation |
| Knowledge docs | `{KNOWLEDGE_ROOT}/` | N/A | Yes |
| Project code | Project folders | N/A | Yes, per requirements |
| Workflow feedback | `ai-workflow/feedback/` | N/A | Yes (both modes) |

---

## Protecting Finalized Outputs

Files in `{CONCEPTS_ROOT}` and `{WORKPLANS_ROOT}` are **finalized artifacts**.

When user requests changes to finalized files:

1. **Ask clarifying questions**:
   ```
   This file is in {CONCEPTS_ROOT}/[name]/v1/ (finalized output).

   Options:
   1. Edit in place (modifies finalized version)
   2. Create new version (>>new-version)
   3. Create new work item to iterate

   Which approach?
   ```

2. **If editing in place**: Confirm user understands this modifies the "official" version

3. **For significant changes**: Recommend `>>new-version` to preserve history

---

## Red Flags to Watch For

**Pause and confirm** when:

- Creating files outside `{WORK_ROOT}` or `{KNOWLEDGE_ROOT}` without explicit path
- User says "update the concept" but there's an active work item
- Request implies bypassing finalization workflow
- Editing finalized outputs without clear intent
- **Project-Hub mode**: Writing to ai-workflow/ (except meta-feedback/)

**Example confirmations**:

```
"You mentioned updating the roadmap. Should I:
1. Edit the draft in {WORK_ROOT}/003-concept-platform/05-ROADMAP.md
2. Edit the finalized version in {WORKPLANS_ROOT}/platform/v1/ROADMAP.md
3. Create a new version (v2)?"
```

```
"I'll create this deliverable in {WORK_ROOT}/003-concept-platform/90-OUTPUTS/.
Is that the right location, or did you want it somewhere else?"
```

---

## Work Packages (Optional Scoping)

When a project has `WORKPACKAGES.md`, numbered folders support optional scoping.

### Scoped Paths

Within scoped projects, paths may include work package prefixes:

| Standard Path | Scoped Equivalent |
|---------------|-------------------|
| `{CONCEPTS_ROOT}/name/` | `{CONCEPTS_ROOT}/wp1-name/` or `{CONCEPTS_ROOT}/_root/name/` |
| `{KNOWLEDGE_ROOT}/file.md` | `{KNOWLEDGE_ROOT}/wp1-data/file.md` or `{KNOWLEDGE_ROOT}/_root/file.md` |
| `{WORK_ROOT}/001-feat-name/` | `{WORK_ROOT}/001-feat-[wp1]-name/` |

### Detection

Check for `WORKPACKAGES.md` at project-root level:
- **Present**: Project uses work packages - respect scoping
- **Absent**: Standard (unscoped) project

### Work Item Scoping

Work items can include scope in their name:
- `001-feat-[wp1]-data-pipeline` → belongs to WP1
- `002-maint-[root]-governance` → belongs to project root
- `003-bug-fix-typo` → belongs to `_root` (implicit)

### Knowledge/Concepts Scoping

When creating scoped content:
- Place in appropriate subfolder: `{KNOWLEDGE_ROOT}/wp1-name/`
- `_root/` subfolder for project-wide content
- Unscoped files at root level belong to `_root` implicitly

---

## Summary

| Principle | Implementation |
|-----------|----------------|
| Detect mode first | Check for project-hub structure |
| Default to work items | Create outputs in `{WORK_ROOT}` folder |
| Controlled promotion | Use `>>finalize` to move to top-level |
| Protect finalized work | Ask before editing `{CONCEPTS_ROOT}` or `{WORKPLANS_ROOT}` |
| Confirm when uncertain | Ask about location for anything unusual |
| Track everything | Work items provide traceability |
| Feedback always writable | `ai-workflow/feedback/` in both modes |
| Check for work packages | If `WORKPACKAGES.md` exists, respect scoping |
