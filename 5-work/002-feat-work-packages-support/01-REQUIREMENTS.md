# Requirements: Work Packages Support

## Problem Statement

Large projects (e.g., research projects with WP1, WP2, WP3) have semi-independent components that:
- Need their own concepts, knowledge, and work items
- Share overall project management and architecture
- Don't warrant separate project-roots (would be over-engineering)

Currently, ai-workflow has no convention for organizing work within a single project-root by sub-project/work-package.

## Requirements

### R1: Optional Work Packages Definition
- New optional file `WORKPACKAGES.md` at project-root level
- Defines work packages with: name, lead, scope, status
- When absent, project works as before (single scope)

### R2: Scoped Folder Organization
When WORKPACKAGES.md exists, numbered folders support optional scoping:
- `1-concepts/wp1-name/` - Concepts for WP1
- `2-knowledge/wp2-name/` - Knowledge for WP2
- `5-work/001-[wp1]-task-name/` - Work item with WP scope

### R3: Root Scope
- `_root/` (or chosen name) always exists for top-level items
- Used for: project-wide architecture, cross-cutting concerns, governance
- Not a "work package" but the container scope

### R4: Work Item Scoping
- Work items can optionally indicate scope: `001-[wp1]-task-name`
- Bracket prefix convention: `[scope]` after number-type prefix
- Unscoped items are implicitly `_root`

### R5: Backward Compatibility
- Projects without WORKPACKAGES.md unchanged
- Scoping is purely organizational (convention, not enforcement)
- Agents should handle both scoped and unscoped projects

## Non-Requirements

- No recursive nesting below work package level
- No tooling enforcement (documentation-only system)
- No required migration for existing projects

## Acceptance Criteria

- [ ] WORKPACKAGES.md template exists
- [ ] ai-workflow docs explain work package convention
- [ ] Agents can detect and work with scoped projects
- [ ] Existing projects continue to work unchanged

## Decisions (Resolved)

### D1: Root Scope Naming
**Decision**: `_root/`
- Underscore prefix sorts first in listings
- "root" is unambiguous as top-level

### D2: Work Item Scope Prefix
**Decision**: Optional, with explicit `[root]` for root-scoped items
- Work items CAN use scope prefix: `001-[wp1]-task-name`
- Root-scoped items use `[root]`: `001-[root]-project-governance`
- Unscoped items implicitly belong to `[root]`
- Pattern: `NNN-TYPE-[scope]-name` or `NNN-TYPE-name`

### D3: STATUS.md Handling
**Decision**: Single STATUS.md with per-WP sections
- Start with one file, split if it becomes too large/complex
- Sections for each work package when needed
- Keep overall project status at top
