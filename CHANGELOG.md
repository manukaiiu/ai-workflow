<!-- template-version: 1.1.0 (customized for ai-workflow) -->

# Changelog: ai-workflow

Track significant milestones and changes to the ai-workflow system.

---

## [Restructure] - 2026-01-14 (Complete)

### Changed
- Moved from `project-hub/ai-workflow/` to `projects/system/ai-workflow-root/`
- Added project-root structure (CONTEXT.md, STATUS.md, numbered folders)
- Separated development environment from installed distribution
- Flattened `meta/` folder - workflow content now at root level
- Relocated `meta-meta/` content (feedback/ to root, dev docs to 2-knowledge/)
- Created installed copy at `project-hub/ai-workflow/`
- Updated all internal references (removed meta/ prefix from paths)

---

## [Initial] - 2024-12 (estimated)

### Added
- Core workflow methodology (CORE.md)
- Human-readable overview (FOR-HUMANS.md)
- Protocol definitions
- Reference documentation
- Workflow templates
- Feedback mechanism for project agents

---

*For detailed implementation history, see git log.*
