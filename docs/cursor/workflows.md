# Common Workflows

<!-- For AI: Load this when users need step-by-step guidance for common tasks -->

This guide provides step-by-step workflows for common development tasks with Cursor.

## Workflow: Starting a New Feature

**Goal:** Implement a new feature from scratch

### Steps

**1. [AI Panel] Plan the Approach**
```
@docs/ARCHITECTURE.md @src/services/UserService.ts

I need to add team management. How should I structure this?
```

**2. [AI Panel] Discuss Implementation Details**
```
What data models do I need?
Should this be a separate service?
```

**3. [AI Panel] Implement the Feature**
```
Following the patterns in @src/services/UserService.ts,
create a TeamService with CRUD operations in src/services/TeamService.ts
```

**4. [Inline Edit] Add Documentation**
```
Select: TeamService class
Edit: @.cursor/rules/documentation.md add comprehensive JSDoc
```

**5. [AI Panel] Add Tests**
```
@.cursor/rules/testing.md @src/services/TeamService.ts
Create comprehensive tests in src/services/TeamService.test.ts
```

**6. [Terminal] Run Tests**
```
npm test
```

**7. [AI Panel] Review**
```
@src/services/TeamService.ts review this implementation for:
- Correctness
- Error handling
- Edge cases
- Performance
```

**8. Commit Changes**
```
git add src/services/TeamService.ts src/services/TeamService.test.ts
git commit -m "feat(teams): add team management service"
```

---

## Workflow: Fixing a Bug

**Goal:** Fix a bug efficiently

### Steps

**1. [AI Panel] Understand the Issue**
```
@src/components/LoginForm.tsx

The email validation is failing for valid emails with + signs
```

**2. [AI Panel] Get Explanation**
```
Why would the current validation reject emails with + signs?
```

**3. [Inline Edit] Write Failing Test**
```
@tests/LoginForm.test.tsx

Add a test for email with + sign that should pass but currently fails
```

**4. [Terminal] Verify Test Fails**
```
npm test LoginForm
```

**5. [Inline Edit] Fix the Issue**
```
Select: email validation regex
Edit: Update to allow + signs in email addresses
```

**6. [Terminal] Verify Test Passes**
```
npm test LoginForm
```

**7. [AI Panel] Check for Similar Issues**
```
@codebase are there other places where email validation might have the same issue?
```

**8. Commit the Fix**
```
git add src/components/LoginForm.tsx tests/LoginForm.test.tsx
git commit -m "fix(auth): allow + in email addresses"
```

---

## Workflow: Refactoring Code

**Goal:** Improve code structure safely

### Steps

**1. Ensure Tests Exist**
```
@tests/ do we have tests for @src/UserManager.ts?
```

If not, add them first.

**2. [AI Panel] Plan Refactoring**
```
@src/UserManager.ts

This class is doing too much. How can I refactor it following
@docs/ARCHITECTURE.md patterns?
```

**3. [AI Panel] Get Detailed Plan**
```
Walk me through the refactoring step by step
```

**4. [AI Panel] Extract First Component**
```
@src/UserManager.ts

Extract the database logic into a new UserRepository class
in src/repositories/UserRepository.ts
```

**5. [Terminal] Run Tests**
```
npm test
```

**6. [AI Panel] Extract Second Component**
```
@src/UserManager.ts

Extract the validation logic into src/validators/UserValidator.ts
```

**7. [Terminal] Run Tests**
```
npm test
```

**8. [AI Panel] Review Final Result**
```
@src/UserManager.ts @src/repositories/UserRepository.ts @src/validators/UserValidator.ts

Review the refactored code for:
- Separation of concerns
- Maintainability
- Any remaining issues
```

**9. Commit Changes**
```
git add src/
git commit -m "refactor(users): extract repository and validator"
```

---

## Workflow: Adding Documentation

**Goal:** Document code thoroughly

### Steps

**1. [Inline Edit] Add Function Documentation**
```
Select: function calculateTotal() { ... }
Edit: @.cursor/rules/documentation.md add comprehensive JSDoc
```

**2. [Inline Edit] Add Class Documentation**
```
Select: class UserService { ... }
Edit: Add class-level JSDoc with examples
```

**3. [Inline Edit] Document Types**
```
Select: interface User { ... }
Edit: Add property documentation
```

**4. [AI Panel] Create Module Documentation**
```
@.cursor/rules/documentation.md @src/services/

Create a README.md in src/services/ documenting:
- Purpose of this directory
- How services are structured
- Examples of usage
```

**5. [AI Panel] Review Documentation**
```
@src/services/ is the documentation clear and complete?
```

---

## Workflow: Understanding Existing Code

**Goal:** Learn how unfamiliar code works

### Steps

**1. [AI Panel] Semantic Search**
```
@codebase how does authentication work?
```

