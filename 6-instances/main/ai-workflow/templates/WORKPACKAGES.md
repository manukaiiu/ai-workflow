# Work Packages

Optional file for organizing large projects with semi-independent components.

> **When to use**: Only create this file if your project has distinct sub-projects or work packages that benefit from separate organization. Most projects don't need this.

---

## Work Package Definitions

### WP1: [Name]
- **Lead:** [name or role]
- **Scope:** [brief description of what this WP covers]
- **Status:** [Active / Planning / Complete]

### WP2: [Name]
- **Lead:** [name or role]
- **Scope:** [brief description]
- **Status:** [Active / Planning / Complete]

### _root
- **Scope:** Project-wide concerns, cross-cutting items, governance
- **Status:** Always present (implicit)

---

## Folder Structure

When this file exists, numbered folders support optional scoping:

```
project-root/
├── WORKPACKAGES.md          ← This file
├── 1-concepts/
│   ├── _root/               ← Project-wide concepts
│   │   └── governance/
│   ├── wp1-[name]/          ← WP1 concepts
│   └── wp2-[name]/          ← WP2 concepts
├── 2-knowledge/
│   ├── _root/
│   │   └── architecture.md  ← Overall architecture
│   ├── wp1-[name]/
│   └── wp2-[name]/
├── 5-work/
│   ├── 001-feat-[wp1]-setup-pipeline/
│   ├── 002-feat-[wp2]-train-model/
│   └── 003-maint-[root]-quarterly-review/
└── 6-instances/
    ├── wp1-dev/
    └── wp2-dev/
```

---

## Work Item Naming

With work packages, work items use optional scope prefix:

| Pattern | Example | Scope |
|---------|---------|-------|
| `NNN-TYPE-[scope]-name` | `001-feat-[wp1]-data-pipeline` | WP1 |
| `NNN-TYPE-[root]-name` | `002-maint-[root]-governance` | Project-wide |
| `NNN-TYPE-name` | `003-bug-fix-typo` | Implicit _root |

---

## Guidelines

1. **Optional** - Only use if your project genuinely has semi-independent components
2. **_root is always present** - Even without explicit folder, unscoped items belong to root
3. **Flat within scope** - Don't nest further below work package level
4. **Consistent naming** - Use same WP identifier across all numbered folders
5. **STATUS.md** - Keep single file with per-WP sections if needed

---

## Example: Research Project

```markdown
# Work Packages

## WP1: Data Platform
- **Lead:** Data Team
- **Scope:** Data ingestion, storage, ETL pipelines, APIs
- **Status:** Active

## WP2: AI Models
- **Lead:** ML Team
- **Scope:** Model training, evaluation, inference services
- **Status:** Active

## WP3: User Interface
- **Lead:** Frontend Team
- **Scope:** Dashboard, visualization, user management
- **Status:** Planning

## _root
- **Scope:** Project management, architecture decisions, cross-WP coordination
- **Status:** Always present
```
