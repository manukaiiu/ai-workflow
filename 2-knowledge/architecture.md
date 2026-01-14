# ai-workflow Architecture

## System Overview

ai-workflow is a documentation-driven workflow system. It has no runtime code - it's purely markdown files that guide AI agent behavior.

## Component Hierarchy

```
ai-workflow/
├── CORE.md              ← Entry point, mental model, navigation
├── MODE.md              ← Dual-mode operation details
├── FOR-HUMANS.md        ← Human user guide
├── README.md            ← Overview and quick start
│
├── protocols/           ← Command implementations
│   ├── start.md         ← >>start protocol
│   ├── continue.md      ← >>continue protocol
│   ├── wrap.md          ← >>wrap protocol
│   ├── pause.md         ← >>pause protocol
│   ├── checkpoint.md    ← >>checkpoint protocol
│   ├── archive.md       ← >>archive protocol
│   ├── test.md          ← >>test protocol
│   ├── feedback.md      ← >>feedback protocol
│   ├── init-knowledge.md
│   ├── scan-repo.md
│   ├── recovery.md
│   └── concept/         ← Concept-specific protocols
│       ├── overview.md
│       ├── start-concept.md
│       ├── add-input.md
│       ├── extract.md
│       ├── conceptualize.md
│       ├── plan.md
│       ├── roadmap.md
│       ├── refine.md
│       ├── finalize.md
│       └── new-version.md
│
├── reference/           ← Supporting documentation
│   ├── GLOSSARY.md      ← Terms and abbreviations
│   ├── FILE-CONVENTIONS.md
│   ├── OUTPUT-LOCATIONS.md
│   ├── WORK-TYPES.md
│   ├── ANTI-PATTERNS.md
│   └── TICKET-TEMPLATES.md
│
├── templates/           ← Document templates
│   ├── features/        ← Feature work item templates
│   ├── maintenance/     ← Maintenance work item templates
│   ├── concept/         ← Concept work item templates
│   ├── knowledge/       ← Knowledge base templates
│   ├── WORK-INDEX.md
│   ├── FEEDBACK-INDEX.md
│   ├── FEEDBACK.md
│   └── INBOX.md
│
└── feedback/            ← Workflow improvement suggestions
    └── FEEDBACK-INDEX.md
```

## Information Flow

### Session Start
```
Agent starts
    ↓
Detect mode (Project-Hub or Standalone)
    ↓
Read CORE.md (builds mental model)
    ↓
[Project-Hub] Read project's AI-AGENT-ORIENTATION.md, CONTEXT.md
    ↓
Check for active work in {WORK_ROOT}
    ↓
If active work: Read 00-OVERVIEW.md (SSOT)
    ↓
Ready to work
```

### Command Execution
```
Human: >>command
    ↓
Agent: Read protocols/command.md
    ↓
Execute steps in protocol
    ↓
Update relevant documents
    ↓
Report to human
```

### Session End (>>wrap)
```
Agent: Read protocols/wrap.md
    ↓
Update 00-OVERVIEW.md status
    ↓
Append to 03-PROGRESS-LOG.md
    ↓
Set next task clearly
    ↓
Update knowledge if discoveries made
    ↓
Report completion to human
```

## Key Relationships

### CORE.md → Protocols
CORE.md acts as a navigation hub. It doesn't contain full protocol details - it links to them. This keeps CORE.md small and loadable every session.

### OVERVIEW.md → Everything Else
Within a work item, 00-OVERVIEW.md is the SSOT. It links to and summarizes other documents in the work item. Agents always start here.

### Templates → Work Items
When `>>start` creates a work item, it copies templates and customizes them. Templates provide structure; work items contain actual content.

### Knowledge ← Work
Knowledge docs are updated during work. When agents discover patterns, gotchas, or useful information, they update the knowledge base. This creates a learning loop.

## Dual-Mode Architecture

### Shared Component (Read-Only in Project-Hub)
```
ai-workflow/
├── CORE.md, MODE.md, FOR-HUMANS.md, README.md
├── protocols/
├── reference/
├── templates/
└── feedback/  ← Exception: writable for feedback
```

### Project-Specific (In Project-Hub Mode)
```
<project>-root/
├── 1-concepts/      ← {CONCEPTS_ROOT}
├── 2-knowledge/     ← {KNOWLEDGE_ROOT}
├── 3-inbox/         ← {INBOX_ROOT}
├── 4-workplans/     ← {WORKPLANS_ROOT}
├── 5-work/          ← {WORK_ROOT}
└── 6-instances/     ← Running environments
```

### Combined (In Standalone Mode)
```
ai-workflow/
├── [all shared components]
├── work/            ← {WORK_ROOT}
├── knowledge/       ← {KNOWLEDGE_ROOT}
├── concepts/        ← {CONCEPTS_ROOT}
├── workplans/       ← {WORKPLANS_ROOT}
└── inbox/           ← {INBOX_ROOT}
```

## Extension Points

### Adding New Work Types
1. Create templates in `templates/<type>/`
2. Update `protocols/start.md` to handle the type
3. Update `reference/WORK-TYPES.md`
4. Update CORE.md work types table

### Adding New Commands
1. Create `protocols/<command>.md`
2. Add to CORE.md commands table
3. Consider if natural language mapping needed
4. Update FOR-HUMANS.md

### Adding New Reference Docs
1. Create in `reference/`
2. Link from CORE.md "Need More Detail?" section
3. Keep focused on single topic
