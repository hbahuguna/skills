---
name: debugging
description: Find and fix the root cause of unexpected behavior. Use when something should work but doesn't, and the reason is not obvious.
compatibility: opencode
license: MIT
metadata:
  workflow: fixing
  audience: developers
---

## When This Fits

Good match when:
- Code runs but produces wrong output
- A previously working feature stopped working
- Tests fail and you don't know why
- Behavior is inconsistent or intermittent

Bad match when:
- The fix is obvious (switch to vibe-coding and apply it)
- You haven't diagnosed yet but the error message is self-explanatory
- You're building something new, not fixing something broken

## Core Idea

Every bug has a single cause. Your job is to find it by eliminating possibilities, not by trying random fixes. Guessing wastes time. A structured elimination process converges fast.

## The Pipeline

### 1. Lock the Reproduction
You cannot fix what you cannot see. Get a reliable way to trigger the bug. If it's intermittent, identify the conditions: "happens on files larger than 10MB" not "sometimes crashes."

Write down:
- Exact steps to trigger
- Input used
- Expected output
- Actual output

### 2. Assess
How bad is it? Does it block the feature? Is there a workaround? Was it ever working? If yes, what changed between then and now? The "what changed" question is often the fastest path to the cause.

### 3. Generate Suspects
List 2-3 things that could cause this. For each one, predict: "If X is the cause, then Y will be true when I check." This turns vague suspicion into testable statements.

### 4. Test Each Suspect
Check the most likely one first. Add a print, check a log, isolate the component, simplify the input. One test per hypothesis. When a hypothesis fails, move to the next.

Key rule: change exactly one variable at a time. If you change two things and the behavior changes, you won't know which one mattered.

### 5. Fix and Confirm
Once you know the cause:
- Apply the smallest change that removes it
- Verify the reproduction case now produces the expected output
- Check that nothing else broke (run related tests, check related features)

### 6. Ask: Where Else?
Same cause pattern, different location. Does the same class of bug exist in similar code? If the fix was adding a null check, where else might a null slip through? If the fix was correcting a logic condition, what other conditions might be wrong?

## Conversations

| Situation | Opening |
|-----------|---------|
| Starting cold | "When I do [X], I see [Y]. I expected [Z]. Here's the code and input." |
| Narrowed down | "I've isolated the crash to this function on line 42. The variable is nil here. What path leads to that?" |
| Regression | "This worked before commit abc123. Here's what changed. Which change could cause this?" |
| Intermittent | "Fails about 1 in 10 runs with this input. No obvious pattern. What should I log to identify the conditions?" |
| After fix | "Root cause was [X]. I applied [fix]. Does the logic look correct for the related paths too?" |

## Relationship to Other Skills

- **Before this:** (none — drop in when something breaks)
- **After this: brainstorming** — if the bug reveals a deeper design problem worth rethinking
- **Alongside this: tdd** — write a test that captures the bug before fixing, so it never comes back

## Quick Check

- [ ] Bug reproduces reliably with documented steps
- [ ] Suspects listed with testable predictions
- [ ] Each suspect tested one at a time
- [ ] Root cause confirmed
- [ ] Fix applied and reproduction now passes
- [ ] Related code checked for same pattern
