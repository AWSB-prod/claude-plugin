---
name: team-permissions
description: Sets up a shared .claude/settings.json with safe permission defaults for a team repository: allow the everyday commands, deny reading secret files and running destructive commands. Use when the user asks about Claude Code permissions for a team, a shared settings file, or stopping permission prompts safely.
---

Create a `.claude/settings.json` the team can commit.

1. Call `get_template` from the ai-workspace-builder connector with id `settings` to get the starting file.
2. Read the repository's package manifests, Makefile and CI config to find the commands the team actually runs for install, test, lint and build. Allow only those, with exact prefixes.
3. Keep the deny rules for reading `.env` and `secrets/`, and fill the destructive-command placeholder with commands the team's docs say never to run (for example a database reset). Add any secret file the repository has that the template doesn't cover.
4. If `.claude/settings.json` exists, merge into it instead of replacing it, and show the user a diff.
5. Remind the user that personal overrides belong in `.claude/settings.local.json`, which should stay out of version control.
