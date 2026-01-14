# Handover: ai-workflow Restructure

This document explains what happened and what you need to do to complete the transition.

---

## What Happened

The ai-workflow repository was transformed from a dual-purpose repo into a proper **project-root** structure within project-hub. This was done to separate development work from the distributed workflow system.

### Changes Made (by project-hub orchestrator agent)

1. **Moved the repository**
   - FROM: `project-hub/ai-workflow/`
   - TO: `project-hub/projects/system/ai-workflow-root/`

2. **Added project-root structure**
   - `AI-AGENT-ORIENTATION.md` - Your entry point (customized for ai-workflow dev)
   - `CONTEXT.md` - Project identity and current state
   - `STATUS.md` - Current progress tracking
   - `CHANGELOG.md` - Milestone tracking
   - `1-concepts/` through `5-work/` - Standard numbered folders

3. **Created placeholder installed version**
   - `project-hub/ai-workflow/README.md` - Temporary placeholder
   - Points to dev location until restructure completes

4. **Updated project-hub references**
   - All paths now expect `ai-workflow/CORE.md` (no meta/ wrapper)
   - Feedback path updated to `ai-workflow/feedback/` (no meta-meta/ wrapper)
   - Roadmap item 003 marked as superseded by 004

---

## What You Need to Do

### Phase 1: Flatten the meta/ Folder

Move the contents of `meta/` to the root level:

```bash
# From ai-workflow-root/
mv meta/CORE.md ./
mv meta/FOR-HUMANS.md ./
mv meta/MODE.md ./
mv meta/README.md ./  # Consider if still needed or merge with main README
mv meta/protocols ./
mv meta/reference ./
mv meta/templates ./
mv meta/archive ./    # Optional: move to 2-knowledge/ or keep at root
mv meta/meta-feedback ./  # Review: is this separate from meta-meta/feedback?
rmdir meta
```

### Phase 2: Relocate meta-meta/ Content

The `meta-meta/` folder contains development artifacts. Move them appropriately:

```bash
# feedback/ stays as feedback/ in repo root
mv meta-meta/feedback ./

# Development docs go to project-root folders
mv meta-meta/OPEN-TASKS.md 5-work/   # Or convert to work items
mv meta-meta/PHASE*.md 2-knowledge/  # Historical development docs

rmdir meta-meta
```

### Phase 3: Update Internal References

Check all markdown files for references to `meta/` paths and update them:

```bash
# Find files with meta/ references
grep -r "meta/" *.md protocols/ reference/ templates/
```

Update any found references:
- `meta/CORE.md` → `CORE.md`
- `meta/protocols/` → `protocols/`
- `meta-meta/feedback/` → `feedback/`
- etc.

### Phase 4: Create the Installed Version

Once the structure is flattened, copy to the installed location:

```bash
# From project-hub root
rm -rf ai-workflow
mkdir ai-workflow

# Copy workflow content (not development artifacts)
cp projects/system/ai-workflow-root/CORE.md ai-workflow/
cp projects/system/ai-workflow-root/FOR-HUMANS.md ai-workflow/
cp -r projects/system/ai-workflow-root/protocols ai-workflow/
cp -r projects/system/ai-workflow-root/reference ai-workflow/
cp -r projects/system/ai-workflow-root/templates ai-workflow/
cp -r projects/system/ai-workflow-root/feedback ai-workflow/

# Optional: include archive if relevant for users
# cp -r projects/system/ai-workflow-root/archive ai-workflow/
```

### Phase 5: Verify

After completing all phases:

- [ ] `ai-workflow-root/CORE.md` exists (no meta/ wrapper)
- [ ] `ai-workflow-root/feedback/` exists
- [ ] No `meta/` or `meta-meta/` folders remain
- [ ] `project-hub/ai-workflow/CORE.md` exists
- [ ] `project-hub/ai-workflow/feedback/` exists
- [ ] Internal references are updated
- [ ] Git status shows expected changes

### Phase 6: Commit and Update Status

```bash
# From ai-workflow-root
git add -A
git commit -m "Restructure: flatten meta/, convert to project-root structure

- Move meta/ contents to root level
- Move meta-meta/ development docs to project-root folders
- Add project-root structure (CONTEXT.md, STATUS.md, etc.)
- feedback/ stays in repo for installed version

Part of project-hub roadmap item 004."
```

Then update:
- `STATUS.md` - Mark restructure as complete
- `CHANGELOG.md` - Update the restructure entry

---

## Current Folder Structure

**Before your work:**
```
ai-workflow-root/
├── .git/
├── .claude/
├── README.md               <- Original repo README
├── meta/                   <- TO BE FLATTENED
│   ├── CORE.md
│   ├── FOR-HUMANS.md
│   ├── MODE.md
│   ├── README.md
│   ├── archive/
│   ├── meta-feedback/
│   ├── protocols/
│   ├── reference/
│   └── templates/
├── meta-meta/              <- TO BE RELOCATED
│   ├── feedback/
│   ├── OPEN-TASKS.md
│   └── PHASE*.md
│
│   (Added by orchestrator - keep these)
├── AI-AGENT-ORIENTATION.md
├── CONTEXT.md
├── STATUS.md
├── CHANGELOG.md
├── HANDOVER.md             <- This file
├── .gitignore
├── 1-concepts/
├── 2-knowledge/
├── 3-inbox/
├── 4-workplans/
└── 5-work/
```

**After your work:**
```
ai-workflow-root/
├── .git/
├── .claude/
│
│   (Workflow content - will be copied to installed version)
├── CORE.md                 <- Flattened from meta/
├── FOR-HUMANS.md
├── MODE.md
├── protocols/
├── reference/
├── templates/
├── feedback/               <- From meta-meta/, stays in repo
├── archive/                <- Optional at root
│
│   (Project-root structure - stays here only)
├── AI-AGENT-ORIENTATION.md
├── CONTEXT.md
├── STATUS.md
├── CHANGELOG.md
├── README.md               <- May need merging/updating
├── .gitignore
├── 1-concepts/
├── 2-knowledge/            <- Contains PHASE*.md and other dev docs
├── 3-inbox/
├── 4-workplans/
└── 5-work/                 <- Contains OPEN-TASKS.md or derived work items
```

---

## Key Principles

1. **feedback/ stays in the repo** - Project agents need to write there, so it must be in both dev and installed versions.

2. **No symlinks** - Use copy for Windows compatibility.

3. **Development artifacts in project-root** - Concepts, knowledge, work items for developing ai-workflow live in the numbered folders, NOT in the distributed workflow content.

4. **Repo content IS the distributable** - After flattening, the root-level workflow files (CORE.md, protocols/, etc.) are what gets copied to installed location.

5. **Project-root files DON'T get copied** - AI-AGENT-ORIENTATION.md, CONTEXT.md, STATUS.md, numbered folders stay in dev only.

---

## Questions?

If anything is unclear:
1. Check `CONTEXT.md` for project identity
2. Check `STATUS.md` for current state
3. Check `../../../_meta/roadmap/004-ai-workflow-restructure.md` for the original plan

---

*This handover was created by the project-hub orchestrator agent as part of roadmap item 004.*
