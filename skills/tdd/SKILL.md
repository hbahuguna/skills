---
name: tdd
description: Lock down behavior by writing tests before implementation. Use when correctness matters, you're refactoring, or you want a safety net for changes.
compatibility: opencode
license: MIT
metadata:
  workflow: testing
  audience: developers
---

## When This Fits

Good match when:
- Getting it wrong has real consequences
- You're refactoring existing code and need to preserve behavior
- The behavior can be specified precisely in tests
- You're adding to code that other people (or future you) will change

Bad match when:
- You don't know what the correct behavior should be (start with brainstorming)
- You're exploring and the cost of being wrong is zero (use vibe-coding instead)
- Writing tests would slow discovery without adding safety

## Core Idea

Tests are specifications that run. Writing a test before code forces you to answer: "What exactly should this do?" If you can't write the test, you don't understand the requirement well enough to implement it.

## The Cycle

### Step 1: Define One Behavior
Pick the smallest behavior worth testing. A single input-output relationship. A single error case. A single edge condition. Not "the whole module works" but "returns 0 when the list is empty."

### Step 2: Write a Test That Fails
Write code that asserts the behavior and run it. It must fail. A test that passes before any implementation tests nothing — it may be testing the wrong thing, or testing nothing at all.

Keep the test minimal: arrange the inputs, call the function, assert the result. Three lines.

### Step 3: Make It Pass
Write the minimum implementation required to pass the test. Do not add features the test doesn't demand. Do not add abstractions. Do not refactor yet. The shortest path to green.

### Step 4: Improve
Now that tests are green, clean up. Remove duplication. Rename variables. Extract helpers. The tests guarantee you didn't break anything while cleaning.

### Step 5: Repeat
Add the next behavior. Each cycle adds a new capability and locks it down. The test suite grows with the code, so confidence stays high throughout.

### Step 6: Run Everything
Before finishing, run the entire suite. One passing test means nothing. All tests passing means the system still works as a whole.

## Conversations

| Situation | Opening |
|-----------|---------|
| First behavior | "This component needs to [behavior]. Write a failing test for the simplest case." |
| Next edge case | "The basic case passes. What edge case should I capture next?" |
| Cleaning up | "Tests are green. Help me improve the code structure without breaking them." |
| Legacy code | "Here's untested code. Help me write tests that capture what it currently does before I change it." |
| Review | "Are these tests checking behavior or implementation details? Would they survive a refactor?" |

## Relationship to Other Skills

- **Before this: brainstorming** — clarify what the behavior should be before writing tests
- **Before this: vibe-coding** — prototype first, then lock with tests once the approach is validated
- **After this: debugging** — if a test fails and the cause isn't obvious, dig into it

## Quick Check

- [ ] One behavior per test, not one test per function
- [ ] Test fails before implementation exists
- [ ] Minimum code written to pass
- [ ] Code improved with tests still green
- [ ] Edge cases covered (empty, null, boundary, error)
- [ ] Full suite passes before finishing
