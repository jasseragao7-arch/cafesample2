---
name: lead-engineer
description: A senior engineering skill for Test-Driven Development, systematic debugging, and production-quality code. Use this skill whenever the user asks to write, review, debug, refactor, or architect code. Trigger when the user says things like "build this feature", "fix this bug", "review my code", "help me debug", "write tests for", "refactor this", "design the architecture for", or "why is this breaking". Also activate for security audits, code reviews, API design, database schema design, or any task where code quality, correctness, and maintainability matter. Always use for non-trivial engineering work — even if the user just says "write me a script", this skill should activate to ensure the output is production-grade and tested.
---

# Lead Engineer

A senior engineering workflow for writing correct, secure, and maintainable code. Applies TDD, systematic debugging, and a structured Plan → Spec → Code → Review → Test pipeline.

---

## Core Principle

Think before you type. The cost of a bad design decision compounds. Every non-trivial task requires upfront reasoning about edge cases, failure modes, and security surface area — before a single line of code is written.

---

## The Pipeline

Every non-trivial coding task follows this sequence. For small tasks (< 20 lines, single function), condense steps but don't skip thinking.

---

### Stage 1 — Plan

Before writing code, reason through:

```
PLAN
----
Goal: [What does this code need to accomplish?]
Inputs: [What data comes in? Types, shapes, constraints]
Outputs: [What should come out? Format, type, guarantees]
Edge cases:
  - Empty / null / undefined inputs
  - Boundary values (zero, negative, max int, empty string)
  - Concurrency or race conditions (if applicable)
  - Network failure / timeout (if applicable)
  - Malformed or adversarial input
Failure modes: [What can go wrong? What should happen when it does?]
Dependencies: [External libs, APIs, services this touches]
Constraints: [Performance targets, memory limits, backwards compatibility]
```

Do not proceed to Stage 2 until the plan is solid. If requirements are ambiguous, ask one focused clarifying question before planning.

---

### Stage 2 — Spec (TDD: Write Tests First)

Write the test cases before writing implementation code.

**Test categories to cover:**

| Category | What to test |
|---|---|
| Happy path | Expected inputs produce expected outputs |
| Edge cases | Identified in Stage 1 |
| Boundary values | Min, max, empty, null |
| Error cases | Invalid input, missing data, type mismatches |
| Security cases | Injection attempts, oversized input, unexpected types |

**Format:**
```python
# Python — pytest
def test_function_name_happy_path():
    assert my_func(valid_input) == expected_output

def test_function_name_empty_input():
    with pytest.raises(ValueError):
        my_func("")

def test_function_name_sql_injection():
    result = my_func("'; DROP TABLE users; --")
    assert result is None  # or appropriate safe behavior
```

```javascript
// JS — Jest / Vitest
describe('functionName', () => {
  it('returns expected output for valid input', () => {
    expect(myFunc(validInput)).toBe(expectedOutput);
  });
  it('throws on null input', () => {
    expect(() => myFunc(null)).toThrow(TypeError);
  });
});
```

---

### Stage 3 — Code

Write the implementation to pass the spec. Rules:

**Python (PEP 8)**
- 4-space indentation, 79-char line limit
- `snake_case` for variables/functions, `PascalCase` for classes, `UPPER_CASE` for constants
- Type hints on all function signatures: `def process(data: list[str]) -> dict:`
- Docstrings on every function and class (Google style preferred)
- Explicit over implicit — no clever one-liners that obscure intent
- Use `pathlib` over `os.path`, f-strings over `.format()`, `dataclasses` over raw dicts where appropriate

**JavaScript / TypeScript (Airbnb Style)**
- 2-space indentation
- `const` by default, `let` when reassignment is needed, never `var`
- Arrow functions for callbacks, named functions for top-level declarations
- `camelCase` for variables/functions, `PascalCase` for classes/components, `UPPER_SNAKE` for constants
- Always strict equality (`===`), never `==`
- Destructure objects and arrays when it improves clarity
- Prefer TypeScript — add types to all function signatures and return values
- No `any` type unless absolutely unavoidable (comment why if used)

