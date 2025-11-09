# Troubleshooting Guide

<!-- For AI: Load this for project-wide troubleshooting, not just Cursor-specific issues -->

Common issues and solutions for this project.

## Setup Issues

### Problem: Template Not Customized

**Symptoms:**
- `.cursor/template.json` shows `"name": "to-be-set"`
- No language-specific files (package.json, requirements.txt, etc.)
- Documentation still has placeholders

**Solution:**
Use setup prompts from `@PROMPTS.md`:
```
@PROMPTS.md @docs/PROJECT_SETUP.md Set up this project for [language/framework]
```

### Problem: Dependencies Not Installing

**Symptoms:**
- Package manager errors
- Missing dependencies

**Solution:**
1. Check you have the right package manager installed
2. Check for version conflicts
3. Clear cache and retry:
```bash
# Node.js
rm -rf node_modules package-lock.json
npm install

# Python
pip install --upgrade pip
pip install -r requirements.txt
```

### Problem: Environment Variables Missing

**Symptoms:**
- App crashes on startup
- "Environment variable not found" errors

**Solution:**
1. Copy `.env.example` to `.env`
2. Fill in required values
3. Check `.env` is in `.gitignore`

---

## Cursor-Specific Issues

> **Note:** For detailed Cursor troubleshooting, see `@docs/cursor/troubleshooting.md`

### Quick Fixes

**AI not following rules:**
→ See `@docs/cursor/troubleshooting.md` → "AI Not Following Rules"

**Too much context loaded:**
→ See `@docs/cursor/troubleshooting.md` → "Context Overload"

**Changes too broad:**
→ See `@docs/cursor/troubleshooting.md` → "Changes Too Broad"

---

## Build Issues

### Problem: Build Fails

**Common causes:**
- Type errors
- Missing dependencies
- Configuration errors

**Solution:**
1. Check error message carefully
2. Verify all dependencies installed
3. Check configuration files
4. Ask: `@codebase what could cause this build error: [error message]`

### Problem: Tests Failing

**Solution:**
1. Run tests locally to reproduce
2. Check if tests are outdated
3. Verify test data/fixtures
4. Ask: `@tests/ why are these tests failing?`

---

## Documentation Issues

### Problem: Documentation Out of Date

**Solution:**
1. Review changed code
2. Update relevant docs
3. Check related documentation
4. Update `@.cursor/template.json` if needed

### Problem: Can't Find Documentation

**Solution:**
1. Check `@.cursor/MANIFEST.md` - lists all documentation
2. Check `@docs/README.md` - documentation index
3. Use `@codebase [topic]` to search

---

## Rules Issues

### Problem: Rules Not Being Applied

**Solution:**
See `@docs/cursor/troubleshooting.md` → "Rules Not Being Applied"

Also check:
- Is rule file in `.cursor/rules/`?
- Is YAML frontmatter valid? (Check `@.cursor/rules/SCHEMA.md`)
- Do globs match your files?

### Problem: Conflicting Rules

**Solution:**
1. Identify conflicting rules
2. Check which is more specific
3. Update or consolidate rules
4. Document the decision

---

## Git/Version Control Issues

### Problem: Merge Conflicts

**Solution:**
1. Identify conflicting files
2. Understand both changes
3. Resolve conflicts keeping both intentions
4. Test after resolving
5. Ask: `Help me resolve merge conflict in @file.ts`

### Problem: Commit Message Format Wrong

**Solution:**
Follow conventional commits format:
```
type(scope): subject

feat: new feature
fix: bug fix
docs: documentation
refactor: code refactoring
test: adding tests
chore: maintenance
```

Reference: `@.cursorrules` for project conventions

---

## Performance Issues

### Problem: Slow Application

**Solution:**
1. Profile the application
2. Identify bottlenecks
3. Check database queries
4. Check for memory leaks
5. Ask: `@codebase what could cause performance issues in [area]?`

### Problem: Large Bundle Size

**Solution:**
1. Analyze bundle
2. Check for duplicate dependencies
3. Implement code splitting
4. Remove unused imports

---

## Testing Issues

### Problem: Tests Pass Locally but Fail in CI

**Solution:**
1. Check environment differences
2. Check for timing issues
3. Check for hardcoded paths
4. Check test isolation

### Problem: Flaky Tests

**Solution:**
1. Identify which tests are flaky
2. Check for timing dependencies
3. Check for shared state
4. Add proper test isolation
5. Reference: `@.cursor/rules/testing.md`

---

## Deployment Issues

### Problem: Deployment Fails

**Solution:**
1. Check deployment logs
2. Verify environment variables
3. Check build output
4. Verify dependencies match
5. Check deployment configuration

---

## Getting Help

### 1. Check Documentation

Start here:
- `@.cursor/MANIFEST.md` - What exists in the project
- `@docs/README.md` - Documentation index
- `@docs/ARCHITECTURE.md` - System architecture
- `@docs/CONTRIBUTING.md` - Contribution guidelines

### 2. Search Codebase

Use semantic search:
```
@codebase how is [feature] implemented?
@codebase where is [functionality] handled?
```

### 3. Ask Cursor AI

Provide context:
```
@relevant/files.ts

I'm experiencing [issue]
Expected: [what should happen]
Actual: [what's happening]
Error: [error message if any]
```

### 4. Check Related Files

Look at:
- Similar working code
- Tests for the feature
- Related documentation

### 5. Review Recent Changes

```bash
git log --oneline -10
git diff HEAD~5
```

---

## Common Error Messages

### "Cannot find module"

**Cause:** Missing dependency or wrong import path

**Solution:**
1. Check if dependency is installed
2. Verify import path is correct
3. Check file actually exists
4. Check case sensitivity

### "Type 'X' is not assignable to type 'Y'"

**Cause:** Type mismatch

**Solution:**
1. Check type definitions in `@src/types/`
2. Verify data structure matches type
3. Add type guards if needed
4. Ask: `@src/types/ help fix type error in @problematic/file.ts`

### "Cannot read property 'X' of undefined"

**Cause:** Accessing property of undefined/null value

**Solution:**
1. Add null checks
2. Use optional chaining `?.`
3. Use nullish coalescing `??`
4. Verify data exists before accessing

---

## Diagnostic Checklist

When debugging issues:

- [ ] Can you reproduce the issue consistently?
- [ ] What changed recently?
- [ ] Does it work in a clean environment?
- [ ] Are there error messages? (check logs)
- [ ] Have you checked relevant documentation?
- [ ] Have you searched the codebase for similar code?
- [ ] Have you asked Cursor AI with proper context?

---

## Preventive Measures

### Before Committing

- [ ] Tests pass locally
- [ ] Linter passes
- [ ] Documentation updated
- [ ] No debug code left in
- [ ] Reviewed your own changes

### Before Deploying

- [ ] All tests pass
- [ ] Build succeeds
- [ ] Environment variables configured
- [ ] Database migrations applied
- [ ] Monitoring in place

---

**For AI Agents:** Use this to help users diagnose and resolve project-wide issues. For Cursor-specific issues, refer to `@docs/cursor/troubleshooting.md`.

**See also:**
- `@docs/cursor/troubleshooting.md` - Cursor-specific issues
- `@docs/ARCHITECTURE.md` - Understanding the system
- `@docs/CONTRIBUTING.md` - Development guidelines
- `@.cursor/MANIFEST.md` - Project map

