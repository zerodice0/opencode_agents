# opencode_agents

OpenCode global agents managed in GitHub.

## Structure

- `agents/`: markdown agent definitions for OpenCode
- `skills/`: reusable OpenCode skill definitions (`SKILL.md`)

## Install globally via symlink

```bash
mkdir -p ~/.config/opencode
[ -e ~/.config/opencode/agents ] && mv ~/.config/opencode/agents ~/.config/opencode/agents.backup.$(date +%Y%m%d_%H%M%S)
ln -s /Users/geom-eungom/workspace/zerodice0/development/opencode_agents/agents ~/.config/opencode/agents
[ -e ~/.config/opencode/skills ] && mv ~/.config/opencode/skills ~/.config/opencode/skills.backup.$(date +%Y%m%d_%H%M%S)
ln -s /Users/geom-eungom/workspace/zerodice0/development/opencode_agents/skills ~/.config/opencode/skills
```

## Verify

```bash
opencode agent list
```

## Run subagents (non-interactive)

Subagents such as `swift-engineer`, `kotlin-engineer`, and `flutter-engineer`
should be invoked through the `/agent` slash command in `opencode run`.

```bash
opencode run "/agent swift-engineer Smoke test only: load swift-docs-latest and return a 3-item checklist."
```

Note: `opencode run --agent <name>` is for primary agents. For subagents, use `/agent <subagent-name> ...`.
