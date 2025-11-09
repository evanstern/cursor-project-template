# Contributing Guidelines

Thank you for considering contributing to this project!

> **Note:** This is a skeleton. Customize these guidelines for your specific project.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Development Process](#development-process)
- [Submitting Changes](#submitting-changes)
- [Coding Standards](#coding-standards)
- [Testing](#testing)
- [Documentation](#documentation)

## Code of Conduct

### Our Pledge

We are committed to providing a welcoming and inclusive environment for all contributors.

### Our Standards

**Positive behavior includes:**
- Using welcoming and inclusive language
- Respecting differing viewpoints
- Accepting constructive criticism gracefully
- Focusing on what's best for the project
- Showing empathy towards others

**Unacceptable behavior includes:**
- Harassment or discriminatory language
- Personal attacks
- Trolling or insulting comments
- Publishing others' private information
- Other conduct inappropriate in a professional setting

### Enforcement

Project maintainers are responsible for enforcing these standards. Unacceptable behavior can be reported to [contact method].

## Getting Started

### Prerequisites

List prerequisites here:
- [Tool/dependency 1 with version]
<!-- Example: Node.js 18+ and npm 9+ -->
- [Tool/dependency 2 with version]
<!-- Example: Git 2.30+ -->
- [Access requirements]
<!-- Example: GitHub account with repository access -->

### Setting Up Development Environment

```bash
# 1. Clone the repository
git clone https://github.com/[user]/[repo].git
cd [repo]

# 2. Install dependencies
[your installation command]
<!-- Example: npm install -->

# 3. Copy environment template
cp .env.example .env
# Edit .env with your local settings
<!-- Example values in comments within .env.example -->

# 4. Run setup script (if applicable)
[your setup command]
<!-- Example: npm run setup -->

# 5. Verify setup
[your verification command]
<!-- Example: npm test --verbose -->
```

### First Time Setup

- [ ] Read project documentation in `docs/`
- [ ] Familiarize yourself with the codebase structure
- [ ] Review coding standards in `.cursorrules`
- [ ] Set up your development tools
- [ ] Run the test suite to ensure everything works

## Development Process

### Before Starting Work

1. **Check for existing work**
   - Search existing issues and PRs
   - Ensure no one else is working on it

2. **Create or claim an issue**
   - For new features, create an issue first
   - For bugs, ensure there's an issue to track
   - Comment that you're working on it

3. **Discuss approach** (for large changes)
   - Comment on the issue with your plan
   - Get feedback before implementing
   - Align with project architecture

### Git Workflow

This project uses **[trunk-based development / git-flow / other]**.

#### Branch Naming

```
feature/issue-123-short-description
<!-- Example: feature/issue-456-add-user-authentication -->
fix/issue-456-bug-description
<!-- Example: fix/issue-789-null-pointer-in-login -->
docs/update-readme
<!-- Example: docs/add-api-documentation -->
refactor/improve-auth
<!-- Example: refactor/extract-validation-logic -->
```

#### Working on Changes

```bash
# 1. Create a branch
git checkout -b feature/issue-123-add-feature

# 2. Make your changes
# Write code, add tests, update docs

# 3. Commit frequently
git add [files]
git commit -m "type(scope): description"

# 4. Keep branch updated
git fetch origin
git rebase origin/main

# 5. Push your branch
git push origin feature/issue-123-add-feature
```

### Commit Messages

Follow [Conventional Commits](https://www.conventionalcommits.org/):

**Format:**
```
type(scope): subject

body (optional)

footer (optional)
```

**Types:**
- `feat` - New feature
- `fix` - Bug fix
- `docs` - Documentation changes
- `style` - Code style changes (formatting, no logic change)
- `refactor` - Code refactoring
- `test` - Adding or updating tests
- `chore` - Maintenance tasks

**Examples:**
```bash
feat(auth): add password reset functionality
<!-- New feature in auth module -->
fix(api): handle null user in getUserData
<!-- Bug fix in API -->
docs(readme): update installation instructions
<!-- Documentation change -->
test(auth): add tests for login flow
<!-- Adding tests -->
```

## Submitting Changes

### Pull Request Process

1. **Ensure quality**
   - [ ] All tests pass
   - [ ] Linter shows no errors
   - [ ] Code is documented
   - [ ] No console.log or debug code

2. **Update documentation**
   - [ ] Update README if needed
   - [ ] Update relevant docs in `docs/`
   - [ ] Add/update comments in code

3. **Create pull request**
   - Use PR template (if provided)
   - Reference related issues
   - Provide clear description
   - Add screenshots (for UI changes)

4. **PR description should include:**
   - What changes were made
   - Why they were made
   - How to test them
   - Any breaking changes
   - Related issues (e.g., "Fixes #123")

### Pull Request Template

```markdown
## Description
[Brief description of changes]

## Motivation
[Why are these changes needed?]

## Changes
- [Change 1]
- [Change 2]

## Testing
[How to test these changes]

## Screenshots (if applicable)
[Add screenshots for UI changes]

## Checklist
- [ ] Tests pass
- [ ] Linter passes
- [ ] Documentation updated
- [ ] No breaking changes (or documented if so)

## Related Issues
Fixes #[issue number]
```

### Review Process

1. **Wait for review**
   - Maintainers will review your PR
   - Be patient - reviews take time

2. **Address feedback**
   - Make requested changes
   - Push new commits to your branch
   - Respond to review comments

3. **Approval and merge**
   - Once approved, a maintainer will merge
   - Your branch will be deleted after merge

## Coding Standards

### General Principles

- **Write clear, readable code** - Code is read more than written
- **Keep functions small** - Each function should do one thing
- **Use meaningful names** - Names should reveal intent
- **Don't repeat yourself (DRY)** - Extract common functionality
- **YAGNI** - You aren't gonna need it (don't over-engineer)

### Language-Specific Standards

Refer to:
- Core rules: `.cursorrules`
- Modular rules: `.cursor/rules/`
- [Add links to style guides]

### Code Review Checklist

Reviewers will check for:

- [ ] **Correctness** - Code does what it's supposed to
- [ ] **Tests** - Adequate test coverage
- [ ] **Documentation** - Code is well-documented
- [ ] **Style** - Follows project conventions
- [ ] **Performance** - No obvious performance issues
- [ ] **Security** - No security vulnerabilities
- [ ] **Maintainability** - Code is easy to understand and modify

## Testing

### Running Tests

```bash
# Run all tests
[your test command]

# Run specific test file
[your specific test command]

# Run with coverage
[your coverage command]
```

### Writing Tests

- All new features require tests
- Bug fixes should include regression tests
- Aim for [X]% code coverage
- Follow testing guidelines in `.cursor/rules/testing.md`

### Test Standards

- **Unit tests** - Test individual functions/modules
- **Integration tests** - Test component interaction
- **E2E tests** - Test user workflows (when applicable)

See `docs/workflows/testing.md` for testing workflow.

## Documentation

### Code Documentation

- Document all public APIs
- Use [JSDoc / docstrings / etc.]
- Follow standards in `.cursor/rules/documentation.md`

### Project Documentation

Update docs when:
- Adding new features
- Changing architecture
- Modifying APIs
- Updating dependencies

Documentation lives in:
- `README.md` - Project overview
- `docs/` - Detailed documentation
- Code comments - Implementation details

## Questions?

- **Documentation**: Check `docs/` directory
- **Cursor AI**: See `docs/CURSOR.md` for AI-assisted development
- **Issues**: Open a new issue with your question
- **Discussions**: Use GitHub Discussions for general questions

## Recognition

Contributors will be recognized in:
- GitHub contributors list
- Release notes (for significant contributions)
- [Other recognition method]

## License

By contributing, you agree that your contributions will be licensed under the same license as the project (see LICENSE file).

---

**Thank you for contributing!** Your efforts help make this project better for everyone.

