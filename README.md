# kinva — किण्व

AI development skills for OpenCode. Kinva is Sanskrit for yeast — the agent that transforms raw ingredients into something greater.

Four skills that cover the full workflow:

| Skill | When |
|-------|------|
| **brainstorming** | The problem is fuzzy. Clarify requirements, constraints, and pick a path. |
| **vibe-coding** | The goal is clear. Build fast through tight conversational loops. |
| **tdd** | The behavior matters. Lock correctness with tests before implementation. |
| **debugging** | Something broke. Find the root cause and fix it cleanly. |

## Install

```bash
mkdir -p ~/.config/opencode/skills
cp -r skills/* ~/.config/opencode/skills/
```

For a single project, copy into `.opencode/skills/` instead.

## Suggested Order

Most sessions follow this sequence:

```
brainstorming → vibe-coding → tdd
                  ↓
              debugging (when something breaks)
```

But any skill can be entry point depending on where you are in the work.

## Structure

```
├── .claude-plugin/
│   └── plugin.json
├── skills/
│   ├── brainstorming/
│   ├── debugging/
│   ├── tdd/
│   └── vibe-coding/
├── README.md
└── LICENSE
```
