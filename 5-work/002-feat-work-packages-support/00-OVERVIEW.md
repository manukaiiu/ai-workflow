# Work Item Overview: Work Packages Support

**Type**: Feature
**Status**: Complete
**Created**: 2026-01-14
**Backlog ID**: B001

## Quick Context

Add optional support for sub-projects / work packages within a project-root. This enables large projects with semi-independent components (like WP1, WP2, WP3 in research projects) to organize work without full recursive nesting.

## Source

Requirement from: `project-hub/_meta/roadmap/005-work-packages-support.md`

## Current Phase

Complete - All phases implemented and released.

## Key Design Elements

### WORKPACKAGES.md (new optional file)
Defines work packages with lead, scope, and status.

### Folder Structure Convention
When WORKPACKAGES.md exists:
- Numbered folders get optional scope prefixes (`wp1-`, `wp2-`, `_root/`)
- `_root/` always exists for top-level/shared items
- Work items use `[scope]` prefix: `001-[wp1]-setup-pipeline`

### Principles
1. **Optional** - Only create if needed
2. **_root always exists** - Top-level scope always available
3. **Prefix convention** - Clarity without enforcement
4. **Flat within scope** - No further nesting

## Design Decisions (Resolved)

1. **Root naming**: `_root/` - underscore sorts first, unambiguous
2. **Scope prefix**: Optional, use `[scope]` pattern (e.g., `[wp1]`, `[root]`)
3. **STATUS.md**: Single file with per-WP sections, split later if needed

## Tasks (from source)

- [ ] Create WORKPACKAGES.md template
- [ ] Update numbered folder READMEs to mention optional scoping
- [ ] Document in FOLDER-STRUCTURE.md (or ai-workflow equivalent)
- [ ] Add example in templates (commented out / optional)

## File Index

| File | Type | Purpose |
|------|------|---------|
| 00-OVERVIEW.md | Core | This file - status and navigation |
| 01-REQUIREMENTS.md | Core | Detailed requirements |
| 02-IMPLEMENTATION-PLAN.md | Core | Implementation approach |
| 03-PROGRESS-LOG.md | Core | Session log |

## Next Actions

Ready to archive with `>>archive`.
