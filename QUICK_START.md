# Quick Start for AI Agents

<!-- For AI: Read this file when first encountering this project to get oriented quickly -->

This guide helps AI agents understand this project structure and know what to read first.

## Initial Context Load

When first encountering this project, load these files in order:

### 1. Read First (Core Understanding)
```
@.cursorrules              # Core universal rules for AI behavior
@.cursor/MANIFEST.md       # Complete project map (this is your index)
@.cursor/template.json     # Machine-readable project metadata
```

### 2. Determine Project State

Check `.cursor/template.json` to understand:
- Is this a fresh template or customized project?
- What's the project type/language? (or "to-be-set")
- What customization has been done?

**If template not yet customized:**
- Project is in initial state
- Offer to help set it up via `@PROMPTS.md`
- No src/ or language-specific files yet

**If template is customized:**
- Check for language indicators (package.json, requirements.txt, go.mod, etc.)
- Load relevant modular rules
- Understand project architecture from `@docs/ARCHITECTURE.md`

### 3. Load Relevant Context

Based on the task, load specific docs:

**For Setup/Customization:**
```
@PROMPTS.md                # Structured setup prompts
@docs/PROJECT_SETUP.md     # Detailed customization guide
```

**For Understanding Rules:**
```
@.cursor/rules/README.md   # How rules work
@.cursor/rules/QUICK_REFERENCE.md  # Rules summary
```

**For Using Cursor Effectively:**
```
@docs/cursor/index.md      # Cursor guide overview
```

**For Troubleshooting:**
```
@docs/TROUBLESHOOTING.md   # Common issues
```

## Decision Tree: What to Load

```
User asks about...
│
├─ "Setup/configure project"
│  └─ Load: @PROMPTS.md, @docs/PROJECT_SETUP.md
│
├─ "How do I use Cursor?"
│  └─ Load: @docs/cursor/index.md
│
├─ "Create/modify rules"
│  └─ Load: @.cursor/rules/README.md, @.cursor/rules/SCHEMA.md
│
├─ "Add workflow"
│  └─ Load: @docs/workflows/README.md
│
├─ "Create agent spec"
│  └─ Load: @docs/agents/README.md
│
├─ "Something not working"
│  └─ Load: @docs/TROUBLESHOOTING.md
│
├─ "What exists in this project?"
│  └─ Load: @.cursor/MANIFEST.md (you should already have this!)
│
└─ "Write code/tests/docs"
   └─ Load relevant: @.cursor/rules/documentation.md,
                    @.cursor/rules/testing.md, etc.
```

## Common First Tasks

### Task: Initial Project Setup

**User says:** "Set up this project for [language/framework]"

**What to do:**
1. Check `@.cursor/template.json` - confirm it's uninitialized
2. Load `@PROMPTS.md` - find setup prompt for that language
3. Load `@docs/PROJECT_SETUP.md` - follow setup checklist
4. Create/modify necessary files
5. Update `.cursor/template.json` with project info

**Example prompts to suggest:**
```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a Next.js web app
```

### Task: Add Project-Specific Rules

**User says:** "Add rules for [specific concern]"

**What to do:**
1. Load `@.cursor/rules/README.md` - understand rule system
2. Load `@.cursor/rules/SCHEMA.md` - understand frontmatter
3. Check if similar rule exists
4. Create new rule file in `.cursor/rules/`
5. Update `.cursor/MANIFEST.md` if adding new category

### Task: Create Workflow

**User says:** "Help me create a workflow for [activity]"

**What to do:**
1. Load `@docs/workflows/README.md` - understand workflow pattern
2. Create workflow doc in `docs/workflows/`
3. Follow template structure from workflows README

### Task: Implement Feature/Fix Bug

**User says:** "Add [feature]" or "Fix [bug]"

**What to do:**
1. Check project type from `.cursor/template.json`
2. Load relevant rules:
   - `@.cursor/rules/documentation.md`
   - `@.cursor/rules/testing.md`
   - Language-specific rules if they exist
3. Check if agent specs exist in `docs/agents/`
4. Implement following rules and patterns

## Token Efficiency Tips

### Don't Load Everything At Once

❌ **Wasteful:**
```
Load: @docs/cursor/index.md, @docs/workflows/README.md,
      @docs/agents/README.md, @docs/PROJECT_SETUP.md, etc.
```

✅ **Efficient:**
```
Load only what's needed for current task
```

### Use Quick References

