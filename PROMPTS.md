# Customization Prompts

<!-- For AI: These are structured prompts you can suggest to users for common customization tasks -->

This file contains ready-to-use prompts for customizing this template. Each prompt is structured with metadata to help AI agents suggest the right prompt at the right time.

## How to Use These Prompts

### For Users
Copy and paste these prompts into Cursor, replacing placeholders `[like this]` with your specific values.

### For AI Agents
Reference specific prompts by their ID when suggesting to users:
```
I recommend using the "Initial TypeScript Setup" prompt from @PROMPTS.md
```

---

## Initial Setup Prompts

### Prompt: Initial TypeScript/JavaScript Setup
**ID:** `setup-typescript`  
**When to use:** Setting up a TypeScript or JavaScript project  
**Expected outcome:** package.json, tsconfig.json, basic dependencies

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a TypeScript project with [framework: Next.js/Express/React/Vue/etc.]
```

**Follow-up actions:**
- Install dependencies: `npm install`
- Review generated configuration files
- Update `.gitignore` for Node.js

---

### Prompt: Initial Python Setup
**ID:** `setup-python`  
**When to use:** Setting up a Python project  
**Expected outcome:** requirements.txt, setup.py, virtual environment guidance

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a Python project using [framework: FastAPI/Django/Flask/etc.]
```

**Follow-up actions:**
- Create virtual environment: `python -m venv venv`
- Install dependencies: `pip install -r requirements.txt`
- Update `.gitignore` for Python

---

### Prompt: Initial Go Setup
**ID:** `setup-go`  
**When to use:** Setting up a Go project  
**Expected outcome:** go.mod, main.go, project structure

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a Go project for [type: CLI/API/web service/etc.]
```

**Follow-up actions:**
- Run `go mod tidy`
- Review project structure
- Update `.gitignore` for Go

---

### Prompt: Initial Rust Setup
**ID:** `setup-rust`  
**When to use:** Setting up a Rust project  
**Expected outcome:** Cargo.toml, src/main.rs or src/lib.rs

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a Rust project for [type: binary/library/etc.]
```

**Follow-up actions:**
- Run `cargo build` to verify
- Review Cargo.toml dependencies
- Update `.gitignore` for Rust

---

