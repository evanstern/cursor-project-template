# Setup Wizard

<!-- For AI: This is YOUR primary guide for walking users through project setup. Read this FIRST when user asks to set up a project. -->

## For AI Agents: Quick Start

When a user asks to "set up this project as [description]":

1. **Ask Phase 0 questions** (see below) - Don't skip this!
2. **Create todos** for applicable phases (use `todo_write`)
3. **Execute one phase at a time** - Complete before moving to next
4. **Update `.cursor/template.json`** after each phase
5. **Provide `ONBOARDING.md`** at the end

**Key principle:** Manageable phases, not overwhelming file dumps.

---

## The 9 Setup Phases

Each phase has: Goal → Questions → Actions → Verification → Update tracking

### Phase 0: Discovery & Planning

**Goal:** Understand project requirements before creating files.

**Ask these questions:**

```
Project Identity:
- Project name?
- One-sentence description?
- Solo, team, or open source?

Project Type:
- Type: web app, API, CLI, library, mobile, desktop?
- Monorepo or single project?
- Expected scale: prototype, medium app, large system?

Technology Stack:
- Primary language(s)?
- Framework(s)?
- Database (if applicable)?
- Must-have technologies?

Development Environment:
- Using Docker/containers?
- CI/CD platform?
- Deployment target?

Team & Process:
- Solo or team?
- Need code review process?
- Documentation level: minimal, standard, extensive?
```

**Actions:**
- Record answers
- Suggest creating ADR: `@docs/decisions/000-template.md Create initial setup ADR`
- Identify which phases apply (e.g., skip Docker if not using)

**Don't create files yet.** Just gather information.

---

### Phase 1: Core Project Setup

**Goal:** Basic project files and configuration.

**Key Actions:**
- Update `.cursor/template.json` project fields
- Create package file (package.json, requirements.txt, etc.)
- Update README.md with project details
- Update LICENSE with correct name
- Customize .gitignore and .cursorignore

**Verification:**
```bash
# Package file valid
# README describes THIS project
# LICENSE has correct info
```

**Update tracking:**
```json
{"setup": {"setup_started": "[ISO date]", "phases_completed": ["Phase 1"]}}
```

**Detailed checklist:** See `@docs/workflows/setup.md` Phase 1

---

### Phase 2: Project Structure

**Goal:** Create directory structure and entry points.

**Ask:** Preferred structure? Where should source/tests live?

**Key Actions:**
- Create src/ (or appropriate directory)
- Create test directory
- Add entry point file(s)
- Add basic boilerplate

**Verification:**
```bash
# Directories exist
# Entry point file valid
# No IDE errors
```

**Update tracking:**
```json
{"customization": {"project_structure_added": true}, "setup": {"phases_completed": [..., "Phase 2"]}}
```

---

### Phase 3: Rules & Standards

**Goal:** Customize AI rules for this project.

**Ask:** Specific conventions? Framework patterns to enforce?

**Key Actions:**
- Update `.cursorrules` with project specifics
- Create modular rules in `.cursor/rules/` for:
  - Framework-specific patterns
  - API design (if applicable)
  - Database patterns (if applicable)
- Update glob patterns to match project structure
- Customize existing rules (testing.md, documentation.md, architecture.md)

**Verification:**
```bash
# Can reference: @.cursor/rules/[new-rule].md
# Auto-apply works: edit file matching glob
# Rules are relevant to THIS project
```

**Update tracking:**
```json
{"customization": {"core_rules_updated": true, "modular_rules_added": true}, "rules": {"custom_rules": ["api-design.md"], "auto_applied_rules": ["testing.md"], "manual_rules": ["architecture.md"]}}
```

---

### Phase 4: Development Environment

**Goal:** Set up linting, testing, building.

**Key Actions:**
- Install dependencies
- Configure linter + add lint script
- Configure formatter + add format script
- Set up test framework + add example tests
- Configure build tools (if needed)
- Create .env.example

**Verification:**
```bash
[install command]    # Succeeds
[lint command]       # Runs without errors
[test command]       # Runs (even if no tests yet)
[build command]      # Succeeds (if applicable)
```

