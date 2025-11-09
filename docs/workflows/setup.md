# Initial Project Setup Workflow

**For Users:** This is your detailed, step-by-step guide for customizing the template.

**For AI:** See `@docs/SETUP_WIZARD.md` for the AI-focused guide. This document is for users who want to understand the process.

---

## Overview

This workflow transforms the generic cursor-project-template into your specific project through 9 phases. Each phase builds on the previous one with clear goals, actions, and verification steps.

**Estimated time:** 1-3 hours depending on project complexity

---

## Quick Start

### Use the Guided Setup (Recommended)

```
@docs/SETUP_WIZARD.md Help me set up this project as a [brief description]
```

The AI will:
- Ask clarifying questions
- Break setup into phases
- Create todos for tracking
- Verify at each step
- Document decisions
- Provide onboarding guide

### Or Follow This Guide Manually

Work through each phase below, checking off items as you complete them.

---

## Phase 0: Discovery & Planning

**Time:** 10-15 minutes  
**Goal:** Understand what you're building before creating files.

### Questions to Answer

#### Project Identity
- [ ] What is the project name?
- [ ] What's a one-sentence description?
- [ ] Is this for personal use, a team, or open source?
- [ ] What problem does it solve?

#### Project Type
- [ ] What type: web app, API, CLI, library, mobile, desktop?
- [ ] Monorepo or single project?
- [ ] Expected scale: prototype, medium app, or large system?

#### Technology Stack
- [ ] Primary programming language(s)?
- [ ] Framework(s) or major libraries?
- [ ] Database (if applicable)?
- [ ] Any must-have technologies?

#### Development Environment
- [ ] Will you use Docker/containers?
- [ ] CI/CD platform (GitHub Actions, GitLab CI, etc.)?
- [ ] Deployment target (cloud provider, self-hosted)?

#### Team & Process
- [ ] Solo project or team?
- [ ] Need code review process?
- [ ] Documentation level: minimal, standard, or extensive?

### Create Initial Decision Log

Document your setup decisions:

```bash
# Create ADR for initial setup
@docs/decisions/000-template.md Create ADR for initial project setup
```

Or manually create `docs/decisions/001-initial-setup.md`:

```markdown
# 001: Initial Project Setup

**Status:** Accepted  
**Date:** [today's date]

## Context
Setting up [project name] to solve [problem].

## Decisions
- Language: [choice] - because [reason]
- Framework: [choice] - because [reason]
- Database: [choice] - because [reason]

## Alternatives Considered
- [Alternative]: Rejected because [reason]

## Consequences
- Need to learn [new technology]
- Will enable [benefit]
```

---

## Phase 1: Core Project Setup

**Time:** 15-20 minutes  
**Goal:** Establish basic project files and configuration.

### Checklist

#### Update Template Metadata
- [ ] Open `.cursor/template.json`
- [ ] Set `project.name` to your project name
- [ ] Set `project.description`
- [ ] Set `project.type` (web-app, api, cli, library, etc.)
- [ ] Set `project.language`
- [ ] Set `project.framework`
- [ ] Set `setup.setup_started` to current ISO date
- [ ] Add `"Phase 1: Core Project Setup"` to `setup.phases_completed`

#### Create Package Management Files
- [ ] Create package file for your language:
  - Node.js: `package.json` with `npm init -y`
  - Python: `requirements.txt` and `setup.py`
  - Go: `go.mod` with `go mod init [module-path]`
  - Rust: `Cargo.toml` with `cargo init`
- [ ] Add project name and description
- [ ] Add initial dependencies
- [ ] Add scripts (dev, build, test, lint)

#### Customize README.md
- [ ] Change project name in header
- [ ] Replace description with your project description
- [ ] Update "Quick Start" section with actual commands
- [ ] Remove or update template-specific text
- [ ] Keep it concise (users can read detailed docs later)

