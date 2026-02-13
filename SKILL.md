---
name: youtrack
description: Fetch and analyze YouTrack issues, then convert task text into actionable implementation steps for coding work. Use when the user references YouTrack, provides an issue key like ABC-123, asks to "do the task", requests task details, acceptance criteria, linked issues, bug-fix context from YouTrack, or asks to configure YouTrack access token/domain for Codex.
---

# YouTrack

Use this skill to pull issue details from YouTrack and turn them into a concrete implementation plan.

## Quick start

- If environment is not configured, ask for setup and run `scripts/setup_env.sh`.
- Require `YOUTRACK_BASE_URL` and `YOUTRACK_TOKEN`.
- Never ask the user to paste the full token in chat.
- Ask the user to set token locally and confirm when ready, or offer to run the interactive setup script.
- Always call YouTrack API directly when issue details are needed.

If token/domain is missing, provide these steps:
1. Create a YouTrack permanent token from user profile security settings.
2. Run setup script:
```bash
"$CODEX_HOME/skills/youtrack/scripts/setup_env.sh"
```
3. Restart Codex desktop after env update.

## Required environment variables

- `YOUTRACK_BASE_URL` (for example `https://youtrack.example.com`)
- `YOUTRACK_TOKEN` (YouTrack permanent token)

Never store tokens in repository files or commit them.

## Workflow

1. Detect issue key in user message with regex `[A-Z][A-Z0-9]+-[0-9]+`.
   Also treat phrases like `Сделай задачу ABC-123` / `Do task ABC-123` as an implementation request.
2. Run `scripts/fetch_issue.sh <ISSUE_KEY>` or query mode when key is absent.
3. Parse response fields:
- `idReadable`
- `summary`
- `description`
- `customFields`
- `links`
- `subtasks`
4. Produce a short structured brief before coding:
- Goal
- Problem statement
- Constraints and scope
- Acceptance criteria
- Open questions
- Implementation steps
5. If the user asks to implement, proceed with code changes immediately.
   For direct execution phrasing (`Сделай задачу ...`), do not stop after summary: continue to implementation.

## Commands

Fetch one issue:

```bash
"$CODEX_HOME/skills/youtrack/scripts/fetch_issue.sh" ABC-123
```

Fetch list by query:

```bash
"$CODEX_HOME/skills/youtrack/scripts/fetch_issue.sh" --query 'for: me #Unresolved'
```