Instead of loading full guides, use quick references:
- `@docs/QUICK_REFERENCE.md` - Key concepts
- `@.cursor/rules/QUICK_REFERENCE.md` - Rules summary
- `@docs/cursor/shortcuts.md` - Just keyboard shortcuts

### Load Specific Sections

Cursor's guide is split into focused files:
- Need context management? Load `@docs/cursor/context.md` only
- Need keyboard shortcuts? Load `@docs/cursor/shortcuts.md` only
- Don't load `@docs/cursor/index.md` unless you need the overview

## Understanding Project State

### Fresh Template (Not Customized)

**Indicators:**
- `.cursor/template.json` shows `"project": { "name": "to-be-set", ... }`
- No language-specific files (package.json, requirements.txt, etc.)
- `docs/ARCHITECTURE.md` is still skeleton
- No src/ directory

**What to do:**
- Offer to help set it up
- Reference `@PROMPTS.md` for setup options
- Guide through `@docs/PROJECT_SETUP.md` checklist

### Partially Customized

**Indicators:**
- Some language-specific files exist
- `.cursor/template.json` partially filled
- Some docs filled, others still skeletons

**What to do:**
- Check what's done vs. TODO
- Continue customization as needed
- Update metadata when making changes

### Fully Customized Project

**Indicators:**
- Project-specific files in place
- `.cursor/template.json` fully populated
- Documentation filled in
- Active development happening

**What to do:**
- Work as normal with project
- Follow established patterns
- Reference project-specific rules

## Finding Information Efficiently

### "Where is [concept] explained?"

Check in order:
1. `.cursor/MANIFEST.md` - Lists where everything is
2. Search in relevant doc directory
3. Use `@codebase [concept]` for semantic search

### "What rules apply to [file type]?"

1. Check `.cursor/rules/` for files with matching globs
2. Look at rule frontmatter for `globs:` field
3. Core rules in `.cursorrules` always apply

### "What's the process for [activity]?"

1. Check `docs/workflows/` for workflow docs
2. Check `docs/cursor/workflows.md` for common patterns
3. If none exist, follow general best practices

## Red Flags to Watch For

### Missing Core Files

If these are missing, something's wrong:
- `.cursorrules` - Core rules file
- `.cursor/MANIFEST.md` - Project map
- `.cursor/template.json` - Metadata

**Action:** Alert user that template is incomplete

### Outdated Template

If `.cursor/template.json` shows old version:
- Note it to user
- Suggest updating template
- Check for breaking changes

### Conflicting Information

If rules/docs contradict:
- Note discrepancy to user
- Ask which is correct
- Offer to fix inconsistency

## Quick Reference Card

```
ALWAYS LOAD FIRST:
@.cursorrules            - Core behavior rules
@.cursor/MANIFEST.md     - Project map

SETUP & CUSTOMIZATION:
@PROMPTS.md              - Structured prompts
@docs/PROJECT_SETUP.md   - Setup guide

UNDERSTANDING RULES:
@.cursor/rules/README.md - Rules system
@.cursor/rules/SCHEMA.md - Rule format

USING CURSOR:
@docs/cursor/index.md    - Overview
@docs/cursor/context.md  - @ references
@docs/cursor/features.md - Tools guide

TROUBLESHOOTING:
@docs/TROUBLESHOOTING.md - Common issues

QUICK ANSWERS:
@docs/QUICK_REFERENCE.md        - Key concepts
@.cursor/rules/QUICK_REFERENCE.md - Rules summary
```

## Working with Users

### User Seems Lost

Suggest loading:
```
@QUICK_START.md           # This file
@docs/QUICK_REFERENCE.md  # Overview of concepts
```

### User Wants to Customize

Direct them to:
```
@PROMPTS.md               # Structured prompts
@docs/PROJECT_SETUP.md    # Step-by-step guide
```

### User Has Issue

Check:
```
@docs/TROUBLESHOOTING.md  # Known issues
```

## Summary for AI Agents

1. **Start here:** Load `.cursorrules`, `MANIFEST.md`, `template.json`
2. **Understand state:** Check if template is customized
3. **Load selectively:** Only load docs relevant to current task
4. **Use quick refs:** Prefer summaries over full guides when possible
5. **Follow decision tree:** Use the flow chart above to know what to load
6. **Be token-efficient:** Don't load everything at once

---

**Remember:** This template is designed for YOU (AI agents) to work efficiently. Use the structure to your advantage by loading only what you need, when you need it.