#### Update LICENSE
- [ ] Replace `[Your Name or Organization]` with actual name
- [ ] Update year if needed
- [ ] Verify license type is appropriate (MIT default)

#### Update Ignore Files
- [ ] Customize `.gitignore` for your stack:
  - Node.js: `node_modules/`, `dist/`, `.env`
  - Python: `venv/`, `__pycache__/`, `*.pyc`
  - Go: `/bin/`, `/pkg/`
  - Rust: `/target/`, `Cargo.lock`
- [ ] Customize `.cursorignore` similarly
- [ ] Add any project-specific patterns

### Verification

```bash
# Check package file is valid
npm pkg get name        # Node.js
cat requirements.txt    # Python
go list                 # Go
cargo check             # Rust

# Verify README describes YOUR project
cat README.md

# Check git ignores work
git status              # Should not show ignored files
```

### Commands to Run

```bash
# Node.js example
npm init -y
npm pkg set name="your-project-name"
npm pkg set description="Your description"

# Python example
cat > requirements.txt << EOF
# Add your dependencies here
EOF

# Go example
go mod init github.com/yourusername/your-project

# Rust example
cargo init --name your-project-name
```

---

## Phase 2: Project Structure

**Time:** 15-20 minutes  
**Goal:** Create directory structure and entry points.

### Checklist

#### Create Source Directory
- [ ] Create main source directory:
  - `src/` (most common)
  - `app/` (some frameworks like Next.js)
  - `lib/` (for libraries)
- [ ] Create subdirectories as needed:
  - `src/components/` (frontend)
  - `src/routes/` or `src/api/` (backend)
  - `src/utils/` or `src/lib/` (shared utilities)

#### Create Test Directory
- [ ] Create test directory:
  - `tests/` or `__tests__/` (separate)
  - Or tests alongside code (e.g., `*.test.ts`)
- [ ] Create test subdirectories matching source structure

#### Add Entry Points
- [ ] Create main entry file:
  - `src/index.ts` or `src/main.ts` (TypeScript)
  - `src/index.js` or `src/main.js` (JavaScript)
  - `src/main.py` or `src/__init__.py` (Python)
  - `main.go` (Go)
  - `src/main.rs` or `src/lib.rs` (Rust)
- [ ] Add basic boilerplate (main function, imports, etc.)

#### Configure Path Aliases (if applicable)
- [ ] Set up path aliases in `tsconfig.json` (TypeScript):
  ```json
  {"compilerOptions": {"baseUrl": ".", "paths": {"@/*": ["src/*"]}}}
  ```
- [ ] Update imports to use aliases

### Verification

```bash
# Verify directories exist
ls -la src/
ls -la tests/

# Verify entry point is valid (no syntax errors)
# TypeScript
npx tsc --noEmit

# Python
python -m py_compile src/main.py

# Go
go build

# Rust
cargo check
```

### Update Tracking

```json
// In .cursor/template.json
{
  "customization": {
    "project_structure_added": true
  },
  "setup": {
    "phases_completed": ["Phase 1: Core Project Setup", "Phase 2: Project Structure"]
  }
}
```

---

## Phase 3: Rules & Standards

**Time:** 20-30 minutes  
**Goal:** Customize AI rules for your specific project.

### Checklist

#### Update Core Rules
- [ ] Open `.cursorrules`
- [ ] Add project-specific coding standards
- [ ] Document naming conventions
- [ ] Add framework-specific patterns
- [ ] Include any team conventions

#### Create Modular Rules

Based on your project, create rules in `.cursor/rules/`:

**For Web Frontends:**
- [ ] `frontend-patterns.md` - Component structure, state management
- [ ] `styling.md` - CSS conventions, design system usage

**For APIs/Backends:**
- [ ] `api-design.md` - Endpoint patterns, error handling
- [ ] `database.md` - Query patterns, migrations

**For All Projects:**
- [ ] Update `testing.md` - Customize for your test framework
- [ ] Update `documentation.md` - Your documentation style
- [ ] Update `architecture.md` - Your architectural decisions