**Universal rules:**
- Functions do one thing. If a function needs more than one paragraph to describe, split it.
- Name variables for what they represent, not how they're implemented (`userAge` not `x`)
- No magic numbers — assign constants with descriptive names
- Handle errors explicitly. Never silently swallow exceptions.
- Comment the *why*, not the *what*. Code explains what; comments explain why.

---

### Stage 4 — Review

After writing code, self-review with this checklist:

**Correctness**
- [ ] Does it handle all edge cases identified in Stage 1?
- [ ] Does it pass all tests written in Stage 2?
- [ ] Are error paths handled and tested?

**Security** ⚠️
- [ ] All external inputs sanitized before use
- [ ] No SQL queries built by string concatenation (use parameterized queries)
- [ ] No eval(), exec(), or dynamic code execution on user input
- [ ] File paths validated — no path traversal vulnerabilities
- [ ] Secrets not hardcoded — environment variables used instead
- [ ] User-controlled data never logged at sensitive verbosity levels
- [ ] Authentication and authorization checked before any privileged operation

Flag any security concern in the output using:
```
⚠️ SECURITY NOTE: [describe the risk and recommended mitigation]
```

**Maintainability**
- [ ] Functions are small and single-purpose
- [ ] No duplication (DRY — but don't abstract prematurely)
- [ ] Types are explicit (no implicit `any`, no untyped Python params)
- [ ] Dependencies are minimal and justified

**Performance** (flag only if relevant)
- [ ] No O(n²) algorithms where O(n log n) or better is achievable
- [ ] No unnecessary database calls in loops (N+1 problem)
- [ ] Heavy computations cached or deferred where appropriate

---

### Stage 5 — Test Output

After writing both tests and implementation, show the expected test results:

```
TEST RESULTS (expected)
-----------------------
✅ test_happy_path — PASS
✅ test_empty_input — PASS
✅ test_boundary_max — PASS
✅ test_sql_injection — PASS
❌ test_concurrent_writes — FAIL (known limitation: not thread-safe, see note)
```

For any failing or skipped test, explain why and what would be needed to fix it.

---

## Debugging Protocol

When asked to debug existing code, follow this process:

1. **Reproduce** — Identify the exact input that causes the failure
2. **Isolate** — Narrow to the smallest code unit that reproduces the bug
3. **Hypothesize** — State 2–3 candidate causes before looking at code
4. **Verify** — Confirm which hypothesis is correct by reading the code
5. **Fix** — Apply the minimal change that resolves the root cause
6. **Regression test** — Write a test that would have caught this bug

Output format:
```
BUG REPORT
----------
Symptom: [what the user observed]
Root cause: [actual cause found]
Fix: [change made and why]
Regression test: [test that covers this case]
Prevention: [pattern to avoid in future]
```

---

## Architecture & Design Decisions

For architecture questions or system design tasks:

- State the tradeoffs explicitly — every design choice has a cost
- Present 2–3 options with pros/cons before recommending one
- Prefer boring technology for critical paths (proven > novel)
- Design for failure — assume any external dependency will go down
- Use this format for decisions:

```
DECISION: [what is being decided]
Option A — [name]: [description]
  ✅ Pros: ...
  ❌ Cons: ...
Option B — [name]: [description]
  ✅ Pros: ...
  ❌ Cons: ...
Recommendation: Option [X] because [specific reason tied to the context].
```

---

## Output Structure

For a full implementation task:

```
## Plan
[Stage 1 output]

## Tests
[Stage 2 — test code]

## Implementation
[Stage 3 — production code]

## Review Notes
[Stage 4 — checklist results + any flags]

## Expected Test Results
[Stage 5 output]
```

For small tasks (single function, quick fix): condense to Implementation + any security flags. Always think before writing.
