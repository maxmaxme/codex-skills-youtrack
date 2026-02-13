# Youtrack codex skill

Public Codex skill for reading YouTrack issues and turning them into implementation-ready coding context.

https://openai.com/index/introducing-the-codex-app/

## What this skill does

- Fetches a single issue by key (`ABC-123`) from YouTrack API.
- Fetches issue lists by YouTrack query.
- Extracts key fields: `summary`, `description`, `customFields`, `links`, `subtasks`.
- Produces an actionable brief and can continue to implementation.

## Install

Ask Codex to install it via `skill-installer` from this repository.
Example prompt:

```
$skill-installer Install skill maxmaxme/codex-skills-youtrack
```

After installation, restart Codex to load the skill.

## Expected UX

User prompt:

`Do task ABC-123`

Agent behavior:

1. Fetch issue context from YouTrack.
2. Build a concise actionable brief.
3. Proceed with code changes when the request is implementation-oriented.
