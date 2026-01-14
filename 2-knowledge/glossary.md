# ai-workflow Glossary

Quick reference for terms used in ai-workflow development.

## Core Terms

| Term | Definition |
|------|------------|
| **Artifact** | The ai-workflow system itself (in `6-instances/main/ai-workflow/`) |
| **Installed version** | The copy at `project-hub/ai-workflow/` that projects read |
| **Project-root** | The development folder (`ai-workflow-root/`) with numbered folders |
| **SSOT** | Single Source of Truth - one authoritative location for information |
| **Protocol** | A defined procedure triggered by `>>` commands |
| **Work item** | A tracked unit of work in a numbered folder |

## Work Types

| Type | Prefix | Use |
|------|--------|-----|
| Feature | `feat` | New functionality |
| Bug | `bug` | Defect fixes |
| Maintenance | `maint` | Updates, refactoring |
| Concept | `concept` | Complex planning |

## Document Numbers

| Range | Purpose |
|-------|---------|
| 00-09 | Core template documents |
| 10-89 | Work-item specific |
| 90-99 | Outputs/deliverables |

## Extraction IDs

| ID | Category |
|----|----------|
| T | Themes & Patterns |
| R | Requirements |
| C | Constraints |
| S | Stakeholders |
| D | Decisions |
| A | Ambiguities |

## Status Symbols

| Symbol | Meaning |
|--------|---------|
| `[ ]` | Pending |
| `[x]` | Complete |
| `[~]` | In progress |
| `[P]` | Paused |

## Path Variables

| Variable | Resolves to |
|----------|-------------|
| `{WORK_ROOT}` | Where work items live |
| `{KNOWLEDGE_ROOT}` | Project knowledge |
| `{CONCEPTS_ROOT}` | Finalized concepts |
| `{WORKPLANS_ROOT}` | Finalized workplans |
| `{INBOX_ROOT}` | Incoming items |

## Modes

| Mode | When | ai-workflow is |
|------|------|----------------|
| Project-Hub | parent has `coordination/` + `projects/` | Read-only (shared) |
| Standalone | parent lacks those | Read-write (embedded) |

## Concept Workflow Phases

| Phase | Command | Output |
|-------|---------|--------|
| Gathering | `>>start concept` | 01-INPUTS/INDEX.md |
| Extracting | `>>extract` | 02-EXTRACTIONS.md |
| Conceptualizing | `>>conceptualize` | 03-CONCEPT.md |
| Planning | `>>plan` | 04-WORKPLAN.md |
| Roadmapping | `>>roadmap` | 05-ROADMAP.md |
| Finalizing | `>>finalize` | concepts/, workplans/ |

## File Names

| File | Purpose |
|------|---------|
| CORE.md | Agent entry point, mental model |
| MODE.md | Dual-mode operation details |
| FOR-HUMANS.md | Human user guide |
| 00-OVERVIEW.md | Work item SSOT |
| 03-PROGRESS-LOG.md | Session history |
