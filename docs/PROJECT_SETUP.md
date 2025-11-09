# Project Setup Guide

This guide helps you customize this template for your specific project.

## Overview

This template provides universal scaffolding for Cursor-based agentic development. After creating a project from this template, follow these steps to customize it for your needs.

## Initial Setup

### 1. Clone the Template

Use GitHub's "Use this template" button, or:

```bash
git clone https://github.com/yourusername/cursor-project-template.git my-project
cd my-project
rm -rf .git
git init
```

### 2. Update Project Identity

**Update README.md:**
- Change project name
- Add project description
- Update repository URLs
- Customize Quick Start section

**Update LICENSE:**
- Add your name/organization
- Verify license type is appropriate

### 3. Configure for Your Stack

Use Cursor to help customize for your technology stack:

```
@.gitignore @.cursorignore Update these for a [Node.js/Python/Go/Rust/etc.] project
```

```
@docs/PROJECT_SETUP.md Set up this project as a [web app/API/CLI/mobile app]
```

## Customizing Rules

### Update Core Rules

**Edit `.cursorrules`:**

```
@.cursorrules Add project-specific rules for [your project type]
```

Common additions:
- Language/framework specific standards
- Naming conventions
- File structure requirements
- Required libraries/patterns

### Add Modular Rules

Create rules for specific concerns:

```
@.cursor/rules/README.md Create a rule for [API design/security/performance]
```

Examples:
- `api-design.md` - REST/GraphQL patterns
- `security.md` - Security requirements
- `database.md` - Database patterns
- `styling.md` - CSS/styling conventions

### Configure Rule Globs

Update glob patterns to match your file structure:

```yaml
---
description: Testing standards
globs:
  - '**/*.test.ts'      # TypeScript
  - '**/*_test.py'      # Python
  - '**/*_test.go'      # Go
alwaysApply: false
---
```

## Setting Up Documentation

### Fill in Core Docs

**ARCHITECTURE.md:**
```
@docs/ARCHITECTURE.md Document the [layered/microservices/monolithic] architecture
```

Add:
- System overview
- Component diagram
- Data flow
- Tech stack details
- Key design decisions

**CONTRIBUTING.md:**
```
@docs/CONTRIBUTING.md Add contribution guidelines for [your team/open source]
```

Add:
- Development setup
- Coding standards
- PR process
- Review guidelines

### Add Project-Specific Docs

Create documentation as needed:

```bash
# API Documentation
docs/API.md

# Database Schema
docs/DATABASE.md

# Deployment Guide
docs/DEPLOYMENT.md

# User Guide
docs/USER_GUIDE.md
```

Use Cursor to generate initial versions:

```
@docs/ Create API documentation based on @src/api/
```

## Setting Up Workflows

### Common Workflows to Add

Create workflow docs in `docs/workflows/`:

**Commit Workflow (`docs/workflows/commit.md`):**
- Quality checks before commit
- Commit message format
- What to include in commits

**Feature Development (`docs/workflows/feature.md`):**
- Planning features
- Implementation steps
- Testing requirements
- Documentation needs

**Bug Fix Workflow (`docs/workflows/bugfix.md`):**
- Reproducing bugs
- Writing tests
- Fixing issues
- Verification steps

Use Cursor to create workflows:

```
@docs/workflows/README.md Create a workflow for [git commits/deploys/releases]
```

## Setting Up Agents

### When to Use Agents

Create specialized agents if you have:
- Multiple platforms (web, mobile, backend)
- Specialized areas (testing, documentation, DevOps)
- Different tech stacks in one repo

### Creating Agent Specs

Create specs in `docs/agents/`:

```
@docs/agents/README.md Create an agent spec for [backend/frontend/testing]
```

Example agents:
- `BACKEND.md` - API development
- `FRONTEND.md` - UI development
- `TESTING.md` - QA and testing
- `DOCUMENTATION.md` - Docs writing
- `DEVOPS.md` - Infrastructure

## Adding Language/Framework Support

### Node.js/JavaScript/TypeScript

```bash
# Initialize package.json
npm init -y

# Add common dependencies
npm install [your dependencies]

# Add dev dependencies
npm install -D typescript @types/node [other dev deps]

# Create tsconfig.json
npx tsc --init
```

Update `.gitignore` and `.cursorignore`:
```
node_modules/
dist/
.next/
```

### Python

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows

# Create requirements.txt
touch requirements.txt

# Create setup files
touch setup.py
touch pyproject.toml
```

Update ignore files:
```
venv/
__pycache__/
*.pyc
.pytest_cache/
```

### Go

```bash
# Initialize module
go mod init github.com/username/project

# Create main.go
touch main.go
```

Update ignore files:
```
/bin/
/pkg/
```

### Rust

```bash
# Create new project
cargo init