**Create custom rules:**
```bash
# Example: Create API design rule
cat > .cursor/rules/api-design.md << 'EOF'
---
description: REST API endpoint patterns and conventions
globs:
  - 'src/api/**/*.ts'
  - 'src/routes/**/*.ts'
alwaysApply: false
---

# API Design Patterns

## Endpoint Structure
- Use RESTful conventions
- Plural nouns for resources: `/api/users`, `/api/posts`
- Nested resources: `/api/users/:id/posts`

## Error Responses
- Use standard HTTP status codes
- Return JSON with: `{error: string, message: string, code: string}`

[Add your specific patterns]
EOF
```

#### Update Glob Patterns
- [ ] Review existing rules
- [ ] Update globs to match YOUR file structure
- [ ] Test by editing a file - does the rule auto-apply?

### Verification

```bash
# Test modular rules load
# In Cursor, try: @.cursor/rules/[your-new-rule].md

# Test auto-apply
# Edit a file matching a glob pattern
# Check if rule is auto-loaded in context
```

### Update Tracking

```json
{
  "customization": {
    "core_rules_updated": true,
    "modular_rules_added": true
  },
  "rules": {
    "custom_rules": ["api-design.md", "frontend-patterns.md"],
    "auto_applied_rules": ["testing.md", "api-design.md"],
    "manual_rules": ["architecture.md", "documentation.md"]
  }
}
```

---

## Phase 4: Development Environment

**Time:** 30-40 minutes  
**Goal:** Set up all development tools.

### Checklist

#### Install Dependencies
- [ ] Run package manager install:
  ```bash
  npm install          # Node.js
  pip install -r requirements.txt  # Python
  go mod download      # Go
  cargo build          # Rust
  ```
- [ ] Verify no errors
- [ ] Check for security vulnerabilities

#### Configure Linter
- [ ] Install linter:
  - ESLint (JavaScript/TypeScript)
  - Pylint or Ruff (Python)
  - golangci-lint (Go)
  - Clippy (Rust - included with cargo)
- [ ] Create linter config file
- [ ] Add lint script to package file
- [ ] Run linter to verify it works

#### Configure Formatter
- [ ] Install formatter:
  - Prettier (JavaScript/TypeScript)
  - Black (Python)
  - gofmt (Go - included)
  - rustfmt (Rust - included with cargo)
- [ ] Create formatter config file
- [ ] Add format script
- [ ] Configure format-on-save in IDE

#### Set Up Testing
- [ ] Install test framework:
  - Jest, Vitest (JavaScript/TypeScript)
  - Pytest (Python)
  - Go's testing package (built-in)
  - Cargo test (Rust - built-in)
- [ ] Create test config file
- [ ] Add example test files
- [ ] Add test scripts (test, test:watch, test:coverage)
- [ ] Run tests to verify setup

#### Configure Build Tools (if needed)
- [ ] Install build tool:
  - Vite, Webpack (JavaScript/TypeScript)
  - setuptools (Python)
  - Go build (built-in)
  - Cargo (Rust)
- [ ] Create build config
- [ ] Add build script
- [ ] Test build succeeds

#### Create Environment Variables
- [ ] Create `.env.example`:
  ```bash
  # Database
  DATABASE_URL=postgresql://localhost/mydb
  
  # API Keys
  API_KEY=your_key_here
  
  # App Config
  PORT=3000
  NODE_ENV=development
  ```
- [ ] Document each variable
- [ ] Verify `.env` is in `.gitignore`
- [ ] Copy to `.env` for local development

### Verification

```bash
# Dependencies installed
npm list --depth=0   # or equivalent

# Linter works
npm run lint

# Formatter works
npm run format

# Tests run
npm test

# Build succeeds (if applicable)
npm run build

# Dev server starts
npm run dev
```

### Update Tracking

