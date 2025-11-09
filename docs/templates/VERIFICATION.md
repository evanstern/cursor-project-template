# Setup Verification Checklist

<!-- AI: Customize this template for user's specific stack, then save to project root as VERIFICATION.md -->
<!-- USER: Delete this file after all verifications pass -->

## Purpose

Verify your project setup works before starting development. Check each box as you verify it works.

**Time required:** 20-30 minutes

---

## Quick Verification (Essential)

These MUST pass before considering setup complete:

- [ ] **Git works:** `git status` runs without errors
- [ ] **Dependencies install:** `[your install command]` completes successfully
- [ ] **Linter runs:** `[your lint command]` executes without errors
- [ ] **Tests run:** `[your test command]` executes (even if no tests yet)
- [ ] **Build succeeds:** `[your build command]` completes (if applicable)
- [ ] **Dev server starts:** `[your dev command]` runs and accessible
- [ ] **README is customized:** No template text remains
- [ ] **Documentation complete:** ARCHITECTURE.md and CONTRIBUTING.md filled in

**If any fail, stop and fix before continuing.**

---

## Detailed Verification

### 1. Repository & Files

- [ ] `git status` works
- [ ] README.md describes THIS project (not template)
- [ ] LICENSE has correct copyright holder
- [ ] .gitignore appropriate for your stack
- [ ] .cursorignore appropriate for your stack

**Commands:**
```bash
git status
cat README.md | head -20    # Check it's customized
```

---

### 2. Package Management

- [ ] Package file exists and is valid
- [ ] Project name is correct in package file
- [ ] Dependencies are listed
- [ ] Scripts/commands are defined

**Commands:**
```bash
# Node.js
npm pkg get name
npm pkg get version

# Python
cat requirements.txt

# Go
go list

# Rust
cargo check
```

---

### 3. Dependencies

- [ ] Dependencies install without errors
- [ ] No security vulnerabilities (or documented if accepted)
- [ ] Lock file created (if applicable)

**Commands:**
```bash
# Node.js
npm install
npm audit

# Python
pip install -r requirements.txt
pip check

# Go
go mod download
go mod verify

# Rust
cargo build
cargo audit
```

---

### 4. Development Environment

#### Linting
- [ ] Linter is installed
- [ ] Linter config exists and is valid
- [ ] Linter runs without errors on initial code
- [ ] IDE shows linting errors inline (if configured)

**Commands:**
```bash
[Your lint command]
# Examples:
# npm run lint
# eslint .
# pylint src/
# golangci-lint run
# cargo clippy
```

#### Formatting
- [ ] Formatter is installed
- [ ] Formatter config exists
- [ ] Formatter runs without errors
- [ ] Format-on-save works (if configured)

**Commands:**
```bash
[Your format command]
# Examples:
# npm run format
# prettier --check .
# black --check .
# gofmt -l .
# cargo fmt -- --check
```

#### Type Checking (if applicable)
- [ ] Type checker runs
- [ ] No type errors in initial code
- [ ] IDE provides type hints

**Commands:**
```bash
[Your type check command]
# Examples:
# tsc --noEmit
# mypy src/
# cargo check
```

---

### 5. Testing

- [ ] Test framework is installed
- [ ] Test config exists and is valid
- [ ] Example tests exist
- [ ] Tests run successfully
- [ ] Test coverage generates (if configured)

**Commands:**
```bash
[Your test command]
# Examples:
# npm test
# jest
# pytest
# go test ./...
# cargo test
```

---

### 6. Building (if applicable)

- [ ] Build command runs without errors
- [ ] Build artifacts created in expected location
- [ ] Build artifacts are in .gitignore
- [ ] Build output is valid

**Commands:**
```bash
[Your build command]
# Examples:
# npm run build
# tsc
# python setup.py build
# go build
# cargo build --release

# Check build output
ls -la [build directory]
```

---

### 7. Development Server

- [ ] Dev server starts without errors
- [ ] Server runs on expected port
- [ ] Can access in browser/client (if applicable)
- [ ] Hot reload works (if applicable)
- [ ] No console errors

**Commands:**
```bash
[Your dev command]
# Examples:
# npm run dev
# python manage.py runserver
# go run main.go
# cargo run
```

**Manual check:**
- [ ] Visit http://localhost:[PORT]
- [ ] Application loads/responds
- [ ] Make a small code change - hot reload works

---

### 8. Documentation

- [ ] ARCHITECTURE.md is filled in (no skeleton text)
- [ ] CONTRIBUTING.md has actionable setup steps
- [ ] All docs in docs/ are either filled in or removed
- [ ] docs/README.md indexes all documentation
- [ ] Initial ADR created (001-initial-setup.md)

