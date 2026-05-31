---
name: brainstorming
description: Get from fuzzy idea to concrete plan. Use when the problem isn't well-defined or you need to choose between paths.
compatibility: opencode
license: MIT
metadata:
  workflow: planning
  audience: developers
---

## When This Fits

Good match when:
- You have a vague notion but can't articulate what needs building
- Multiple approaches exist and none is clearly better
- You need to understand trade-offs before investing time
- The problem space is new to you

Bad match when:
- You know exactly what to build (switch to vibe-coding)
- The requirements are already documented
- You need to fix something specific (switch to debugging)

## Core Idea

Clarity before code. The goal is not a solution — it's a shared understanding of the problem, the constraints, and at least one plausible path forward. You should end this session knowing what to build and why that choice makes sense.

## The Sequence

### 1. One-Line Problem
Write exactly one sentence describing what you're trying to solve. If you can't, the problem isn't scoped tightly enough. "Users can't find the export button." Not "The UX needs work."

### 2. List the Fences
What are you working within? These shape every decision:
- **Time**: deadline or available hours
- **Tech**: language, platform, existing stack
- **Skill**: what you know, what you don't
- **Dependency**: what must integrate, what must not break
- **Non-goals**: what you're explicitly not solving

### 3. Generate Paths
Produce 2-3 distinct approaches. For each, capture:
- The core mechanism in one line
- The main trade-off: what gets easier, what gets harder
- The biggest risk

Do not evaluate yet. Just list.

### 4. Choose
Compare the paths against your fences. Pick the simplest one that satisfies the core need. The test: "If I build this, will the original one-line problem be solved?" If yes, go. If no, you need a different path.

### 5. Define the Start Point
The session ends with a single next action. Not "start building" but:
- "Build the data ingestion module as a standalone script"
- "Test whether library X handles Y by writing a 20-line proof"
- "Write tests for component Z's current behavior before changing it"

## Conversations

| Starting point | Opening |
|----------------|---------|
| Unclear target | "I want to achieve [outcome]. What questions should I answer before I start?" |
| Too many options | "Here are the options I see. Which one is simplest given [constraint]?" |
| Blind spots | "What am I not considering that could block this approach?" |
| Decision time | "Based on [goals] and [constraints], which path should I take?" |
| Ready to build | "We chose [path]. What's the smallest useful piece to start with?" |

## Relationship to Other Skills

- **Before this:** (none — this is the starting point)
- **After this: vibe-coding** — build the chosen approach fast
- **After this: tdd** — if the chosen approach needs correctness guarantees from the start

## Quick Check

- [ ] Problem captured in one sentence
- [ ] Constraints written down
- [ ] 2-3 approaches listed without evaluating
- [ ] Trade-offs and risks noted for each
- [ ] Decision made with rationale
- [ ] Next step is concrete and actionable