```json
{
  "development": {
    "package_manager": "npm",
    "test_framework": "jest",
    "linter": "eslint",
    "formatter": "prettier",
    "build_tool": "vite"
  },
  "setup": {
    "phases_completed": [..., "Phase 4: Development Environment"]
  }
}
```

---

## Phase 5: Documentation

**Time:** 30-45 minutes  
**Goal:** Fill in project documentation.

### Checklist

#### Fill ARCHITECTURE.md
- [ ] System overview (2-3 paragraphs)
- [ ] Component diagram or description
- [ ] Data flow explanation
- [ ] Tech stack details with versions
- [ ] Key design decisions
- [ ] Remove all skeleton/template text

#### Customize CONTRIBUTING.md
- [ ] Development setup steps (test them!)
- [ ] Coding standards (link to .cursorrules)
- [ ] Commit message format
- [ ] PR process (if team)
- [ ] Review guidelines (if team)
- [ ] Remove template text

#### Create Project-Specific Docs

**If you have an API:**
- [ ] Create `docs/API.md`
- [ ] Document endpoints, request/response formats
- [ ] Include authentication details
- [ ] Add example requests

**If you have a database:**
- [ ] Create `docs/DATABASE.md`
- [ ] Document schema
- [ ] Explain migrations process
- [ ] Include ER diagram or description

**If deploying:**
- [ ] Create `docs/DEPLOYMENT.md`
- [ ] Document deployment process
- [ ] List environment requirements
- [ ] Include troubleshooting steps

#### Update Documentation Index
- [ ] Edit `docs/README.md`
- [ ] List all documentation files with descriptions
- [ ] Organize into logical sections
- [ ] Add links to key resources

#### Create Initial Setup ADR
- [ ] Create `docs/decisions/001-initial-setup.md`
- [ ] Document key setup decisions
- [ ] Explain technology choices
- [ ] Note alternatives considered
- [ ] Record trade-offs accepted

### Verification

```bash
# Read through each doc - is it clear?
cat docs/ARCHITECTURE.md
cat docs/CONTRIBUTING.md

# No template placeholders remain?
grep -r "to-be-set" docs/
grep -r "skeleton" docs/
# Should return nothing or only in templates/

# Documentation index is complete?
cat docs/README.md
```

### Update Tracking

```json
{
  "customization": {
    "documentation_filled": true,
    "decisions_documented": true
  },
  "decisions": {
    "decision_count": 1,
    "latest_decision": "001-initial-setup.md"
  }
}
```

---

## Phase 6: Workflows & CI/CD

**Time:** 30-45 minutes  
**Goal:** Document processes and set up automation.

### Checklist

#### Create Workflow Documents

**Commit Workflow (`docs/workflows/commit.md`):**
- [ ] Pre-commit checks (lint, test)
- [ ] Commit message format
- [ ] When to commit (logical units)

**Feature Development (`docs/workflows/feature.md`):**
- [ ] Planning a feature
- [ ] Creating a branch (if using)
- [ ] Implementation steps
- [ ] Testing requirements
- [ ] Documentation requirements
- [ ] Review process

**Bug Fixing (`docs/workflows/bugfix.md`):**
- [ ] Reproducing the bug
- [ ] Writing a failing test
- [ ] Fixing the issue
- [ ] Verification steps

#### Set Up CI/CD

**For GitHub Actions (`.github/workflows/`):**

- [ ] Create `.github/workflows/test.yml`:
  ```yaml
  name: Test
  on: [push, pull_request]
  jobs:
    test:
      runs-on: ubuntu-latest
      steps:
        - uses: actions/checkout@v3
        - uses: actions/setup-node@v3
          with:
            node-version: '18'
        - run: npm ci
        - run: npm test
  ```

- [ ] Create `.github/workflows/lint.yml` (similar structure)
- [ ] Create `.github/workflows/deploy.yml` (if deploying)

**For GitLab CI (`.gitlab-ci.yml`):**
- [ ] Create `.gitlab-ci.yml` with test/lint/deploy stages

