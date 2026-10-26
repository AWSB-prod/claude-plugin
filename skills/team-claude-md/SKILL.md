---
name: team-claude-md
description: Creates or rewrites a team CLAUDE.md for the current repository from the docs the team already has (README, CONTRIBUTING, onboarding guide, wiki pages). Use when the user asks to set up Claude Code for their team, write or improve a CLAUDE.md, or turn their docs into agent instructions.
---

Build a CLAUDE.md the whole team can commit, using only facts found in the repository and the docs the user provides.

1. Collect sources. Read README.md, CONTRIBUTING.md, any docs/ folder, package manifests (package.json, pyproject.toml, Cargo.toml, go.mod), CI config, and an existing CLAUDE.md if there is one. Ask the user for onboarding or wiki pages that aren't in the repository.
2. Extract answers for these fields, quoting the sources: project_name, project_overview, tech_stack, tooling_versions, repo_structure, commands, conventions, behaviour_autonomy, special_files, avoid, testing, deployment, commit_conventions, secrets, imports. Leave a field empty when no source supports it. Never guess a command or a convention.
3. Call the `build_claude_md` tool from the ai-workspace-builder connector with those answers. Never put secret values in any field; describe where secrets live instead.
4. Show the user the result and the fields it reports as missing. Ask about the missing ones that matter most: the test command, things to avoid, and who may deploy.
5. Write the file to CLAUDE.md at the repository root only after the user approves it. If a CLAUDE.md already exists, show a diff and keep anything the team wrote that is still true.
6. Keep the file under 200 lines. Move procedures that only matter for one kind of task (release steps, migrations) into skills instead.

If the connector isn't available, call `get_template` with id `team-root` or write the same sections by hand.