**Update tracking:**
```json
{"development": {"package_manager": "npm", "test_framework": "jest", "linter": "eslint", "formatter": "prettier", "build_tool": "vite"}}
```

---

### Phase 5: Documentation

**Goal:** Fill in docs for this project.

**Ask:** Documentation depth needed? Need API/database docs?

**Key Actions:**
- Fill `docs/ARCHITECTURE.md` (system overview, components, data flow)
- Customize `docs/CONTRIBUTING.md` (setup steps, standards, PR process)
- Create project-specific docs (API.md, DATABASE.md, etc.)
- Update `docs/README.md` index
- Create initial ADR: `docs/decisions/001-initial-setup.md`

**Verification:**
```bash
# ARCHITECTURE.md describes THIS project (no skeleton text)
# CONTRIBUTING.md has accurate setup steps
# docs/README.md indexes all docs
# Initial ADR created
```

**Update tracking:**
```json
{"customization": {"documentation_filled": true, "decisions_documented": true}, "decisions": {"decision_count": 1, "latest_decision": "001-initial-setup.md"}}
```

---

### Phase 6: Workflows & CI/CD

**Goal:** Document processes and set up automation.

**Key Actions:**
- Create workflow docs in `docs/workflows/` (commit.md, feature.md, bugfix.md)
- Set up CI/CD config (.github/workflows/, .gitlab-ci.yml, etc.)
- Add pre-commit hooks (optional)

**Verification:**
```bash
# Workflow docs are actionable
# CI config is valid (syntax check)
```

**Update tracking:**
```json
{"customization": {"workflows_added": true, "ci_cd_configured": true}}
```

---

### Phase 7: Specialized Features (Optional)

**Goal:** Add Docker, monorepo, agent specs, or other specialized configs.

**Only if needed:**

**Docker:**
- Create Dockerfile(s), docker-compose.yml, .dockerignore
- Test: `docker build` and `docker-compose up`

**Monorepo:**
- Install tool (Turborepo, Nx, etc.)
- Create turbo.json/nx.json
- Create packages/ structure
- Test: workspace commands work

**Agent Specs:**
- Create `docs/agents/BACKEND.md`, `FRONTEND.md`, `TESTING.md`, etc.
- Agent specs reference correct rules

**Update tracking:**
```json
{"customization": {"agent_specs_added": true}}
```

---

### Phase 8: Verification

**Goal:** Ensure everything works before committing.

**Key Actions:**
1. **Generate verification checklist:**
   ```
   @docs/templates/VERIFICATION.md Create verification checklist for [stack]
   ```
   - Customize from template for user's specific stack
   - Save to project root as `VERIFICATION.md`
   
2. **Run all verifications:**
   - Dependencies install
   - Linter runs
   - Tests run
   - Build succeeds
   - Dev server starts
   - Docker works (if applicable)
   - All documentation filled

3. **Address failures:**
   - Fix issues found
   - Re-verify
   - Don't proceed until all pass

**Verification:**
```bash
# All items in VERIFICATION.md pass ✅
```

**Update tracking:**
```json
{"customization": {"verification_completed": true}, "setup": {"verification_passed": true, "phases_completed": [..., "Phase 8"]}}
```

---

### Phase 9: Onboarding & Completion

**Goal:** Show user how to use the customized template.

**Key Actions:**
1. **Present onboarding guide:**
   ```
   @docs/ONBOARDING.md Show user how to use template features
   ```
   - Customize for their specific setup
   - Highlight created rules, workflows, agent specs
   - Suggest relevant quick wins
   
2. **Guide initial commit:**
   ```bash
   git add .
   git commit -m "Initial project setup from cursor-project-template
   
   Customizations:
   - [List major customizations]
   - Technologies: [stack]
   - Structure: [architecture]
   
   See docs/decisions/001-initial-setup.md"
   ```

3. **Cleanup:**
   - Delete `VERIFICATION.md` (or move to docs/archive/)
   - Remove any template placeholder files