**For other platforms:**
- [ ] Create appropriate CI config

#### Add Pre-commit Hooks (Optional)
- [ ] Install husky: `npm install -D husky`
- [ ] Initialize: `npx husky install`
- [ ] Add pre-commit hook:
  ```bash
  npx husky add .husky/pre-commit "npm run lint && npm test"
  ```
- [ ] Test hook works

### Verification

```bash
# Workflow docs are clear and actionable
cat docs/workflows/commit.md

# CI config is valid
# GitHub Actions: Use act or push to test
# GitLab: gitlab-ci-lint command

# Pre-commit hooks work (if added)
git commit -m "test" --allow-empty
# Should run lint and tests
```

### Update Tracking

```json
{
  "customization": {
    "workflows_added": true,
    "ci_cd_configured": true
  }
}
```

---

## Phase 7: Specialized Features (Optional)

**Time:** 30-60 minutes (if needed)  
**Goal:** Add Docker, monorepo, or other specialized configurations.

### Docker Setup (If Using)

#### Checklist
- [ ] Create `Dockerfile`:
  ```dockerfile
  FROM node:18-alpine
  WORKDIR /app
  COPY package*.json ./
  RUN npm ci
  COPY . .
  RUN npm run build
  CMD ["npm", "start"]
  ```
- [ ] Create `docker-compose.yml` (if multiple services)
- [ ] Create `.dockerignore`
- [ ] Test: `docker build -t your-app .`
- [ ] Test: `docker run -p 3000:3000 your-app`

### Monorepo Setup (If Using)

#### Checklist
- [ ] Choose and install tool (Turborepo, Nx, etc.)
- [ ] Create workspace config (turbo.json, nx.json, etc.)
- [ ] Create directory structure:
  ```
  /apps/
    /web/
    /api/
  /packages/
    /shared-types/
    /shared-config/
  ```
- [ ] Configure workspace dependencies
- [ ] Test: All packages build

### Agent Specs (If Multi-Domain Project)

#### Checklist
- [ ] Create `docs/agents/BACKEND.md` (if backend)
- [ ] Create `docs/agents/FRONTEND.md` (if frontend)
- [ ] Create `docs/agents/TESTING.md` (if dedicated testing)
- [ ] Each spec should:
  - Define the agent's focus area
  - List rules to always reference
  - Describe responsibilities
  - Provide example prompts

### Verification

```bash
# Docker works
docker build -t test .
docker run --rm test

# Monorepo commands work
npm run build    # or turbo run build, nx run-many, etc.

# Agent specs are clear and useful
cat docs/agents/BACKEND.md
```

### Update Tracking

```json
{
  "customization": {
    "agent_specs_added": true
  }
}
```

---

## Phase 8: Verification

**Time:** 20-30 minutes  
**Goal:** Verify everything works before committing.

### Create Verification Checklist

Either use AI to generate:
```
@docs/templates/VERIFICATION.md Create a verification checklist for my [stack] project
```

Or manually create `VERIFICATION.md` in project root with checks for:
- Dependencies install
- Linter runs
- Tests pass
- Build succeeds
- Dev server starts
- Documentation complete
- All configs valid

### Run Full Verification

Work through the entire `VERIFICATION.md` checklist:
- [ ] Complete all "Basic Setup" checks
- [ ] Complete all "Development Environment" checks
- [ ] Complete all "Testing" checks
- [ ] Complete all "Building" checks
- [ ] Complete all "Documentation" checks
- [ ] Complete specialized feature checks (Docker, etc.)

### Address Any Failures

If something doesn't work:
1. Identify the specific issue
2. Check `@docs/TROUBLESHOOTING.md` for solutions
3. Fix the problem
4. Re-run that verification
5. Don't proceed until all checks pass

### Update Tracking

```json
{
  "customization": {
    "verification_completed": true
  },
  "setup": {
    "verification_passed": true
  }
}
```

