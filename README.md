# AI Workspace Builder for Claude Code

Turn the docs your team already has into a Claude Code setup the whole team shares.

## What it does

- **team-claude-md**: reads your README, contributing guide, onboarding docs and package manifests, extracts the commands, conventions and rules they contain, and builds a team CLAUDE.md. Fields the docs don't support are left out and reported, so nothing is guessed.
- **team-permissions**: creates a shared `.claude/settings.json` that allows the commands your team runs every day and denies reading secret files and running commands your docs say never to run.
- **Connector**: both skills use the AI Workspace Builder connector at `https://aiworkspacebuilder.ai/mcp`. It needs no account and stores nothing. Its tools are `list_templates`, `get_template`, `build_claude_md` and `list_role_profiles`.

## Install

In Claude Code:

```
/plugin marketplace add AWSB-prod/claude-plugin
/plugin install ai-workspace-builder@ai-workspace-builder
```

## Usage

Ask Claude to "set up Claude Code for our team" or "write a CLAUDE.md from our docs", or run `/team-claude-md` or `/team-permissions` directly. Claude shows you every file before writing it.

## More

To generate a CLAUDE.md, role profiles for each part of your team and an install script straight from uploaded documents, use the [web app](https://aiworkspacebuilder.ai/?utm_source=github&utm_medium=plugin).

Short how-to videos, from a first CLAUDE.md to a full team setup: [youtube.com/@aiworkspacebuilder](https://www.youtube.com/@aiworkspacebuilder)

## Privacy

The connector does not store the answers it receives or anything else from your conversation, apart from standard server logs. Full policy: https://aiworkspacebuilder.ai/privacy

## Support

hello@aiworkspacebuilder.ai

## License

MIT
