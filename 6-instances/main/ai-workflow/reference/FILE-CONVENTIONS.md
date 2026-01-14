# File Conventions

Rules for file organization, naming, and management in the workflow system.

---

## Folder Structure

```
ai-workflow/
├── CORE.md                         ← Read every session
├── protocols/                      ← Protocol files (read on-demand)
├── reference/                      ← Reference docs (consult as needed)
├── templates/                      ← Document templates
├── feedback/                       ← Workflow system feedback
├── work/                           ← Active work items
│   ├── 001-feat-name/
│   ├── 002-maint-name/
│   └── archive/                   ← Archived work items
├── concepts/                       ← Finalized concepts
│   └── [name]/v1/
├── workplans/                      ← Finalized work plans
│   └── [name]/v1/
└── knowledge/                      ← Project knowledge base
    ├── SYSTEM-OVERVIEW.md
    ├── REPOSITORY-MAP.md
    ├── CONCEPTS-INDEX.md
    ├── COMMANDS.md
    └── subsystems/
```

---

## Work Item Folder Naming

**Pattern**: `NNN-TYPE-name` or `NNN-TYPE-[scope]-name`

| Component | Rule | Example |
|-----------|------|---------|
| NNN | 3-digit sequential number | `001`, `002`, `047` |
| TYPE | Work type prefix | `feat`, `bug`, `maint`, `concept` |
| [scope] | Optional work package scope | `[wp1]`, `[root]` |
| name | Kebab-case description | `user-auth`, `deps-update` |

**Standard Examples**:
- `001-feat-user-authentication`
- `002-maint-dependency-updates`
- `003-bug-login-timeout`
- `004-concept-new-platform`

**Scoped Examples** (when using work packages):
- `001-feat-[wp1]-data-pipeline`
- `002-maint-[wp2]-model-update`
- `003-feat-[root]-project-governance`

**Numbering Rule**: Find highest number across ALL folders in `work/`, add 1.

**Scope Rule**: Scope prefix is optional. When omitted, work item belongs to `_root` implicitly. See `templates/WORKPACKAGES.md` for work package setup.

---

## Document Numbering

### Template Files (00-09) - Reserved

| Number | Document | Work Types |
|--------|----------|------------|
| 00 | OVERVIEW.md | All |
| 01 | REQUIREMENTS.md / SCOPE.md / INPUTS/ | All |
| 02 | IMPLEMENTATION-PLAN.md / EXTRACTIONS.md | All |
| 03 | PROGRESS-LOG.md / CONCEPT.md | All |
| 04 | TESTING-CHECKLIST.md / WORKPLAN.md | All |
| 05 | ROADMAP.md / ANALYSIS.md | Optional |
| 06 | PR-MESSAGE.md / PROGRESS-LOG.md | Optional |
| 07 | REFINEMENT-LOG.md | Concept |
| 08 | OPEN-QUESTIONS.md | Concept |
| 09 | (Reserved) | - |

### Input Files (01-INPUTS/)

`01-INPUTS/` - Optional folder for work-item-specific input files
- Use for sources specific to THIS work item (not project-wide)
- Contains an INDEX.md listing all inputs (required for concept work)
- Examples: meeting notes, requirement docs, screenshots, reference materials

**When to use**:
- Work item has unique source materials
- Need to track processing status of inputs
- Want to keep work item self-contained

**Project-wide vs work-item inputs**:
- Project-wide: Reference from `knowledge/` or project folders
- Work-item-specific: Copy/place in `01-INPUTS/`

### Output Files (90-OUTPUTS/)

`90-OUTPUTS/` - Standard folder for deliverables
- Use descriptive names (no numbers)
- Examples: `template-auth-flow.md`, `api-design.md`
- Work-item-specific outputs that may be referenced elsewhere

---

## Document Max Lengths

| Document | Max | Action if Exceeded |
|----------|-----|-------------------|
| 00-OVERVIEW.md | 2 pages | Refactor, archive old decisions |
| 01-REQUIREMENTS.md | 3 pages | Split feature or remove detail |
| 01-SCOPE.md | 2 pages | Be more concise |
| 02-IMPLEMENTATION-PLAN.md | 4 pages | Break phases into sub-features |
| 03-PROGRESS-LOG.md | Unlimited | Archive old entries |
| 04-TESTING-CHECKLIST.md | 2 pages | Remove duplicate scenarios |
| 05-ANALYSIS.md | 3 pages | Move insights to knowledge |
| 06-PR-MESSAGE.md | 1 page | Keep summary concise |

---

## Append-Only Rule

`03-PROGRESS-LOG.md` (and `06-PROGRESS-LOG.md` for concepts):
- ✅ Add new entries at the end
- ❌ Never modify old entries (except typos)
- ❌ Never create separate session files
- ❌ Never duplicate info already logged

---

## File Index in OVERVIEW

Maintain a file index in `00-OVERVIEW.md`:

```markdown
## File Index

| File | Type | Purpose |
|------|------|---------|
| 00-OVERVIEW.md | Core | Status and navigation |
| 01-REQUIREMENTS.md | Core | Requirements |
| 02-IMPLEMENTATION-PLAN.md | Core | Implementation phases |
| 03-PROGRESS-LOG.md | Core | Session log |
| 90-OUTPUTS/ | Outputs | Deliverables |
```

Update when creating/deleting files.

---

## Knowledge Files

```
knowledge/
├── SYSTEM-OVERVIEW.md      ← High-level project info
├── REPOSITORY-MAP.md       ← Repository structure
├── CONCEPTS-INDEX.md       ← Patterns, APIs, models
├── COMMANDS.md             ← Project commands
└── subsystems/
    ├── auth.md             ← Subsystem documentation
    ├── database.md
    └── api.md
```

**Subsystem naming**: Use kebab-case, descriptive names.

---

## Concept Output Folders

After `>>finalize`:

```
concepts/[name]/v1/
├── CONCEPT.md
├── CONCEPT-[sub].md
└── INPUTS-SUMMARY.md

workplans/[name]/v1/
├── WORKPLAN.md
├── ROADMAP.md
└── ROADMAP.mermaid.md
```

**Version folders**: `v1`, `v2`, etc.

---

## Work Packages (Optional)

For large projects with semi-independent components, you can organize by work package.

**Setup**: Create `WORKPACKAGES.md` at project-root level. See `templates/WORKPACKAGES.md`.

**Scoped Folder Structure**:
```
project-root/
├── WORKPACKAGES.md
├── 1-concepts/
│   ├── _root/              ← Project-wide concepts
│   ├── wp1-data/           ← WP1-specific concepts
│   └── wp2-models/         ← WP2-specific concepts
├── 2-knowledge/
│   ├── _root/
│   ├── wp1-data/
│   └── wp2-models/
└── 5-work/
    ├── 001-feat-[wp1]-pipeline/
    ├── 002-feat-[wp2]-training/
    └── 003-maint-[root]-governance/
```

**Key Points**:
- `_root/` folder is always present (project-wide scope)
- Work items use `[scope]` prefix in name
- Unscoped items belong to `_root` implicitly
- Most projects don't need this - only use for large multi-component projects

---

## Anti-Patterns

❌ Creating multiple status documents
❌ Documents without numbers in 00-09 range
❌ Skipping numbers in work item sequence
❌ Mixing work types in names (e.g., `feat-bug-fix`)
❌ Files in wrong locations
❌ Duplicate information across files
❌ Exceeding max document lengths
