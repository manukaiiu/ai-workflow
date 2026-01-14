# Concept: ai-workflow System

## What It Is

**ai-workflow** is a structured meta-documentation system for human-AI collaboration on software projects. It provides a methodology that enables AI agents to work effectively across sessions with minimal context loss.

## Core Problem Solved

AI agents lose context between sessions (context windows, crashes, handovers). This system ensures:
- **Continuity**: Work can resume in under 2 minutes
- **Consistency**: Same methodology regardless of agent or session
- **Traceability**: All decisions and progress are documented

## Philosophy

### 1. Single Source of Truth (SSOT)
Each work item has ONE authoritative document (`00-OVERVIEW.md`) that tells agents:
- Current status
- What to do next
- What files to read

### 2. Append-Only Progress
Progress logs (`03-PROGRESS-LOG.md`) only grow - history is never rewritten. This creates an audit trail and prevents information loss.

### 3. Hierarchical Loading
Minimize context usage through on-demand loading:
- **Always load**: CORE.md (~250 lines) - navigation hub
- **On-demand**: protocols/ - when executing commands
- **As-needed**: reference/ - for conventions and glossary

### 4. Self-Sufficient Work Items
Each work item contains everything needed to resume:
- Current state
- Next actions
- Relevant context
- Resume instructions if paused

### 5. Commands Trigger Protocols
Simple `>>commands` expand to full procedures:
- `>>start feat X` → creates work item, asks questions, makes plan
- `>>continue` → reads SSOT, summarizes state, confirms direction
- `>>wrap` → updates logs, sets next task, captures knowledge

## Core Abstractions

### Work Types
| Type | Prefix | Purpose |
|------|--------|---------|
| Feature | `feat` | New functionality |
| Bug | `bug` | Defect fixes |
| Maintenance | `maint` | Updates, refactoring, security |
| Concept | `concept` | Complex planning with workplans/roadmaps |

### Work Item Structure
```
NNN-TYPE-name/
├── 00-OVERVIEW.md          ← SSOT (always read first)
├── 01-REQUIREMENTS.md      ← What to build
├── 02-IMPLEMENTATION-PLAN.md ← How to build
├── 03-PROGRESS-LOG.md      ← Session history (append-only)
├── 04-TESTING-CHECKLIST.md ← Test scenarios
└── 90-OUTPUTS/             ← Deliverables
```

### Document Numbering
- **00-09**: Core template documents
- **10-89**: Work-item specific documents
- **90-99**: Outputs and deliverables

### Knowledge System
Project knowledge accumulates in `{KNOWLEDGE_ROOT}/`:
- `SYSTEM-OVERVIEW.md` - Project basics
- `REPOSITORY-MAP.md` - Directory structure
- `CONCEPTS-INDEX.md` - Patterns, APIs, models
- `COMMANDS.md` - Useful commands
- `subsystems/` - Deep subsystem documentation

## Dual-Mode Operation

The system works in two deployment modes:

### Project-Hub Mode
- ai-workflow is **shared and read-only** across projects
- Work outputs go to **project's folders** (5-work/, 2-knowledge/, etc.)
- Exception: `feedback/` is writable for workflow improvement suggestions

### Standalone Mode
- ai-workflow is **embedded** in a single project
- Work outputs go to **ai-workflow's folders** (work/, knowledge/, etc.)
- Full read-write access to all folders

### Path Variables
Both modes use the same protocols; only output paths differ:
- `{WORK_ROOT}` → where work items live
- `{KNOWLEDGE_ROOT}` → where project knowledge lives
- `{CONCEPTS_ROOT}` → finalized concepts
- `{WORKPLANS_ROOT}` → finalized workplans

## Concept Workflow (Special)

For complex planning work that produces workplans and roadmaps:

```
GATHER → EXTRACT → CONCEPTUALIZE → PLAN → ROADMAP → FINALIZE
```

Each phase has dedicated protocols and produces specific artifacts:
- **Gather**: Collect inputs (documents, conversations, URLs)
- **Extract**: Process into structured data with IDs (T1, R2, C3...)
- **Conceptualize**: Build concept document with max 7 sub-concepts
- **Plan**: Generate work breakdown (generic, Jira, GitHub formats)
- **Roadmap**: Create dependency map with Mermaid visualizations
- **Finalize**: Promote to `concepts/` and `workplans/` folders

## Design Decisions

### Why `>>` Commands?
- Clear signal that triggers a protocol
- Easy to type and recognize
- Distinguishes workflow commands from natural language

### Why Numbered Folders?
- Sequential ordering shows history
- Unique IDs prevent collision
- Easy to reference (001, 002...)

### Why Separate Templates by Work Type?
- Features need requirements; maintenance needs scope
- Different workflows have different needs
- Keeps templates focused and minimal

### Why Max 7 Sub-Concepts?
- Cognitive limit for comprehension
- Forces meaningful grouping
- Encourages splitting large concepts

### Why Append-Only Progress Logs?
- Preserves history for debugging
- Enables session-by-session review
- Prevents accidental information loss

## Success Metrics

The system works when:
- ✅ `>>continue` gets agents working in < 2 minutes
- ✅ Agents read ~300 lines per session (not 1700+)
- ✅ Work items are numbered: `NNN-TYPE-name`
- ✅ Progress logs show clear progression
- ✅ Knowledge docs stay updated
- ✅ Human can resume with any agent
