---
description: Documentation standards and best practices
globs:
  - '**/*.ts'
  - '**/*.js'
  - '**/*.py'
  - '**/*.go'
  - '**/*.rs'
  - '**/*.java'
alwaysApply: false
---

<!-- For AI: This rule defines documentation standards for code. Apply when writing or reviewing code that needs documentation. -->
<!-- Related: @docs/QUICK_REFERENCE.md for project overview -->
<!-- Use with: Code generation, documentation tasks -->

# Documentation Standards

This rule defines documentation standards for the project.

## Purpose

Good documentation:
- Helps others understand your code
- Serves as API contracts
- Improves IDE support (intellisense, type hints)
- Makes onboarding easier

## Function Documentation

### Required Elements

All exported/public functions must include:
- **Description** - What the function does
- **Parameters** - Each parameter explained
- **Return value** - What it returns
- **Exceptions** - Any errors thrown
- **Examples** - Usage examples (when helpful)

### Language-Specific Formats

**TypeScript/JavaScript (JSDoc):**
```typescript
/**
 * Calculate the total price including tax
 * @param price - Base price before tax
 * @param taxRate - Tax rate as decimal (e.g., 0.08 for 8%)
 * @returns Total price including tax
 * @throws {Error} When price or taxRate is negative
 */
export function calculateTotal(price: number, taxRate: number): number {
  // implementation
}
```

**Python (Docstring):**
```python
def calculate_total(price: float, tax_rate: float) -> float:
    """
    Calculate the total price including tax.
    
    Args:
        price: Base price before tax
        tax_rate: Tax rate as decimal (e.g., 0.08 for 8%)
    
    Returns:
        Total price including tax
    
    Raises:
        ValueError: When price or tax_rate is negative
    """
    # implementation
```

**Go:**
```go
// CalculateTotal calculates the total price including tax.
// Returns an error when price or taxRate is negative.
func CalculateTotal(price float64, taxRate float64) (float64, error) {
    // implementation
}
```

## Class/Struct Documentation

Document the purpose and provide usage examples:

```typescript
/**
 * HTTP client for making authenticated API requests
 * Handles token refresh and error handling automatically
 * @example
 * const client = new HttpClient({
 *   baseUrl: 'https://api.example.com',
 *   getAccessToken: () => localStorage.getItem('token'),
 * });
 */
export class HttpClient {
  // implementation
}
```

## Type/Interface Documentation

Document properties and their purpose:

```typescript
/**
 * Configuration options for the API client
 */
export interface ApiClientConfig {
  /** Base URL of the API (e.g., 'https://api.example.com') */
  baseUrl: string;
  
  /** Function to retrieve current access token */
  getAccessToken?: () => string | null;
  
  /** Callback when authentication fails */
  onUnauthorized?: () => void;
}
```

## File-Level Documentation

Add a header comment to modules:

```typescript
/**
 * User management utilities
 * Provides functions for user data formatting and validation
 * @module user-utils
 */
```

## What NOT to Document

Avoid documenting the obvious:

❌ **Bad:**
```typescript
/**
 * Gets the user ID
 * @param user - The user
 * @returns The ID
 */
function getUserId(user: User): string {
  return user.id;
}
```

✅ **Better:**
```typescript
// Self-explanatory - no doc needed for simple getters
function getUserId(user: User): string {
  return user.id;
}
```

## When to Add Examples

Add examples when:
- Function behavior is not immediately obvious
- Multiple parameters interact in complex ways
- Common use case should be shown
- Error handling is important to demonstrate

## Best Practices

- Write docs as you write code (not after)
- Update docs when changing behavior
- Explain "why" not just "what"
- Keep it concise but complete
- Use proper markdown formatting
- Link to related functions/types

## References

Adapt this rule to match your language's conventions:
- [JSDoc](https://jsdoc.app/)
- [Python Docstrings (PEP 257)](https://www.python.org/dev/peps/pep-0257/)
- [Go Documentation](https://go.dev/blog/godoc)
- [Rust Documentation](https://doc.rust-lang.org/rustdoc/)

---

**Customize this rule** for your project's specific documentation needs.

