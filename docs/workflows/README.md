# Development Workflows

This directory contains documentation for common development workflows.

## What Are Workflows?

Workflows are step-by-step guides for common development tasks. They help ensure consistency and completeness when performing routine activities.

## Why Workflows?

### For Developers
- **Consistency** - Everyone follows the same process
- **Completeness** - Don't forget important steps
- **Onboarding** - New team members learn the process
- **Efficiency** - No need to remember every detail

### For AI Assistants
- **Guided Execution** - Clear steps to follow
- **Context-Aware** - Understand the full process
- **Quality Assurance** - Built-in quality checks
- **Automation** - Can execute multi-step processes

## Using Workflows

### In Cursor

Reference workflows with `@` when you need guidance:

```
@docs/workflows/commit.md Help me commit my changes
```

```
@docs/workflows/feature.md Guide me through adding a new feature
```

```
@docs/workflows/bugfix.md I need to fix a bug
```

The AI will read the workflow and guide you through each step.

### Manual Use

You can also use workflows as checklists:
1. Open the workflow document
2. Follow steps in order
3. Check off completed steps
4. Ensure quality gates are met

## Workflow Structure

Each workflow should follow this structure:

```markdown
# Workflow Name

Brief description of what this workflow accomplishes.

## When to Use

[When should this workflow be used?]

## Prerequisites

- [Requirement 1]
- [Requirement 2]

## Steps

### 1. [First Step]

Description of what to do.

**Actions:**
- [Specific action 1]
- [Specific action 2]

**Success Criteria:**
- [How to know this step succeeded]

**Common Issues:**
- [Issue and solution]

### 2. [Second Step]

[Same structure as step 1]

## Verification

- [ ] [Check 1]
- [ ] [Check 2]

## Troubleshooting

Common problems and solutions.

## Related Workflows

- [Link to related workflow]
```

## Common Workflows to Add

Here are workflows commonly needed in projects:

### Development Workflows

**Feature Development (`feature.md`)**
- Planning a feature
- Creating feature branch (if used)
- Implementation steps
- Testing requirements
- Documentation needs
- Review process
- Merge/deploy

**Bug Fix (`bugfix.md`)**
- Reproducing the bug
- Writing a failing test
- Implementing the fix
- Verifying the fix
- Regression testing
- Documentation updates

**Refactoring (`refactor.md`)**
- Identifying refactoring opportunity
- Planning the refactor
- Maintaining tests
- Step-by-step refactoring
- Verification
- Documentation

### Git Workflows

**Committing (`commit.md`)**
- Pre-commit checks (lint, tests)
- Staging changes
- Writing commit messages
- Commit conventions
- Push guidelines

**Pull Request (`pull-request.md`)**
- Creating PRs
- PR description template
- Requesting reviewers
- Addressing feedback
- Merging strategy

**Release (`release.md`)**
- Version bumping
- Changelog generation
- Tag creation
- Release notes
- Deployment

### Quality Workflows

**Code Review (`code-review.md`)**
- Review checklist
- What to look for
- How to give feedback
- Approval criteria

**Testing (`testing.md`)**
- Running tests locally
- Writing new tests
- Test coverage checks
- E2E testing
- Manual testing checklist

### Documentation Workflows

**API Documentation (`api-docs.md`)**
- Documenting endpoints
- Request/response examples
- Error documentation
- Keeping docs in sync

**Architecture Documentation (`arch-docs.md`)**
- When to update architecture
- What to include
- Diagram creation
- Decision records

## Creating New Workflows

### 1. Identify the Need

Create a workflow when:
- A process is repeated frequently
- New team members ask how to do something
- Mistakes happen in a process
- Quality varies in how something is done

### 2. Document Current State

Write down how the process is currently done:
- Ask experienced team members
- Observe the process
- Note variations in how it's done

### 3. Define Best Practice

Determine the ideal process:
- What works well?
- What should be added?
- What should be removed?
- What quality checks are needed?

### 4. Create the Workflow

Use the template structure above:
- Clear steps
- Specific actions
- Success criteria
- Troubleshooting

### 5. Test and Iterate

- Have someone follow the workflow
- Gather feedback
- Refine based on experience
- Keep it updated