# Or use cargo new
cargo new my-project
```

Update ignore files:
```
/target/
Cargo.lock
```

### Other Languages

Use Cursor to help:

```
Set up this project for [Java/C#/Ruby/PHP] development
```

## Setting Up Testing

### Add Test Framework

Choose and configure a testing framework:

```
@.cursor/rules/testing.md Set up [Jest/Pytest/Go testing/etc.] for this project
```

### Create Test Structure

```bash
# JavaScript/TypeScript
mkdir -p src/__tests__

# Python
mkdir -p tests

# Go
# Tests live alongside code (*_test.go)

# Rust
# Tests live in src with #[cfg(test)]
```

### Configure Test Rules

Update `.cursor/rules/testing.md` for your framework:

```
@.cursor/rules/testing.md Update for [Jest/Pytest/etc.] specifics
```

## Setting Up CI/CD

### GitHub Actions

```bash
mkdir -p .github/workflows
```

Create workflow files:

```yaml
# .github/workflows/test.yml
name: Test
on: [push, pull_request]
jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run tests
        run: [your test command]
```

### Other CI Systems

- **GitLab CI**: Create `.gitlab-ci.yml`
- **CircleCI**: Create `.circleci/config.yml`
- **Travis CI**: Create `.travis.yml`

Use Cursor to generate configs:

```
Create a GitHub Actions workflow for [testing/building/deploying]
```

## Adding Build Tools

### Common Build Tools

**Webpack/Vite (JavaScript):**
```bash
npm install -D vite
# or
npm install -D webpack webpack-cli
```

**Build Scripts (Python):**
```bash
pip install build setuptools wheel
```

**Make (Universal):**
```bash
touch Makefile
```

Use Cursor to create build configs:

```
Create a [Makefile/package.json scripts/build config] for this project
```

## Environment Configuration

### Environment Variables

Create `.env.example`:

```bash
# .env.example
DATABASE_URL=postgresql://localhost/mydb
API_KEY=your_api_key_here
DEBUG=false
```

Add to README:
```markdown
## Environment Setup

Copy `.env.example` to `.env` and fill in your values:

\`\`\`bash
cp .env.example .env
\`\`\`
```

### Configuration Files

Create config files as needed:
- `config.json` / `config.yaml`
- `config/development.json`
- `config/production.json`

## Adding Dependencies

### Document Dependencies

In README.md, add:

```markdown
## Prerequisites

- [Runtime/language] version X.Y
- [Database] version X.Y
- [Other tool] version X.Y

## Installation

\`\`\`bash
[installation commands]
\`\`\`
```

### Keep Dependencies Updated

Add scripts or tools to check for updates:
- `npm outdated` (Node.js)
- `pip list --outdated` (Python)
- `go list -u -m all` (Go)
- `cargo outdated` (Rust)

## Checklist

Use this checklist when setting up a new project:

### Essential Setup
- [ ] Update README.md with project details
- [ ] Update LICENSE with correct name/org
- [ ] Customize `.cursorrules` for your stack
- [ ] Update `.gitignore` and `.cursorignore`
- [ ] Initialize language/framework (package.json, etc.)

### Documentation
- [ ] Fill in `docs/ARCHITECTURE.md`
- [ ] Customize `docs/CONTRIBUTING.md`
- [ ] Add project-specific docs as needed
- [ ] Update `docs/README.md` with doc structure

### Rules & Workflows
- [ ] Add modular rules to `.cursor/rules/`
- [ ] Create workflows in `docs/workflows/`
- [ ] Set up agent specs if needed (multi-platform)

### Development Setup
- [ ] Configure testing framework
- [ ] Set up linting/formatting
- [ ] Add build tools
- [ ] Create `.env.example`
- [ ] Set up CI/CD

### First Commit
- [ ] Initialize git repository
- [ ] Make initial commit
- [ ] Push to remote
- [ ] Set up branch protection (if applicable)

## Getting Help

Use Cursor to help with setup:

```
@docs/PROJECT_SETUP.md I'm setting up a [type] project, help me configure [aspect]
```

Ask specific questions:
```
What dependencies should I add for a [your stack] project?
How should I structure a [your project type] project?
What testing framework works best for [your stack]?
```

## Next Steps

After initial setup:

1. **Start Coding** - Begin implementing features
2. **Iterate on Rules** - Add/refine rules as patterns emerge
3. **Build Workflows** - Create workflows for common tasks
4. **Improve Documentation** - Keep docs updated as you build

## Resources

- [Cursor Documentation](https://cursor.sh/docs)
- [GitHub Template Repositories](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-template-repository)
- Language/framework specific guides

---

**Remember:** This template is a starting point. Customize it to fit your project's needs. Use Cursor to help with the setup process!