### Prompt: Initial Mobile (React Native) Setup
**ID:** `setup-react-native`  
**When to use:** Setting up a React Native/Expo project  
**Expected outcome:** React Native project structure, package.json, app.json

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a React Native project using [Expo/bare React Native]
```

**Follow-up actions:**
- Install dependencies
- Review platform-specific configs
- Test on simulator/emulator

---

### Prompt: Generic Language Setup
**ID:** `setup-generic`  
**When to use:** Setting up any other language  
**Expected outcome:** Language-appropriate configuration

```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project for [language: Ruby/PHP/Java/C#/etc.] using [framework/tools]
```

**Follow-up actions:**
- Install language-specific dependencies
- Review generated configurations
- Update ignore files

---

## Configuration Prompts

### Prompt: Update Ignore Files
**ID:** `config-ignores`  
**When to use:** Need to add project-specific ignores  
**Expected outcome:** Updated .gitignore and .cursorignore

```
@.gitignore @.cursorignore Update these files for a [language/framework] project
```

---

### Prompt: Add Environment Configuration
**ID:** `config-env`  
**When to use:** Need to set up environment variables  
**Expected outcome:** .env.example file with documented variables

```
@docs/PROJECT_SETUP.md Create a .env.example file for [type of project] with variables for [database/API keys/etc.]
```

---

### Prompt: Set Up Testing Framework
**ID:** `config-testing`  
**When to use:** Need to configure testing  
**Expected outcome:** Test framework configured, sample tests

```
@.cursor/rules/testing.md Set up [Jest/Pytest/Go testing/etc.] for this project with example tests
```

---

## Rules Prompts

### Prompt: Add Project-Specific Rule
**ID:** `rules-add-specific`  
**When to use:** Need custom rule for specific concern  
**Expected outcome:** New modular rule file

```
@.cursor/rules/README.md @.cursor/rules/SCHEMA.md Create a new modular rule for [API design/security/performance/etc.]
```

---

### Prompt: Create Language-Specific Rule
**ID:** `rules-add-language`  
**When to use:** Need language-specific coding standards  
**Expected outcome:** Language-specific rule file

```
@.cursor/rules/README.md Create a modular rule for [TypeScript/Python/Go/etc.] best practices
```

---

### Prompt: Update Core Rules
**ID:** `rules-update-core`  
**When to use:** Need to add project-wide standards  
**Expected outcome:** Updated .cursorrules file

```
@.cursorrules Add project-specific rules for [naming conventions/error handling/logging/etc.]
```

---

## Documentation Prompts

### Prompt: Fill In Architecture Documentation
**ID:** `docs-architecture`  
**When to use:** Project structure is established  
**Expected outcome:** Completed ARCHITECTURE.md

```
@docs/ARCHITECTURE.md @src/ Document the architecture of this [type] project including [components/layers/services/etc.]
```

---

### Prompt: Create API Documentation
**ID:** `docs-api`  
**When to use:** Need to document API endpoints  
**Expected outcome:** API.md with endpoint documentation

```
@docs/ Create API documentation for the endpoints in @src/api/ following @.cursor/rules/documentation.md standards
```

---

### Prompt: Document Database Schema
**ID:** `docs-database`  
**When to use:** Need to document data models  
**Expected outcome:** DATABASE.md or schema documentation

```
@docs/ Create database schema documentation for [database models/tables/collections] in @src/models/
```

---

### Prompt: Create Deployment Guide
**ID:** `docs-deployment`  
**When to use:** Need deployment documentation  
**Expected outcome:** DEPLOYMENT.md

```
@docs/ Create a deployment guide for this [type] project covering [environment/CI-CD/hosting platform]
```

---

## Workflow Prompts

### Prompt: Create Commit Workflow
**ID:** `workflow-commit`  
**When to use:** Need standardized commit process  
**Expected outcome:** docs/workflows/commit.md

```
@docs/workflows/README.md Create a commit workflow that includes [linting/testing/commit message format/etc.]
```

---

### Prompt: Create Feature Development Workflow
**ID:** `workflow-feature`  
**When to use:** Need feature development process  
**Expected outcome:** docs/workflows/feature.md

```
@docs/workflows/README.md Create a feature development workflow covering [planning/implementation/testing/review]
```

---

### Prompt: Create Release Workflow
**ID:** `workflow-release`  
**When to use:** Need release process documented  
**Expected outcome:** docs/workflows/release.md

```
@docs/workflows/README.md Create a release workflow for [versioning strategy/changelog/deployment]
```

---

## Agent Prompts

### Prompt: Create Backend Agent Spec
**ID:** `agent-backend`  
**When to use:** Backend development needs specialized guidance  
**Expected outcome:** docs/agents/BACKEND.md

```
@docs/agents/README.md Create a backend agent specification for [language/framework] focusing on [API/database/business logic]
```

---

### Prompt: Create Frontend Agent Spec
**ID:** `agent-frontend`  
**When to use:** Frontend development needs specialized guidance  
**Expected outcome:** docs/agents/FRONTEND.md

```
@docs/agents/README.md Create a frontend agent specification for [framework] focusing on [components/state/styling]
```

---

### Prompt: Create Testing Agent Spec
**ID:** `agent-testing`  
**When to use:** Testing needs specialized guidance  
**Expected outcome:** docs/agents/TESTING.md

```
@docs/agents/README.md Create a testing agent specification for [testing framework] covering [unit/integration/e2e tests]
```

---

### Prompt: Create Mobile Agent Spec
**ID:** `agent-mobile`  
**When to use:** Mobile development needs platform-specific guidance  
**Expected outcome:** docs/agents/MOBILE.md

```
@docs/agents/README.md Create a mobile agent specification for [React Native/Flutter/native] covering [platform differences/navigation/native modules]
```

---

## Structure Prompts

### Prompt: Create Source Directory Structure
**ID:** `structure-src`  
**When to use:** Need to scaffold source code structure  
**Expected outcome:** src/ directory with appropriate subdirectories

```
@docs/PROJECT_SETUP.md Create a source code directory structure for a [type] project using [architecture: layered/microservices/etc.]
```

---

### Prompt: Add CI/CD Configuration
**ID:** `structure-cicd`  
**When to use:** Need continuous integration setup  
**Expected outcome:** .github/workflows/ or similar CI config

```
@docs/PROJECT_SETUP.md Set up [GitHub Actions/GitLab CI/CircleCI] for this project to run [tests/linting/deployment]
```

---

### Prompt: Create Docker Configuration
**ID:** `structure-docker`  
**When to use:** Need containerization  
**Expected outcome:** Dockerfile, docker-compose.yml

```
@docs/PROJECT_SETUP.md Create Docker configuration for this [type] project with [services/dependencies]
```

---

## Maintenance Prompts

### Prompt: Update Dependencies
**ID:** `maintenance-deps`  
**When to use:** Dependencies need updating  
**Expected outcome:** Updated dependency files

```
Review and update dependencies in [package.json/requirements.txt/go.mod/etc.] checking for security vulnerabilities and breaking changes
```

---

### Prompt: Add Pre-commit Hooks
**ID:** `maintenance-hooks`  
**When to use:** Need automated quality checks  
**Expected outcome:** Git hooks or pre-commit configuration

```
@docs/PROJECT_SETUP.md Set up pre-commit hooks for [linting/formatting/testing] using [husky/pre-commit/etc.]
```

---

### Prompt: Refactor for Better Organization
**ID:** `maintenance-refactor`  
**When to use:** Code structure needs improvement  
**Expected outcome:** Refactored code with better organization

```
@docs/ARCHITECTURE.md @.cursor/rules/architecture.md Refactor [directory/module] to follow [pattern/principle]
```

---

## Multi-Step Workflows

### Workflow: Complete Initial Setup (Guided)
**ID:** `workflow-guided-setup`  
**Recommended for:** All new project setups  
**Uses:** Setup Wizard for structured approach

**Primary Prompt:**
```
@docs/SETUP_WIZARD.md Help me set up this project as a [brief description]
```

**What this does:**
- AI asks clarifying questions (Phase 0)
- Breaks setup into manageable phases
- Verifies at each checkpoint
- Documents decisions as they're made
- Provides onboarding guide at the end

**Benefits:**
- ✅ No information overload
- ✅ Clear decision points
- ✅ Verification built-in
- ✅ Learns template features after setup

---

### Workflow: Complete Initial Setup (Quick)
**ID:** `workflow-complete-setup`  
**Recommended for:** When you know exactly what you want  
**Steps:** Multiple prompts in sequence

**Step 1: Initialize Project**
```
@.cursorrules @docs/PROJECT_SETUP.md Set up this project as a [language/framework] project
```

**Step 2: Configure Testing**
```
@.cursor/rules/testing.md Set up [test framework] with example tests
```

**Step 3: Add Documentation**
```
@docs/ARCHITECTURE.md Document the initial project structure
```

**Step 4: Set Up CI/CD**
```
Set up [CI/CD platform] to run tests and linting
```

**Step 5: Verify Setup**
```
Create a VERIFICATION.md checklist and verify all components work
```

**Note:** Quick setup is faster but may miss important decision points. Consider guided setup for complex projects.

---

### Workflow: Add New Feature Domain
**ID:** `workflow-add-domain`  
**Steps:** Multiple prompts for adding a new feature area

**Step 1: Create Module Structure**
```
@docs/ARCHITECTURE.md Create a new module for [feature] in src/[feature]/
```

**Step 2: Add Domain Rules** (if needed)
```
@.cursor/rules/README.md Create a modular rule for [feature]-specific patterns
```

**Step 3: Document Feature**
```
@docs/ Document the [feature] module including [API/usage/architecture]
```

**Step 4: Add Tests**
```
@.cursor/rules/testing.md Create tests for the [feature] module
```

---

## Tips for Using Prompts

### For Users

1. **Replace placeholders** - Change `[text in brackets]` to your specific needs
2. **Combine prompts** - Chain multiple prompts for complex tasks
3. **Iterate** - Start with basic prompt, refine based on results
4. **Reference context** - Add `@file.ext` references for more context

### For AI Agents

1. **Suggest relevant prompts** - Based on user's task, recommend specific prompt IDs
2. **Explain expected outcome** - Tell users what the prompt will do
3. **Customize on the fly** - Adapt prompt text to user's specific situation
4. **Chain prompts** - For complex tasks, suggest multi-step workflows
5. **Reference this file** - `@PROMPTS.md` when user asks "how do I customize..."

---

## Adding New Prompts

When you identify a common customization pattern:

1. **Add it here** with:
   - Unique ID
   - When to use
   - Expected outcome
   - The prompt itself
   - Follow-up actions

2. **Update sections**:
   - Add to appropriate category
   - Update table of contents if needed

3. **Keep it structured**:
   - Follow the format above
   - Make prompts copy-paste ready
   - Include clear placeholders

---

**For AI Agents:** Use these prompts as templates. Adapt them to the user's specific context and needs. When users ask "how do I set up...", "how do I add...", or "how do I configure...", reference the relevant prompt from this file.

