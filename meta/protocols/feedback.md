# Protocol: >>feedback

Record feedback about the workflow system itself (not the project you're working on).

## When to Use

- Human has an observation about the workflow system
- Human suggests an improvement to how agent-human collaboration works
- Agent notices a pattern worth capturing
- After implementing a workflow change, to document the reasoning

## Steps

### 1. Ensure meta-feedback folder exists

```
ai-agent/meta/meta-feedback/
├── FEEDBACK-INDEX.md
└── FB-NNN-*.md files
```

If folder doesn't exist, create it and copy the index template:
- Create folder: `ai-agent/meta/meta-feedback/`
- Copy template: `meta/templates/FEEDBACK-INDEX.md` → `meta/meta-feedback/FEEDBACK-INDEX.md`

### 2. Determine next feedback ID

Read `meta/meta-feedback/FEEDBACK-INDEX.md` and find the highest existing FB-NNN number.
Next ID = highest + 1 (or FB-001 if none exist).

### 3. Ask about feedback type

**Ask human:**
> "Quick freeform note, or structured feedback with context?"

- **Quick**: Create minimal file with just the observation
- **Structured**: Use template from `meta/templates/FEEDBACK.md`

### 4. Gather feedback content

**For quick feedback**, ask:
> "What's the feedback? (I'll capture it as-is)"

**For structured feedback**, gather:
- What was observed?
- Where/when did it happen? (project, work item, situation)
- What's the impact? (efficiency, quality, clarity, safety)
- What improvement is suggested?

### 5. Create feedback file

Create `meta/meta-feedback/FB-NNN-short-slug.md`

**Quick format:**
```markdown
# FB-NNN: [Short title]

> **Status**: Open
> **Source**: human
> **Date**: YYYY-MM-DD

[Freeform feedback content here]
```

**Structured format:** Use full template from `meta/templates/FEEDBACK.md`

### 6. Update the index

Add entry to `meta/meta-feedback/FEEDBACK-INDEX.md` in the **Open** section:

```markdown
| FB-NNN | [Summary] | [human/agent/collaborative] | [date] |
```

### 7. Confirm

Tell human:
> "Recorded as FB-NNN. You can find it in meta/meta-feedback/"

## Notes

- This is for **workflow system** feedback, not project/feature feedback
- Feedback can come from human, agent, or collaborative observation
- Keep summaries concise in the index (< 60 chars)
- Status flow: Open → In Progress → Implemented/Declined