## Workflow Best Practices

### Keep It Actionable

Each step should be clear and specific:

❌ **Vague:** "Make sure the code is good"  
✅ **Specific:** "Run linter with `npm run lint` and fix all errors"

### Include Quality Gates

Add checkpoints to ensure quality:

```markdown
## Quality Checks

Before proceeding, verify:
- [ ] All tests pass
- [ ] Linter reports no errors
- [ ] Code review is approved
- [ ] Documentation is updated
```

### Make It Discoverable

- Use clear names
- Add to this README
- Reference in related docs
- Include examples

### Keep It Current

- Review workflows periodically
- Update when process changes
- Remove outdated workflows
- Gather team feedback

## Automating Workflows

Some workflow steps can be automated:

### Pre-commit Hooks

```bash
# .git/hooks/pre-commit
npm run lint
npm run test
```

### GitHub Actions

```yaml
# .github/workflows/pr-checks.yml
name: PR Checks
on: [pull_request]
jobs:
  checks:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - run: npm run lint
      - run: npm run test
```

### Makefile

```makefile
.PHONY: commit
commit:
	npm run lint
	npm run test
	git add -p
	git commit
```

### Scripts

```bash
# scripts/commit.sh
#!/bin/bash
npm run lint || exit 1
npm run test || exit 1
git add -p
git commit
```

## Using Workflows with Cursor

### Guided Execution

Ask Cursor to guide you through a workflow:

```
@docs/workflows/feature.md I want to add a new feature for [description]
```

The AI will:
1. Read the workflow
2. Understand your context
3. Guide you step-by-step
4. Perform actions where appropriate
5. Verify completion

### Workflow Adaptation

Workflows can be adapted for specific situations:

```
@docs/workflows/commit.md Help me commit, but skip tests since they're already passing
```

### Workflow Chaining

Combine multiple workflows:

```
@docs/workflows/feature.md @docs/workflows/commit.md
Create feature [X], then help me commit it properly
```

## Example Workflows

### Example: Simple Commit Workflow

```markdown
# Commit Workflow

## Steps

### 1. Review Changes
\`\`\`bash
git status
git diff
\`\`\`

### 2. Run Quality Checks
\`\`\`bash
npm run lint
npm run test
\`\`\`

### 3. Stage Changes
\`\`\`bash
git add [files]
\`\`\`

### 4. Commit with Conventional Message
Format: `type(scope): subject`

Types: feat, fix, docs, style, refactor, test, chore

Example:
\`\`\`bash
git commit -m "feat(auth): add token refresh"
\`\`\`

### 5. Push
\`\`\`bash
git push
\`\`\`
```

## Workflow Ideas

Common workflows teams find useful:

### Development
- `setup.md` - Initial project setup
- `feature.md` - Feature development
- `bugfix.md` - Bug fixing process
- `hotfix.md` - Emergency fixes
- `refactor.md` - Refactoring process

### Git & Deployment
- `commit.md` - Committing changes
- `branch.md` - Branch management
- `merge.md` - Merging strategy
- `rebase.md` - Rebase workflow
- `release.md` - Release process
- `rollback.md` - Rollback procedure

### Quality
- `code-review.md` - Review process
- `testing.md` - Testing guidelines
- `debugging.md` - Debugging process
- `performance.md` - Performance testing

### Documentation
- `api-docs.md` - API documentation
- `changelog.md` - Changelog management
- `adr.md` - Architecture decision records

### Maintenance
- `dependency-update.md` - Updating dependencies
- `security-patch.md` - Security updates
- `migration.md` - Data/code migrations

## Resources

- [Trunk-Based Development](https://trunkbaseddevelopment.com/)
- [Conventional Commits](https://www.conventionalcommits.org/)
- [GitHub Flow](https://guides.github.com/introduction/flow/)
- [Git Flow](https://nvie.com/posts/a-successful-git-branching-model/)

## Contributing

When adding new workflows:
1. Follow the template structure
2. Be specific and actionable
3. Include examples
4. Test with team members
5. Update this README

---

**Remember:** Workflows should help, not hinder. Keep them focused, actionable, and up-to-date. They're living documents that evolve with your project.

