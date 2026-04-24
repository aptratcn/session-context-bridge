# Session Context Bridge 🔗

> **Never start from zero. Carry context across sessions with zero dependencies.**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/dependencies-0-green.svg)]()
[![Skill](https://img.shields.io/badge/type-agent--skill-blue.svg)]()

## The Problem

Every new session starts blind. You lose:

| What You Lose | Impact | Recovery Time |
|--------------|--------|---------------|
| Task state & progress | "Where was I?" | 5-15 min |
| Key decisions & reasoning | Re-decide what was already decided | 10-30 min |
| Environment configuration | "Wait, what env vars?" | 5-10 min |
| Blockers & dependencies | Hit same walls again | 15-60 min |
| Project mental model | Re-read codebase | 30-120 min |

**Cost:** ~60-240 minutes of re-contextualization per session. At $0.01/token, that's $5-20 wasted per session on re-reading context you already had.

**claude-mem (65K★)** proved the need. But it requires installation, a worker service, and a database. This skill achieves 80% of the value with 0 dependencies — just markdown files.

## The Solution

```
┌─────────────────────────────────────────────────────────────────┐
│  SESSION END                                                     │
│  ┌──────────────┐  ┌──────────────┐  ┌──────────────┐         │
│  │ current.md   │  │ decisions.md │  │ archive/     │         │
│  │ Active task  │  │ Why we chose │  │ Past sessions│         │
│  │ Next steps   │  │ what we chose│  │ Searchable   │         │
│  │ Blockers     │  │ Alternatives │  │ Reference    │         │
│  └──────────────┘  └──────────────┘  └──────────────┘         │
│       │                   │                  │                  │
│       ▼                   ▼                  ▼                  │
│  ┌─────────────────────────────────────────────────────┐       │
│  │           .context/ directory (git-friendly)         │       │
│  └─────────────────────────────────────────────────────┘       │
│       │                                                         │
│  NEXT SESSION START                                             │
│       ▼                                                         │
│  "Restore my context" → Agent reads .context/ → Picks up      │
│  exactly where you left off                                     │
└─────────────────────────────────────────────────────────────────┘
```

## Quick Start

```bash
# Claude Code
cp SKILL.md ~/.claude/skills/session-context-bridge/

# OpenClaw
cp SKILL.md ~/.openclaw/workspace/skills/session-context-bridge/

# Any agent: Copy SKILL.md content into your agent's skill directory
```

**Commands:**
- End of session: `"save my context"`
- Start of session: `"restore my context"`
- Anytime: `"update context"` after important decisions

## File Structure

```
.context/
├── current.md        ← What you're working on NOW (auto-updated)
├── decisions.md      ← Architectural decisions with reasoning
└── archive/          ← Previous sessions (searchable)
    ├── 2026-04-24.md
    └── 2026-04-23.md
```

### current.md Template

```markdown
# Current Context

## Active Task
[What you're working on right now]

## Progress
- [x] Completed step 1
- [x] Completed step 2
- [ ] Next: step 3
- [ ] Then: step 4

## Blockers
- [Any blockers and their status]

## Environment
- Branch: feature/auth
- Last test: PASS (14:30)
- Deploy: staging
```

### decisions.md Template

```markdown
# Decision Log

## 2026-04-24: Auth Strategy
- **Decision:** Use JWT with refresh tokens
- **Alternatives:** Session cookies, OAuth-only
- **Reason:** Mobile-first, stateless, scalable
- **Trade-off:** More complex token management
```

## Why Zero Dependencies?

| Approach | Dependencies | Setup Time | Maintenance |
|----------|-------------|------------|-------------|
| claude-mem | Node.js + Worker + DB | 30 min | Ongoing |
| Vector DB solutions | Embeddings + DB | 60 min | Ongoing |
| **This skill** | **None** | **30 seconds** | **None** |

Markdown files are:
- **Git-friendly**: Version controlled, diffable, mergeable
- **Searchable**: `grep`, `ripgrep`, any text tool
- **Portable**: Works with any agent, any OS
- **Transparent**: You can read and edit them directly
- **Zero-risk**: No supply chain, no database, no service to maintain

## Works With

- [OpenClaw](https://openclaw.ai)
- Claude Code, Cursor, Codex
- Any agent framework

## Related Skills

- [token-budget-guard](https://github.com/aptratcn/token-budget-guard) — Optimize context window usage
- [skill-context-doctor](https://github.com/aptratcn/skill-context-doctor) — Diagnose context bloat
- [evr-framework](https://github.com/aptratcn/evr-framework) — Verify session outputs

## License

MIT — Context should persist, not perish.
