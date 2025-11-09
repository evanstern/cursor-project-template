---
description: Testing patterns and conventions
globs:
  - '**/*.test.ts'
  - '**/*.test.js'
  - '**/*.spec.ts'
  - '**/*.spec.js'
  - '**/*_test.py'
  - '**/*_test.go'
  - '**/*_spec.rb'
  - '**/test_*.py'
alwaysApply: false
---

<!-- For AI: This rule applies when editing test files. Defines testing patterns and best practices. -->
<!-- Related: @docs/TROUBLESHOOTING.md if tests are failing -->
<!-- Use with: Writing tests, reviewing test code -->

# Testing Standards

This rule defines testing patterns and conventions for the project.

## Purpose

Good tests:
- Verify code works as expected
- Catch regressions
- Document behavior
- Enable confident refactoring

## Test Structure

### Arrange-Act-Assert (AAA) Pattern

Structure tests in three clear phases:

```typescript
test('should calculate total with tax', () => {
  // Arrange - Set up test data
  const price = 100;
  const taxRate = 0.08;
  
  // Act - Execute the code under test
  const result = calculateTotal(price, taxRate);
  
  // Assert - Verify the result
  expect(result).toBe(108);
});
```

### Given-When-Then (BDD Style)

Alternative structure for behavioral tests:

```typescript
describe('Shopping Cart', () => {
  it('should apply discount when total exceeds threshold', () => {
    // Given a cart with items totaling $150
    const cart = new ShoppingCart();
    cart.addItem({ price: 100 });
    cart.addItem({ price: 50 });
    
    // When applying bulk discount
    const total = cart.calculateTotal();
    
    // Then discount should be applied
    expect(total).toBeLessThan(150);
  });
});
```

## Test Naming

### Descriptive Names

Test names should describe what is being tested and the expected outcome:

❌ **Bad:**
```typescript
test('test1', () => { ... });
test('it works', () => { ... });
```

✅ **Good:**
```typescript
test('should return empty array when no items match filter', () => { ... });
test('should throw error when price is negative', () => { ... });
```

### Naming Patterns

Choose a consistent pattern:

**Pattern 1: should + behavior**
```typescript
test('should validate email format', () => { ... });
test('should reject invalid dates', () => { ... });
```

**Pattern 2: behavior + when + condition**
```typescript
test('returns null when user not found', () => { ... });
test('throws error when token expired', () => { ... });
```

## What to Test

### Test Behavior, Not Implementation

Focus on **what** the code does, not **how** it does it:

❌ **Bad (tests implementation):**
```typescript
test('should call internal helper function', () => {
  const spy = jest.spyOn(module, 'internalHelper');
  doSomething();
  expect(spy).toHaveBeenCalled();
});
```

✅ **Good (tests behavior):**
```typescript
test('should format user name correctly', () => {
  const result = formatUserName({ first: 'John', last: 'Doe' });
  expect(result).toBe('John Doe');
});
```

### Test Edge Cases

Include tests for:
- Empty inputs
- Null/undefined values
- Boundary conditions
- Error conditions
- Invalid inputs

```typescript
describe('divideNumbers', () => {
  test('should divide positive numbers', () => {
    expect(divideNumbers(10, 2)).toBe(5);
  });
  
  test('should handle division by zero', () => {
    expect(() => divideNumbers(10, 0)).toThrow('Cannot divide by zero');
  });
  
  test('should handle negative numbers', () => {
    expect(divideNumbers(-10, 2)).toBe(-5);
  });
});
```

## Test Organization

### Group Related Tests

Use `describe` blocks to organize tests:

```typescript
describe('User Authentication', () => {
  describe('login', () => {
    test('should succeed with valid credentials', () => { ... });
    test('should fail with invalid password', () => { ... });
    test('should fail with non-existent user', () => { ... });
  });
  
  describe('logout', () => {
    test('should clear session', () => { ... });
    test('should invalidate token', () => { ... });
  });
});
```

### Setup and Teardown

Use hooks for common setup:

```typescript
describe('Database Tests', () => {
  beforeEach(() => {
    // Run before each test
    database.clear();
  });
  
  afterEach(() => {
    // Run after each test
    database.close();
  });
  
  test('should insert user', () => { ... });
  test('should update user', () => { ... });
});
```