**Update tracking:**
```json
{"setup": {"setup_completed": "[ISO date]", "onboarding_shown": true, "phases_completed": ["Phase 1", ..., "Phase 9"]}}
```

---

## AI Agent Guidelines

### Communication Style

**At each phase:**
- **Start:** "🎯 Phase X: [goal]"
- **During:** "Creating [N] files: [list key ones]"
- **Complete:** "✅ Phase X complete"
- **Transition:** "Ready for Phase Y? [what happens next]"

**For large phases:**
- Group files logically: "Creating 5 configuration files..."
- Summarize after: "Created 12 files in 4 directories"
- Highlight key files: "Most important: package.json - defines dependencies"

### Adaptation

**Not all phases apply:**
- CLI tool? Skip Docker (Phase 7)
- Solo prototype? Minimal docs (Phase 5)
- Library? Skip workflows (Phase 6)

**Adjust based on:**
- Project type
- Team size
- Time constraints
- User experience level

### Decision Documentation

**Throughout setup, suggest recording decisions:**

When making a choice:
```
"I'm choosing X over Y because [reason]. Should I document this in an ADR?"
```

If yes, create ADR immediately:
```
@docs/decisions/000-template.md Create ADR: Chose [X] for [purpose]
```

**Good candidates for ADRs:**
- Technology selections
- Architectural patterns
- Database/storage choices
- Framework decisions
- Deployment strategies

### Verification is Critical

**Don't skip verification steps.**

If verification fails:
1. Identify the specific issue
2. Fix it immediately
3. Re-verify the fix
4. Then continue

**Never proceed with failing verification.**

### Todo Management

Use `todo_write` to track progress:

**At start (after Phase 0):**
```json
[
  {"id": "1", "content": "Phase 1: Core Project Setup", "status": "in_progress"},
  {"id": "2", "content": "Phase 2: Project Structure", "status": "pending"},
  // ... applicable phases
]
```

**After each phase:**
```json
[
  {"id": "1", "status": "completed"},
  {"id": "2", "status": "in_progress"}
]
```

This shows user clear progress.

---

## Common Patterns

### Monorepo Setup
```
Phase 0: Identify monorepo tool (Turborepo, Nx, pnpm workspaces)
Phase 2: Create apps/ and packages/ structure
Phase 3: Create monorepo.md rule
Phase 7: Configure monorepo tool
```

### Full-Stack Web App
```
Phase 0: Identify frontend + backend frameworks
Phase 2: Create separate frontend/backend directories or monorepo
Phase 3: Create frontend.md and backend.md rules
Phase 7: Create FRONTEND.md and BACKEND.md agent specs
```

### Simple Library
```
Skip Phase 6 (workflows/CI minimal)
Skip Phase 7 (no Docker)
Phase 5: Focus on API documentation
```

---

## Troubleshooting

**User doesn't know what they want:**
- Ask more specific questions
- Offer common options with pros/cons
- Suggest starting simple, can add later

**Too many files at once:**
- You're not batching by phase
- Review this guide - execute ONE phase at a time
- Use todos to show progress

**Rules not working:**
- Check glob patterns match file structure
- Verify YAML frontmatter is valid
- Test with manual reference first

**Verification failing:**
- Don't proceed until fixed
- Use `@docs/TROUBLESHOOTING.md`
- Check for typos in config files

---

## Summary

This wizard provides structure without prescription:

✅ **9 clear phases** - Manageable chunks
✅ **Built-in verification** - Catch issues early
✅ **Decision recording** - Context for future
✅ **Progress tracking** - Always know status
✅ **Feature introduction** - User learns through onboarding
✅ **Flexible** - Adapt to project needs

**Key to success:** 
- Ask questions in Phase 0
- Execute one phase at a time
- Verify before proceeding
- Update tracking after each phase
- Provide onboarding at end

---

**For detailed checklists:** See `@docs/workflows/setup.md`

**For users:** If setup isn't going well, reference this file: `@docs/SETUP_WIZARD.md help me set up this project step by step`
