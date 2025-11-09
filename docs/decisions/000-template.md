# [number]: [Short Title of Decision]

**Status:** [Proposed | Accepted | Deprecated | Superseded]  
**Date:** [YYYY-MM-DD]  
**Deciders:** [List of people involved in the decision]  
**Supersedes:** [ADR number] (optional)  
**Superseded by:** [ADR number] (optional)

## Context

What is the issue that we're seeing that is motivating this decision or change?

Include:
- The problem being solved
- Relevant constraints (technical, business, time, resources)
- Current situation or pain points
- Requirements that influenced the decision

Keep this section focused and concise. Provide just enough context for someone unfamiliar with the situation to understand why the decision matters.

## Decision

What is the change that we're proposing and/or doing?

Be specific and clear:
- State the decision in one clear sentence
- Describe what will be done
- Explain how it will be implemented (high-level)
- Note any important details or configurations

Example:
"We will use PostgreSQL 15 as our primary database, accessed through TypeORM 0.3, with separate read replicas for analytics queries."

## Consequences

What becomes easier or more difficult to do because of this change?

### Positive Consequences
- What benefits does this decision provide?
- What problems does it solve?
- What does it enable that wasn't possible before?

### Negative Consequences  
- What downsides or costs does this decision have?
- What constraints does it introduce?
- What complexity does it add?

### Neutral Consequences
- What changes that are neither clearly positive nor negative?
- What new responsibilities or processes are required?

Be honest about trade-offs. Every decision has pros and cons.

## Alternatives Considered

What other options did we consider?

For each alternative:

### [Alternative Name]
**Description:** Brief description of the alternative  
**Pros:** Why it was attractive  
**Cons:** Why it wasn't chosen  
**When to reconsider:** Under what circumstances might this alternative be better?

Example:

### MongoDB
**Description:** NoSQL document database  
**Pros:** Flexible schema, fast for simple queries, familiar to team  
**Cons:** Lack of schema enforcement, weaker consistency guarantees  
**When to reconsider:** If we pivot to a data model that truly doesn't fit relational paradigm

List at least 2-3 alternatives to show due diligence. If you didn't consider alternatives, that might indicate the decision wasn't well-thought-out.

## Implementation Notes

(Optional) Any specific implementation details worth noting:

- Configuration requirements
- Migration path from current state
- Key files or components affected
- Timeline or phased rollout plan
- Dependencies to install
- Team members responsible

This section is optional but useful for complex decisions.

## References

(Optional) Links to resources that informed this decision:

- Documentation
- Blog posts or articles
- Discussion threads or RFCs
- Benchmarks or comparisons
- Related ADRs

## Notes

(Optional) Any additional context, caveats, or future considerations:

- Known limitations
- Future improvements planned
- Assumptions made
- Open questions
- Lessons learned (for deprecated ADRs)

---

## How to Use This Template

### For Users

1. **Copy this file** and rename it with the next number and a descriptive title
   ```bash
   cp 000-template.md 001-my-decision.md
   ```

2. **Fill in all required sections** (Context, Decision, Consequences, Alternatives)

3. **Be specific and honest** about trade-offs

4. **Commit with related code** that implements the decision

### For AI Agents

When creating an ADR:

1. **Ask clarifying questions** if context is unclear:
   - What problem is being solved?
   - What alternatives were considered?
   - What constraints exist?

2. **Use the next sequential number** 
   - Check existing ADRs to find the highest number
   - Use that number + 1

3. **Fill in all sections** based on user's answers

4. **Suggest alternatives** if user hasn't considered them

5. **Identify consequences** the user may not have thought of

6. **Format consistently** with this template

Example prompt for AI:
```
@docs/decisions/000-template.md Create an ADR for [decision topic]
```

AI should respond with questions about context, alternatives, and consequences before filling in the template.

---

**Remember:** ADRs are living documents. Update the status as decisions evolve. Don't delete old ADRs—mark them as superseded and create new ones.

