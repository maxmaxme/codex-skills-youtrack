# Youtrack codex skill

[![Buy Me a Coffee](https://img.buymeacoffee.com/button-api/?text=Buy+me+a+coffee&emoji=%E2%98%95&slug=maxmaxme&button_colour=FFDD00&font_colour=000000&font_family=Cookie&outline_colour=000000&coffee_colour=ffffff)](https://buymeacoffee.com/maxmaxme)

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

During installation, Codex may ask for multiple approval prompts for network commands.
- Press `Yes` for each required step.
- To avoid repeated prompts, choose `Yes, and don't ask again...` for repeated installer command prefixes.

After installation, restart Codex to load the skill.

## Expected UX

User prompt:

`Do task ABC-123`

Agent behavior:

1. Fetch issue context from YouTrack.
2. Build a concise actionable brief.
3. Proceed with code changes when the request is implementation-oriented.
