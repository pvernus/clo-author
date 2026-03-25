# Session Capture — Complete Documentation

*v1.1 — Document work sessions for cross-session continuity*

## Input
$ARGUMENTS

## Instructions

Session Capture documents work sessions for cross-session continuity.

### Core workflow (5 steps)

**Step 1: Identify scope**
Review the conversation history for:
- Topic and project name
- Session length: Brief (< 30 min), Medium (30–90 min), Extended (> 90 min)
- Key themes and outputs

**Step 2: Extract artifacts**
Identify:
- Decisions made (design choices, direction changes, resolved questions)
- Unresolved questions (open items, ambiguities, deferred choices)
- Concrete next steps / follow-ups (actionable items for the next session)
- Files created or modified (with paths)

**Step 3: Write session entry**
Append to `.claude/session-log.md` in reverse chronological order (newest first):

```markdown
## YYYY-MM-DD HH:MM — [Session Topic]

**Decisions:**
- [Decision made] — [rationale]

**Unresolved:**
- [Open question or deferred item]

**Next steps:**
- [ ] [Actionable follow-up]

**Files:**
- [path/to/file] — [created/modified/deleted]
```

Create `.claude/session-log.md` with a title header if it doesn't exist:
`# Session Log — [Project Name]`

**Step 4: Generate handoff note**
Overwrite `.claude/handoff.md` with the most recent session's context:

```markdown
# Handoff — [Date]

**Last session:** [Topic]
**Status:** [What was completed]

**Resume here:**
- [Most important next action]

**Context to remember:**
- [Key decision or constraint that shapes upcoming work]
- [Any open question to resolve first]
```

Only the most recent session's context persists in this file.

**Step 5: Maintenance**
- Prune entries from `.claude/session-log.md` older than 60 days
- Confirm output locations: `.claude/session-log.md` and `.claude/handoff.md`

---

### Argument modifiers

- `quick` — abbreviated capture: decisions and follow-ups only (skip detailed file list)
- `project:name` — tag entry to a specific project name

---

### Output locations

| File | Purpose |
|------|---------|
| `.claude/session-log.md` | Reverse-chronological session history |
| `.claude/handoff.md` | Most recent session context for next-session resumption |

---

### Important
- Missing log files are created automatically with proper headers
- The handoff file overwrites the previous session's notes each time — only the most recent context persists
- Use `quick` for brief check-ins; full capture for substantive sessions
