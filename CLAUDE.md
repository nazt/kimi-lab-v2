# CLAUDE.md - AI Assistant Guidelines

## Quick Reference - Short Codes

### Context & Planning Workflow
- `ccc` - Create context issue and compact conversation
- `nnn` - Smart planning: Auto-runs `ccc` if no recent context → Create implementation plan
- `gogogo` - Execute the most recent plan issue step-by-step
- `lll` - List project status (issues, PRs, commits)
- `rrr` - Create detailed session retrospective
- `ddd` - Quick date/time check (GMT+7)

## Working Style

### Communication
- English default, Thai when user uses Thai
- Concise and direct

### Authentication
- **User handles all login/auth** - Claude does NOT attempt to login
- Pause and wait when login is required

### File vs Issue
- **GitHub Issues** → Plans, progress tracking, context snapshots
- **Files** → Reference docs, protocols, retrospectives

### Timezone
- **GMT+7** (Bangkok) - Always show GMT+7 first
- Always use `date` command to verify before creating dated files

## Critical Safety Rules

### GitHub Flow (ALWAYS)
**Every change must follow this flow - NO EXCEPTIONS:**
```bash
git checkout -b [type]/[description]   # 1. Create branch
# make changes
git add -A && git commit -m "..."      # 2. Commit
git push -u origin [branch]            # 3. Push branch
gh pr create                           # 4. Create PR
# 5. STOP - wait for user to review and merge
```
- **NEVER** commit directly to `main`
- **NEVER** merge PRs without explicit user permission
- Even "small" changes require branch + PR

### Git Operations
- **NEVER** use `git push --force` or `-f`
- Always use safe, reversible operations

### File Operations
- Never use `rm -rf` - use `rm -i` for confirmation
- Always confirm before deleting files

## Short Code Details

### `ccc` - Create Context & Compact
1. Gather: `git status`, `git diff`, `git log --oneline -5`
2. Create GitHub Issue with current state
3. Compact conversation with `/compact`

### `nnn` - Next Task Planning
1. Check for recent context (run `ccc` if none)
2. Analyze issue/context
3. Create comprehensive plan issue
4. **NO CODING** - only research and planning

### `gogogo` - Execute Plan
1. **Create branch**: `git checkout -b [type]/issue-[number]-[description]`
2. Find most recent `plan:` issue
3. Execute step-by-step
4. Test & verify
5. Commit changes
6. Push branch & create PR
7. **STOP** - wait for user review and merge

### `lll` - List Status
Run `gh` and `git` commands to show:
- Open issues
- Recent PRs
- Current branch status
- Recent commits

### `ddd` - Date/Time Check
Quick verification of current date and time.

**When to use:**
- Before creating dated files (retrospectives, context snapshots)
- Before adding timestamps to issues or commits
- Whenever unsure about current date/time

**Output:**
- Current date (YYYY-MM-DD)
- Current time (HH:MM)
- Timezone confirmation (GMT+7 Bangkok)

**Command:**
```bash
date "+%Y-%m-%d %H:%M %Z"
```

### `rrr` - Retrospective
Create `retrospectives/YYYY/MM/YYYY-MM-DD_HH-MM_retrospective.md` with:
- Session summary & timeline
- Technical details
- **AI Diary** (REQUIRED)
- What went well / could improve
- **Honest Feedback** (REQUIRED)
- Lessons learned
- Next steps

## Git Commit Format
```
[type]: [brief description]

- What: [specific changes]
- Why: [motivation]
- Impact: [affected areas]

Closes #[issue-number]
```
Types: `feat`, `fix`, `docs`, `style`, `refactor`, `test`, `chore`

## Lessons Learned
- **2025-11-30**: Always use GitHub Flow (branch → PR → review) - no direct commits to main, even for "small" changes
