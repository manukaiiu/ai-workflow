# Design Decisions

Key decisions made in the design of ai-workflow and their rationale.

## Documentation-Only Approach

**Decision**: No runtime code, purely markdown documentation.

**Rationale**:
- Works with any AI agent/model without integration
- No dependencies to install or maintain
- Easy to modify and customize
- Version-controlled like code
- Readable by humans for review

**Trade-offs**:
- No automatic enforcement of rules
- Relies on agent following instructions
- Can't prevent anti-patterns programmatically

---

## Hierarchical Loading

**Decision**: CORE.md is always loaded; protocols loaded on-demand.

**Rationale**:
- Reduces context usage from ~1700 lines to ~300 per session
- Keeps essential mental model always available
- Loads detail only when needed
- Preserves context for actual work

**Trade-offs**:
- More file reads during session
- Agent must remember to read protocols
- Initial learning curve

---

## SSOT in 00-OVERVIEW.md

**Decision**: Single source of truth for each work item.

**Rationale**:
- One place to look for current state
- Prevents conflicting information
- Fast session resume
- Clear ownership of status

**Trade-offs**:
- Must keep OVERVIEW updated
- Can become stale if not maintained
- Adds overhead on every state change

---

## Append-Only Progress Logs

**Decision**: 03-PROGRESS-LOG.md grows, never shrinks.

**Rationale**:
- Preserves complete history
- Enables debugging past sessions
- Prevents accidental information loss
- Shows progression over time

**Trade-offs**:
- Files grow indefinitely
- May need periodic archival
- Searching old logs can be slow

---

## Dual-Mode Operation

**Decision**: Support both project-hub (shared) and standalone (embedded) modes.

**Rationale**:
- Scales from single project to multi-project organization
- Shared system ensures consistency across projects
- Standalone mode for simplicity when starting
- Same methodology works in both

**Trade-offs**:
- Mode detection adds complexity
- Must handle path resolution carefully
- Two mental models to maintain

---

## `>>` Command Prefix

**Decision**: Use `>>` to trigger protocols.

**Rationale**:
- Clear visual signal
- Unlikely to occur naturally
- Easy to type
- Easy to search/grep
- Distinguishes from other text

**Trade-offs**:
- Non-standard syntax
- Agents must learn convention
- Could conflict with quote/reply conventions

---

## Numbered Work Item Folders

**Decision**: Use `NNN-TYPE-name` pattern.

**Rationale**:
- Sequential numbers show order
- Type prefix enables filtering
- Name provides context
- Unique across all types

**Trade-offs**:
- Must scan all folders for next number
- Numbers can get high over time
- Deleted items leave gaps

---

## Max 7 Sub-Concepts

**Decision**: Limit concept work to 7 sub-concepts.

**Rationale**:
- Based on cognitive load research (Miller's Law)
- Forces meaningful grouping
- Prevents scope creep
- Encourages splitting large concepts

**Trade-offs**:
- Arbitrary limit may frustrate
- Requires work to consolidate
- May need multiple concept items

---

## Natural Language Mapping

**Decision**: Map common phrases to commands.

**Rationale**:
- Humans don't need to remember exact syntax
- Feels more natural
- Reduces friction
- Still supports exact commands

**Trade-offs**:
- Ambiguity in some phrases
- Agents must maintain mapping
- Could miss intended command

---

## Feedback as Exception to Read-Only

**Decision**: In project-hub mode, `feedback/` is writable.

**Rationale**:
- Enables workflow improvements from any project
- Single collection point for suggestions
- Agents can contribute learnings
- Humans can review all feedback centrally

**Trade-offs**:
- Exception to read-only rule
- Must communicate clearly
- Potential for clutter

---

## Templates Per Work Type

**Decision**: Separate templates for feat/maint/bug/concept.

**Rationale**:
- Each type has different needs
- Features need requirements; maintenance needs scope
- Keeps templates focused
- Enables type-specific protocols

**Trade-offs**:
- More templates to maintain
- Some duplication across types
- Must remember which to use

---

## Knowledge Checkpoint at Wrap

**Decision**: Update knowledge docs at every `>>wrap`.

**Rationale**:
- Ensures discoveries are captured
- Prevents knowledge loss
- Builds up knowledge base over time
- Natural pause point for reflection

**Trade-offs**:
- Adds overhead to session end
- May feel repetitive if nothing new
- Agents might skip it

---

## Extraction IDs (T, R, C, S, D, A)

**Decision**: Standard prefixes for concept extraction.

**Rationale**:
- Enables traceability in concepts
- Clear categorization
- Easy to reference (T1, R2...)
- Consistent across all concepts

**Trade-offs**:
- Learning curve for prefixes
- May not fit all domains
- Rigid categorization