## Test Data

### Use Meaningful Test Data

Make test data clear and representative:

❌ **Bad:**
```typescript
const user = { name: 'abc', age: 123 };
```

✅ **Good:**
```typescript
const user = { name: 'John Doe', age: 30 };
```

### Factory Functions for Complex Data

Create helpers for complex test data:

```typescript
function createTestUser(overrides = {}) {
  return {
    id: 1,
    name: 'Test User',
    email: 'test@example.com',
    ...overrides,
  };
}

test('should update user email', () => {
  const user = createTestUser({ email: 'old@example.com' });
  // test with user
});
```

## Assertions

### Be Specific

Use the most specific assertion possible:

❌ **Weak:**
```typescript
expect(result).toBeTruthy();
```

✅ **Specific:**
```typescript
expect(result).toBe(true);
expect(array).toHaveLength(3);
expect(user).toMatchObject({ name: 'John', age: 30 });
```

### One Logical Assertion Per Test

Keep tests focused:

❌ **Too many concerns:**
```typescript
test('should process user', () => {
  const user = createUser();
  expect(user.name).toBe('John');
  expect(user.email).toBe('john@example.com');
  expect(sendEmail(user)).toBe(true);
  expect(logActivity(user)).toBe(true);
});
```

✅ **Focused:**
```typescript
test('should create user with correct name', () => {
  const user = createUser();
  expect(user.name).toBe('John');
});

test('should send email after user creation', () => {
  const user = createUser();
  expect(sendEmail(user)).toBe(true);
});
```

## Mocking and Stubbing

### Mock External Dependencies

Isolate the code under test:

```typescript
test('should fetch user from API', async () => {
  // Mock the HTTP client
  const mockClient = {
    get: jest.fn().mockResolvedValue({ id: 1, name: 'John' }),
  };
  
  const service = new UserService(mockClient);
  const user = await service.getUser(1);
  
  expect(mockClient.get).toHaveBeenCalledWith('/users/1');
  expect(user.name).toBe('John');
});
```

### Don't Over-Mock

Only mock what you need to:

❌ **Too much mocking:**
```typescript
// Mocking simple math defeats the purpose
const mockAdd = jest.fn((a, b) => a + b);
```

✅ **Mock external/expensive operations:**
```typescript
// Mock database, API calls, file system, etc.
const mockDatabase = { query: jest.fn() };
```

## Async Testing

### Handle Promises Correctly

```typescript
// Option 1: async/await
test('should fetch data', async () => {
  const data = await fetchData();
  expect(data).toBeDefined();
});

// Option 2: return promise
test('should fetch data', () => {
  return fetchData().then(data => {
    expect(data).toBeDefined();
  });
});
```

## Test Coverage

### Aim for High Coverage, But Don't Obsess

- Focus on critical paths
- Cover edge cases
- Don't test trivial code (simple getters/setters)
- 80%+ coverage is a good target
- 100% coverage doesn't guarantee bug-free code

## Best Practices

- **Write tests first or alongside code** - Not as an afterthought
- **Keep tests fast** - Slow tests won't be run
- **Make tests independent** - Each test should run in isolation
- **Test one thing at a time** - Focused tests are easier to debug
- **Use descriptive names** - Test name should explain what failed
- **Avoid test interdependence** - Tests shouldn't rely on each other
- **Clean up after tests** - Reset state, close connections

## Anti-Patterns to Avoid

❌ **Testing implementation details**
❌ **Overly complex test setup**
❌ **Tests that test the testing framework**
❌ **Ignoring failing tests**
❌ **Copy-pasting test code without understanding**

## Framework-Specific Notes

### Jest (JavaScript/TypeScript)
- Use `describe` and `test` (or `it`)
- Leverage built-in matchers
- Use `beforeEach`/`afterEach` for setup

### Pytest (Python)
- Use `test_` prefix for test functions
- Use fixtures for setup
- Leverage parametrize for data-driven tests

### Go Testing
- Use `_test.go` suffix
- Use `t.Run` for subtests
- Table-driven tests are idiomatic

---

**Customize this rule** for your project's testing framework and conventions.