**Commands:**
```bash
# Check for template placeholders
grep -r "to-be-set" docs/
grep -r "skeleton" docs/
# Should return nothing or only in templates/

# Verify ADR exists
ls docs/decisions/
```

---

### 9. Cursor Rules

- [ ] .cursorrules is customized (not just template)
- [ ] Modular rules created in .cursor/rules/ (if needed)
- [ ] Glob patterns match your file structure
- [ ] Can reference rules with @

**Manual check:**
- [ ] In Cursor: `@.cursor/rules/testing.md` - does it load?
- [ ] Edit a test file - is testing rule auto-applied?
- [ ] Rules mention YOUR project specifics

---

## Optional Verifications

Only check these if you're using these features:

### Docker (Skip if not using)

- [ ] Docker is installed: `docker --version`
- [ ] Dockerfile exists and is valid
- [ ] docker-compose.yml exists (if using)
- [ ] Docker builds successfully: `docker build -t test .`
- [ ] Containers start: `docker-compose up -d`
- [ ] Services are accessible
- [ ] No error logs: `docker-compose logs`

---

### Database (Skip if not using)

- [ ] Database server is running
- [ ] Connection string correct in .env
- [ ] Can connect to database
- [ ] Migrations run (if applicable): `[your migrate command]`
- [ ] Seed data loads (if applicable)

**Commands:**
```bash
# Test connection
psql $DATABASE_URL -c "SELECT 1;"    # PostgreSQL
mysql -h localhost -u user -p -e "SELECT 1;"  # MySQL
mongo --eval "db.version()"          # MongoDB
```

---

### Monorepo (Skip if not using)

- [ ] Monorepo tool is installed
- [ ] Workspace config is valid
- [ ] Can build all packages: `[your workspace build command]`
- [ ] Internal dependencies resolve correctly
- [ ] Workspace commands work

**Commands:**
```bash
# Build all
turbo run build
# or: nx run-many --target=build --all
# or: pnpm -r build

# List workspaces
pnpm list -r --depth 0
# or: npm workspaces list
```

---

### CI/CD (Skip if not configured)

- [ ] CI config file exists and is valid
- [ ] Can trigger CI manually (if pushed to remote)
- [ ] All jobs pass

**Validation:**
```bash
# GitHub Actions (with act)
act -l

# GitLab CI
gitlab-ci-lint .gitlab-ci.yml
```

---

## Verification Complete

Once all essential checks pass:

### Final Steps

- [ ] All "Quick Verification" items pass ✅
- [ ] All "Detailed Verification" items pass ✅
- [ ] Optional items pass (for features you're using) ✅
- [ ] `.cursor/template.json` updated with verification status:
  ```json
  {
    "customization": {"verification_completed": true},
    "setup": {"verification_passed": true}
  }
  ```

### Clean Up

- [ ] Delete this file: `rm VERIFICATION.md`
- [ ] Or move to archive: `mv VERIFICATION.md docs/archive/`

### Make Initial Commit

```bash
git add .
git commit -m "Initial project setup from cursor-project-template

Verified and working:
- [List key components verified]

See docs/decisions/001-initial-setup.md for details."
```

---

## If Verification Fails

### General Troubleshooting

1. **Read error messages carefully** - They often point directly to the problem
2. **Check typos** - Configuration files, paths, variable names
3. **Verify prerequisites** - Correct runtime/language version?
4. **Clean and retry** - Remove dependencies and reinstall
5. **Check documentation** - `@docs/TROUBLESHOOTING.md`

### Common Issues

**Dependencies won't install:**
- Check internet connection
- Verify package registry is accessible
- Try clearing cache
- Check for conflicting versions

**Linter/Tests failing:**
- Check configuration file syntax
- Verify file paths are correct
- Look for typos in config
- Ensure dependencies installed

**Build failing:**
- Check for syntax errors
- Verify all imports resolve
- Check configuration is valid
- Ensure build directory exists

**Dev server won't start:**
- Check port isn't already in use
- Verify environment variables set
- Look for missing dependencies
- Check for errors in startup code

### Get Help

```
@docs/TROUBLESHOOTING.md I'm getting this error: [error message]
```

---

## For AI Agents

When creating this file for a user:

1. **Replace all `[your command]` placeholders** with actual commands for their stack
2. **Remove sections** that don't apply (e.g., Docker if not using)
3. **Add project-specific checks** unique to their setup
4. **Keep commands copy-paste ready** - no placeholders in final version
5. **Mark optional sections clearly** - "Skip if not using"

Example customization:
```
Before: [Your test command]
After (Node.js): npm test
After (Python): pytest
After (Go): go test ./...
```

---

**Remember:** This checklist catches issues BEFORE you start developing. Take the time to verify everything works—it saves hours of debugging later!
