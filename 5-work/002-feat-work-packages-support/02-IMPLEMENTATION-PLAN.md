# Implementation Plan: Work Packages Support

## Overview

Add optional work package scoping to ai-workflow. This is a documentation-only feature - no code, just templates and updated docs.

**Artifact location**: `6-instances/main/ai-workflow/`

---

## Phase 1: Template Creation
**Goal**: Create WORKPACKAGES.md template

### Tasks
- [ ] Create `templates/WORKPACKAGES.md` template
- [ ] Include: work package definition format, _root explanation, examples

### Output
- `6-instances/main/ai-workflow/templates/WORKPACKAGES.md`

---

## Phase 2: Reference Documentation
**Goal**: Document the work packages convention

### Tasks
- [ ] Update `reference/FILE-CONVENTIONS.md` - add scoped folder naming
- [ ] Update `reference/OUTPUT-LOCATIONS.md` - explain scoped paths
- [ ] Consider new `reference/WORK-PACKAGES.md` for detailed guidance

### Output
- Updated reference docs explaining the convention

---

## Phase 3: Core Documentation
**Goal**: Update CORE.md and MODE.md if needed

### Tasks
- [ ] Review CORE.md - does work packages need mention?
- [ ] Review MODE.md - path resolution with scopes
- [ ] Update folder structure diagrams if helpful

### Output
- Updated core docs (minimal changes expected)

---

## Phase 4: Protocol Updates
**Goal**: Update relevant protocols to handle scoped projects

### Tasks
- [ ] Update `protocols/start.md` - handle scoped work item creation
- [ ] Update `protocols/status.md` - handle per-WP status sections
- [ ] Review other protocols for scope awareness

### Output
- Protocols that work with both scoped and unscoped projects

---

## Phase 5: Release
**Goal**: Deploy to installed version

### Tasks
- [ ] Verify all changes in artifact (`6-instances/main/ai-workflow/`)
- [ ] Copy artifact to `project-hub/ai-workflow/`
- [ ] Update CHANGELOG.md

### Output
- Updated installed version

---

## File Changes Summary

| File | Change |
|------|--------|
| `templates/WORKPACKAGES.md` | NEW - template for work packages definition |
| `reference/FILE-CONVENTIONS.md` | UPDATE - scoped folder naming |
| `reference/OUTPUT-LOCATIONS.md` | UPDATE - scoped path resolution |
| `reference/WORK-PACKAGES.md` | NEW (optional) - detailed guide |
| `protocols/start.md` | UPDATE - scope prefix handling |
| `CORE.md` | REVIEW - minimal updates if any |

---

## Risks & Mitigations

| Risk | Mitigation |
|------|------------|
| Over-complicating simple projects | Keep it optional, docs emphasize "only if needed" |
| Breaking existing projects | Pure addition, no changes to existing behavior |
| Agents confused by scopes | Clear detection: WORKPACKAGES.md present = scoped project |

---

## Success Criteria

- [ ] Can create WORKPACKAGES.md in a project and organize by scope
- [ ] Agents detect scoped vs unscoped projects correctly
- [ ] Work items can use `[scope]` prefix
- [ ] Existing projects unchanged
- [ ] Documentation is clear and complete
