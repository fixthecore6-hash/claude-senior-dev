# senior-dev — AI Coding Skill

> Code like a 20+ year senior fullstack engineer. Surgical fixes. Zero padding. Minimum correct change.

A skill for Claude (and other AI coding agents) that stops the pattern of writing 50 lines to fix a 5-line bug.

## The Problem

AI coding agents tend to:
- Rewrite entire files when one line is broken
- Add abstractions, logging, and helpers that weren't asked for
- Paste the full file back when showing a fix
- Over-engineer simple changes

## What This Skill Does

Forces the agent to:
1. **Diagnose first** — find the root cause before writing anything
2. **Fix minimally** — change only what's broken
3. **Show diffs, not files** — output only the changed lines
4. **Match the codebase** — use the same style, patterns, and libraries already present
5. **Defer complexity** — no premature abstraction

## Install

### Claude Code (Plugin)
```bash
claude plugin marketplace add your-username/senior-dev
claude plugin install senior-dev@senior-dev
```

### Claude.ai / Anthropic Skills
Upload `senior-dev.skill` via the Skills settings panel.

### Manual (Any Agent)
Copy `SKILL.md` into your agent's skills directory:
```bash
# Claude Code
cp -r senior-dev/ ~/.claude/skills/

# Cursor
cp -r senior-dev/ ~/.cursor/skills/

# Windsurf
cp -r senior-dev/ ~/.codeium/windsurf/skills/
```

## Usage

The skill auto-triggers on coding requests. You can also invoke explicitly:

```
/senior-dev fix this bug
/senior-dev add pagination to this function
/senior-dev refactor this component
```

Or just describe your problem — the skill activates on any bug fix, feature, or refactor request.

## What You Get

**Before (junior pattern):**
```
Sure! I'd be happy to help with that. The issue is in your authentication. 
Let me rewrite the entire auth module with better error handling, token 
refresh, logging, and utility functions...
[50 lines of unrequested code]
```

**After (senior pattern):**
```
`token` is undefined when user is not logged in. Add null check:

if (!token) return null;
```

## Skill Structure

```
senior-dev/
├── SKILL.md              # Core skill instructions
├── references/
│   └── stacks.md         # Stack-specific idioms (JS/TS, React, Next.js, 
│                         # Node, Python, SQL, CSS, REST, Git)
└── README.md             # This file
```

## Covers

- **Bug fixes** — diagnosis protocol, common root causes checklist
- **Feature implementation** — interface-first, YAGNI
- **Refactoring** — behavior-preserving, scope-limited
- **Architecture** — boring-tech defaults, optimize for deletion
- **Anti-patterns** — explicit list of what NOT to do

## Stack Support

JavaScript · TypeScript · React · Next.js · Node.js · Python · SQL · CSS/Tailwind · REST APIs · Git

## Contributing

PRs welcome. Focus on:
- Additional stack idioms in `references/stacks.md`
- New anti-pattern entries
- Better diagnosis protocol examples

## License

MIT