**2. [AI Panel] Understand Specific File**
```
@src/auth/AuthService.ts explain how this works
```

**3. [AI Panel] Trace Flow**
```
@src/auth/AuthService.ts walk me through what happens when login() is called
```

**4. [AI Panel] Understand Patterns**
```
@src/services/ what patterns are used across these services?
```

**5. [AI Panel] Find Related Code**
```
@codebase what other code interacts with AuthService?
```

---

## Workflow: Adding Tests

**Goal:** Add comprehensive test coverage

### Steps

**1. [AI Panel] Understand What to Test**
```
@src/utils/formatters.ts @.cursor/rules/testing.md

What should I test for the formatDate function?
```

**2. [AI Panel] Create Test File**
```
@.cursor/rules/testing.md @src/utils/formatters.ts

Create comprehensive tests in src/utils/formatters.test.ts covering:
- Normal cases
- Edge cases
- Error cases
```

**3. [Terminal] Run Tests**
```
npm test formatters
```

**4. [AI Panel] Review Coverage**
```
@src/utils/formatters.test.ts

Are there any cases I'm missing?
```

**5. [Inline Edit] Add Missing Tests**
```
Add tests for [identified missing cases]
```

**6. [Terminal] Verify All Pass**
```
npm test formatters
```

---

## Workflow: Code Review

**Goal:** Review code before committing/merging

### Steps

**1. [AI Panel] Overall Review**
```
@src/features/teams/TeamService.ts

Review this new feature for:
- Correctness
- Error handling
- Security
- Performance
- Standards compliance
```

**2. [AI Panel] Check Standards**
```
@.cursorrules does this follow our coding standards?
```

**3. [AI Panel] Check Tests**
```
@tests/TeamService.test.ts

Are these tests comprehensive?
Do they follow @.cursor/rules/testing.md?
```

**4. [AI Panel] Check Documentation**
```
@src/features/teams/ is this adequately documented per @.cursor/rules/documentation.md?
```

**5. [Terminal] Run Full Test Suite**
```
npm test
```

**6. [Terminal] Run Linter**
```
npm run lint
```

---

## Workflow: Debugging

**Goal:** Fix an issue efficiently

### Steps

**1. Reproduce the Issue**
```
[Manual testing or automated test]
```

**2. [AI Panel] Analyze Error**
```
I'm getting this error:
[paste error message]

In @src/api/users.ts at line 45

What's causing this?
```

**3. [AI Panel] Understand Context**
```
@src/api/users.ts explain what this code is trying to do
```

**4. [Inline Edit] Add Logging**
```
Select: problematic section
Edit: Add console.log to debug values
```

**5. Test with Logging**
```
[Run and check logs]
```

**6. [Inline Edit] Fix Issue**
```
Select: buggy code
Edit: Fix the issue based on findings
```

**7. [Inline Edit] Remove Debug Logging**
```
Select: console.log statements
Edit: Remove debug code
```

**8. [Terminal] Verify Fix**
```
npm test
```

---

## Workflow: Performance Optimization

**Goal:** Improve code performance

### Steps

**1. [Terminal] Profile**
```
npm run profile
```

**2. [AI Panel] Analyze Results**
```
These functions are slow: [list]
@src/services/DataService.ts

How can I optimize them?
```

**3. [AI Panel] Get Specific Suggestions**
```
@src/services/DataService.ts

The fetchAll() method is slow. Suggest optimizations.
```

**4. [Inline Edit] Implement Optimization**
```
Select: slow function
Edit: Implement suggested optimization (e.g., caching, batching)
```

**5. [Terminal] Benchmark**
```
npm run benchmark
```

**6. [Terminal] Verify Tests Pass**
```
npm test
```

---

## Quick Reference

| Workflow | Primary Tools | Key Steps |
|----------|--------------|-----------|
| New Feature | Chat → Composer → Inline Edit | Plan → Implement → Polish → Test |
| Bug Fix | Chat → Inline Edit → Terminal | Understand → Fix → Verify |
| Refactor | Chat → Composer → Terminal | Plan → Extract → Test → Repeat |
| Documentation | Inline Edit → Composer | Document inline → Create guides |
| Understanding | Chat | Search → Read → Trace → Understand |
| Testing | Chat → Composer → Terminal | Plan → Create → Run → Review |
| Code Review | Chat | Review → Check → Verify |
| Debug | Chat → Inline Edit | Reproduce → Analyze → Fix → Verify |

---

**For AI Agents:** Use these workflows as templates. Adapt them based on the specific context and user's needs.

**See also:**
- [features.md](./features.md) - Tool capabilities
- [best-practices.md](./best-practices.md) - General guidance
- [troubleshooting.md](./troubleshooting.md) - When things go wrong

