# Open Tasks & Deferred Decisions

Tasks and design questions for the ai-workflow system that need further thinking.

---

## Open Questions

### CHANGELOG.md Integration (2026-01-14)

**Context:** Project-hub now has `CHANGELOG.md` in each project-root for tracking milestones & releases.

**Question:** How should ai-workflow protocols interact with CHANGELOG.md?

**Options considered:**
1. Add to `>>archive` protocol with prompt: "Is this milestone-worthy for CHANGELOG?"
2. New `>>release` or `>>milestone` command
3. Document as human-managed (agent suggests entries but doesn't write)
4. Automatic detection of "release-worthy" work items

**Considerations:**
- CHANGELOG is more formal than STATUS.md
- Not every completed work item is changelog-worthy
- Releases often bundle multiple work items
- Human judgment likely needed for what constitutes a "milestone"

**Status:** Deferred - needs more thinking

---

## Completed Tasks

(Move items here when resolved)

---

## Archive

(Old phase docs in this folder are from earlier development iterations - kept for reference)
