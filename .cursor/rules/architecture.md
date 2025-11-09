---
description: Architecture patterns and design principles
alwaysApply: false
---

<!-- For AI: This rule defines architectural principles. Reference when making structural decisions or reviewing architecture. -->
<!-- Related: @docs/ARCHITECTURE.md for project-specific architecture documentation -->
<!-- Use with: System design, refactoring, architecture reviews -->

# Architecture Principles

This rule defines architectural patterns and design principles for the project.

## Purpose

Good architecture:
- Makes the codebase maintainable
- Enables scaling the team and product
- Reduces cognitive load
- Facilitates testing and changes

## Core Principles

### 1. Separation of Concerns

Keep different aspects of the system separate:

```
✅ Good Structure:
src/
  api/           # API/network layer
  domain/        # Business logic
  ui/            # Presentation layer
  utils/         # Utilities

❌ Bad Structure:
src/
  everything-mixed-together.ts
```

### 2. Single Responsibility

Each module/class/function should have one reason to change:

❌ **Bad (multiple responsibilities):**
```typescript
class UserManager {
  saveToDatabase(user) { ... }
  sendEmail(user) { ... }
  validateUser(user) { ... }
  formatUserDisplay(user) { ... }
}
```

✅ **Good (single responsibility):**
```typescript
class UserRepository {
  save(user) { ... }
}

class EmailService {
  send(to, subject, body) { ... }
}

class UserValidator {
  validate(user) { ... }
}
```

### 3. Dependency Inversion

Depend on abstractions, not concrete implementations:

❌ **Bad (tight coupling):**
```typescript
class OrderService {
  private db = new MySQLDatabase(); // Hard-coded dependency
  
  createOrder(order) {
    this.db.insert(order);
  }
}
```

✅ **Good (dependency injection):**
```typescript
interface Database {
  insert(data: any): void;
}

class OrderService {
  constructor(private db: Database) {} // Injected dependency
  
  createOrder(order) {
    this.db.insert(order);
  }
}
```

## Layered Architecture

Organize code in logical layers:

```
┌─────────────────────────────┐
│  Presentation Layer         │  (UI, controllers, routes)
├─────────────────────────────┤
│  Business Logic Layer       │  (domain models, services)
├─────────────────────────────┤
│  Data Access Layer          │  (repositories, database)
└─────────────────────────────┘
```

### Rules
- Upper layers can depend on lower layers
- Lower layers should NOT depend on upper layers
- Each layer has a clear responsibility

## Module Organization

### Feature-Based Structure

Organize by feature, not by file type:

✅ **Good (by feature):**
```
src/
  users/
    user.model.ts
    user.service.ts
    user.controller.ts
    user.test.ts
  orders/
    order.model.ts
    order.service.ts
    order.controller.ts
    order.test.ts
```

❌ **Bad (by file type):**
```
src/
  models/
    user.model.ts
    order.model.ts
  services/
    user.service.ts
    order.service.ts
  controllers/
    user.controller.ts
    order.controller.ts
```

### Co-locate Related Files

Keep related files together:
- Components with their styles
- Tests with the code they test
- Types with the modules that use them

## Code Organization

### Keep Functions Small

Functions should do one thing and do it well:

❌ **Too large:**
```typescript
function processOrder(order) {
  // 100+ lines of validation, calculation, database operations, email sending...
}
```

✅ **Well-factored:**
```typescript
function processOrder(order) {
  validateOrder(order);
  const total = calculateTotal(order);
  saveOrder(order);
  sendConfirmationEmail(order);
}
```

### Use Meaningful Names

Names should reveal intent:

❌ **Bad:**
```typescript
function proc(d) { ... }
const x = getUserData();
```

✅ **Good:**
```typescript
function processPayment(amount) { ... }
const userData = getUserData();
```

## Error Handling

### Handle Errors at the Right Level

```typescript
// Low-level: Throw specific errors
function findUser(id: string): User {
  const user = database.get(id);
  if (!user) {
    throw new UserNotFoundError(id);
  }
  return user;
}

// High-level: Handle and present to user
async function displayUser(id: string) {
  try {
    const user = await findUser(id);
    render(user);
  } catch (error) {
    if (error instanceof UserNotFoundError) {
      showNotification('User not found');
    } else {
      showNotification('An error occurred');
    }
  }
}
```

## State Management

### Keep State Minimal

Only store what you need:

❌ **Bad (derived state):**
```typescript
const [items, setItems] = useState([]);
const [itemCount, setItemCount] = useState(0); // Derived from items!
```

✅ **Good (compute derived state):**
```typescript
const [items, setItems] = useState([]);
const itemCount = items.length; // Computed
```

### Lift State When Needed

Move state to the lowest common ancestor:

```
Component A (needs data)
Component B (needs same data)
→ Lift state to their parent
```

## Dependencies

### Minimize External Dependencies

- Evaluate if you really need a library
- Consider maintenance and security
- Prefer standard library when possible

### Isolate External Dependencies

Wrap external libraries to make them replaceable:

```typescript
// Wrapper around external library
export class Logger {
  private lib = externalLoggingLibrary;
  
  log(message: string) {
    this.lib.info(message);
  }
}

// Rest of app uses Logger, not the external lib directly
```

## Design Patterns (Use Sparingly)

Common patterns to consider (when appropriate):

- **Factory** - Object creation
- **Observer** - Event-driven communication
- **Strategy** - Swappable algorithms
- **Repository** - Data access abstraction
- **Adapter** - Interface translation

⚠️ **Warning:** Don't over-engineer. Use patterns when they solve real problems.

## Performance Considerations

### Optimize When Needed

1. Make it work
2. Make it right
3. Make it fast (if needed)

Don't prematurely optimize.

### Common Optimizations

- Cache expensive computations
- Lazy load large resources
- Paginate large datasets
- Use appropriate data structures
- Profile before optimizing

## Testing Architecture

### Design for Testability

- Use dependency injection
- Keep functions pure when possible
- Separate logic from I/O
- Mock external dependencies

```typescript
// Testable: Dependencies injected
function processData(data, validator, storage) {
  if (validator.isValid(data)) {
    storage.save(data);
  }
}

// Hard to test: Hard-coded dependencies
function processData(data) {
  if (new Validator().isValid(data)) {
    new Database().save(data);
  }
}
```

## Documentation

### Document Architecture Decisions

Use Architecture Decision Records (ADRs):

```markdown
# ADR 001: Use PostgreSQL for primary database

## Context
Need a database for relational data with strong consistency guarantees.

## Decision
Use PostgreSQL.

## Consequences
- Pro: Strong ACID guarantees
- Pro: Rich query capabilities
- Con: Slightly more complex setup than MongoDB
```

## Best Practices

- **KISS** - Keep it simple, stupid
- **YAGNI** - You aren't gonna need it (don't build for imaginary future)
- **DRY** - Don't repeat yourself (but don't over-abstract)
- **Explicit over implicit** - Clear code beats clever code
- **Convention over configuration** - Use sensible defaults
- **Fail fast** - Detect errors early

## Red Flags

Watch out for:
- God objects (objects that do too much)
- Circular dependencies
- Deep nesting (> 3-4 levels)
- Functions longer than a screen
- Modules with many dependencies
- Tight coupling between modules

## Resources

- [Clean Code](https://www.oreilly.com/library/view/clean-code-a/9780136083238/)
- [Design Patterns](https://refactoring.guru/design-patterns)
- [SOLID Principles](https://en.wikipedia.org/wiki/SOLID)

---

**Customize this rule** for your project's specific architectural needs and patterns.