---

## Phase 9: Onboarding & Completion

**Time:** 15-20 minutes  
**Goal:** Understand how to use the customized template and make initial commit.

### Review Onboarding Guide

- [ ] Read `@docs/ONBOARDING.md`
- [ ] Understand how to use modular rules
- [ ] Learn how to create ADRs for future decisions
- [ ] Review workflow documents you created
- [ ] Understand agent specs (if created)

### Make Initial Commit

```bash
# Add all files
git add .

# Commit with detailed message
git commit -m "Initial project setup from cursor-project-template

Customizations:
- Language: [your language]
- Framework: [your framework]
- Database: [your database if applicable]
- Architecture: [your structure]

Technologies:
- [List key technologies]

Setup includes:
- Complete development environment
- CI/CD configuration
- Documentation
- ADRs for decision tracking

See docs/decisions/001-initial-setup.md for details."
```

### Push to Remote (If Applicable)

```bash
# Add remote
git remote add origin https://github.com/yourusername/your-repo.git

# Push
git push -u origin main
```

### Clean Up

- [ ] Delete `VERIFICATION.md` (or move to `docs/archive/`)
- [ ] Remove any temporary test files
- [ ] Archive or remove template placeholder files

### Update Final Tracking

```json
{
  "setup": {
    "setup_completed": "[current ISO date]",
    "onboarding_shown": true,
    "phases_completed": [
      "Phase 1: Core Project Setup",
      "Phase 2: Project Structure",
      "Phase 3: Rules & Standards",
      "Phase 4: Development Environment",
      "Phase 5: Documentation",
      "Phase 6: Workflows & CI/CD",
      "Phase 7: Specialized Features",
      "Phase 8: Final Setup & Verification",
      "Phase 9: Onboarding & Next Steps"
    ]
  }
}
```

---

## Post-Setup: What's Next?

### Immediate Actions (Today)

- [ ] Try the quick wins from `ONBOARDING.md`
- [ ] Create a simple "hello world" feature
- [ ] Add a test for it
- [ ] Document it
- [ ] Verify your workflow works end-to-end

### This Week

- [ ] Start first real feature
- [ ] Invite team members (if applicable)
- [ ] Set up production environment (if deploying)
- [ ] Create any missing documentation

### Ongoing

- [ ] Update rules as patterns emerge
- [ ] Create ADRs for important decisions
- [ ] Keep documentation current
- [ ] Refine workflows based on experience

---

## Troubleshooting

### Setup Feels Overwhelming

**Solution:** Don't do it all at once. Focus on phases 1-4 first (core setup through dev environment). Get code working, then add docs/workflows/specialized features.

### Not Sure What to Choose

**Solution:** 
- Create an ADR exploring options
- Ask AI for trade-off analysis
- Start with familiar/simple choice
- Can change later

### Rules Aren't Working

**Solution:**
- Check glob patterns match your files
- Verify YAML frontmatter is valid
- Test with manual reference: `@.cursor/rules/[rule].md`

### Tests/Build Failing

**Solution:**
- Check error messages carefully
- Verify all dependencies installed
- Check configuration files for typos
- See `@docs/TROUBLESHOOTING.md`

### Documentation Feels Like Busywork

**Solution:**
- Start minimal - expand later
- Focus on what's not obvious from code
- Use AI to help generate initial versions
- Update as you develop

---

## Summary

This workflow provides a structured path from template to working project:

✅ **9 phases** - Each with clear goal and verification
✅ **Checklists** - Nothing is forgotten
✅ **Commands** - Copy-paste ready
✅ **Verification** - Catch issues early
✅ **Documentation** - Future-proof your decisions

**Estimated total time:** 2.5-4 hours for complete setup

**Key to success:** Don't rush. Each phase builds on the previous. Verify before moving forward.

---

**Need help?** Use AI with: `@docs/SETUP_WIZARD.md` or reference specific phase sections from this document.
