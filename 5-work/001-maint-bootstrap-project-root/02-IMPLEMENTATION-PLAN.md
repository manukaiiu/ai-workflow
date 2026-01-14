# Implementation Plan: Bootstrap Project-Root Structure

## Phase 1: Artifact Analysis
**Goal**: Understand the ai-workflow system deeply by reading the artifact

### Tasks
- [ ] Read `6-instances/main/ai-workflow/CORE.md` thoroughly
- [ ] Read `6-instances/main/ai-workflow/MODE.md`
- [ ] Survey protocols/ folder structure and key protocols
- [ ] Survey reference/ documentation
- [ ] Survey templates/ to understand work item structures
- [ ] Document findings in scratch notes

### Output
- Mental model of the system
- Notes for concept extraction

---

## Phase 2: Concept Extraction
**Goal**: Create concept documentation in `1-concepts/`

### Tasks
- [ ] Create `1-concepts/ai-workflow-system/` folder
- [ ] Write `CONCEPT.md` - main concept document
- [ ] Consider sub-concepts if needed (protocols, knowledge system, etc.)

### Output
- `1-concepts/ai-workflow-system/CONCEPT.md`

---

## Phase 3: Knowledge Base Organization
**Goal**: Structure `2-knowledge/` properly

### Tasks
- [ ] Create `architecture.md` - system components and relationships
- [ ] Create `design-decisions.md` - rationale for key decisions
- [ ] Create `glossary.md` - terminology reference
- [ ] Review existing PHASE-*.md files - reorganize or archive
- [ ] Remove redundant/obsolete content

### Output
- Organized `2-knowledge/` folder

---

## Phase 4: Workplan Structure
**Goal**: Set up `4-workplans/` for future work tracking

### Tasks
- [ ] Create workplan index/structure
- [ ] Define categories (features, improvements, tech-debt, docs)
- [ ] Optionally create initial workplan from known improvements

### Output
- `4-workplans/` ready to receive items

---

## Phase 5: External File Collection
**Goal**: Integrate scattered .md files from user's disk

### Tasks
- [ ] User provides paths to .md files
- [ ] Read and triage each file
- [ ] Translate into: work items, workplan entries, or inbox items
- [ ] Archive or delete originals (user decision)

### Output
- Integrated backlog of improvements

---

## Dependencies

- Phase 2 depends on Phase 1
- Phase 3 can run in parallel with Phase 2
- Phase 4 can run in parallel with Phase 2/3
- Phase 5 requires user input (file locations)
