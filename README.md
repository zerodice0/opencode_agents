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
opencode mcp list
```

## Kotlin MCP server setup

`kotlin-engineer` assumes a `kotlin-mcp` server is configured and connected.

```json
{
  "mcp": {
    "kotlin-mcp": {
      "type": "local",
      "command": [
        "/Users/geom-eungom/.local/share/opencode/mcp/kotlin-mcp-server/.venv/bin/python",
        "/Users/geom-eungom/.local/share/opencode/mcp/kotlin-mcp-server/kotlin_mcp_server.py"
      ],
      "enabled": true,
      "environment": {
        "MCP_API_TIMEOUT_MS": "10000"
      },
      "timeout": 10000
    }
  }
}
```

If the server does not connect, run `opencode mcp list` and confirm the command path exists.

## Run subagents (non-interactive)

Subagents such as `swift-engineer`, `kotlin-engineer`, and `flutter-engineer`
should be invoked through the `/agent` slash command in `opencode run`.

```bash
opencode run "/agent swift-engineer Smoke test only: load swift-docs-latest and return a 3-item checklist."
```

Note: `opencode run --agent <name>` is for primary agents. For subagents, use `/agent <subagent-name> ...`.

## Local runtime artifacts

`mcp_audit.db` and `mcp_security.log` are runtime files created by local MCP execution and should not be committed.
