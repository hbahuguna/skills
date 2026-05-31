---
name: vibe-coding
description: Ship working software fast by directing AI through tight conversational loops. Use when the goal is clear and you want results, not architecture diagrams.
compatibility: opencode
license: MIT
metadata:
  workflow: prototyping
  audience: developers
---

## When This Fits

Good match when:
- You know what you want and want to see it working
- Speed matters more than polish
- You're comfortable iterating on a live result
- The cost of being wrong is low

Bad match when:
- Lives depend on correctness (switch to tdd)
- You haven't decided what to build yet (switch to brainstorming)
- The problem needs deep diagnostic work (switch to debugging)

## Core Idea

You steer, the machine builds. Your job is to describe the destination clearly enough that each step lands close to the mark. The machine's job is to turn those descriptions into runnable code. You check the result, adjust, and repeat. Each cycle is seconds, not hours.

## The Loop

### 1. State the Target
One sentence. What does the output look like? What input does it take? "A CLI that accepts a CSV path and a column name and returns the min, max, and mean." Not "Make something useful with data."

### 2. Send the First Chunk
Give the AI one piece — the smallest thing that can run on its own. Include the language, the environment, and any non-negotiable constraints. "Python 3.12, no external deps. Read CSV from stdin, write results to stdout."

### 3. Run What You Get
Execute immediately. Observe the output. Does it do the thing? Does it crash? You now have real information, not speculation.

### 4. Correct with Specifics
Each iteration gets one concrete delta. "The mean is wrong when a cell is empty." "Add a --json flag." "Rename output to results.txt." Vague feedback produces vague fixes.

### 5. Repeat Until Done
Each cycle tightens the fit. Stop when it works for the cases you care about. Resist the urge to keep polishing beyond what you need.

## Staying Out of Trouble

Speed hides mistakes. These habits keep you from wrecking:

- **Review the diff.** Always look at what changed before accepting. AI will delete things, add things, and rename things without telling you.
- **Batch size matters.** A 400-line change is a risk. Push for smaller, focused edits.
- **Commit after every working state.** Not just at the end. Each commit is a rollback point.
- **Watch for silence.** If the output says "Done" but you don't see evidence, stop and verify.
- **Cut the thread.** If the AI is spinning — generating increasingly complex code to fix earlier mistakes — stop the session, reset context, and start fresh.

## Guard Points

These are non-negotiable. Flag them every time:

| Hazard | Response |
|--------|----------|
| Secrets in code | Stop. Use env vars or a secrets file. |
| Destructive action | Read the command before running. |
| Data loss risk | Confirm intent before proceeding. |
| Runaway process | Set a timeout. Kill if stuck. |

## Relationship to Other Skills

- **Before this: brainstorming** — pick a direction when you're unsure what to build
- **After this: tdd** — lock down behavior with tests once the prototype works
- **Alongside this: debugging** — dig into a specific failure when the cause is unclear

## Quick Check

- [ ] Can I describe what I want in one sentence?
- [ ] Is the first piece small enough to run standalone?
- [ ] Did I run the output and observe the result?
- [ ] Did I review the diff before accepting?
- [ ] Is every working state committed?
- [ ] When to stop: it works for my use case.
