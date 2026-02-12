# opencode_agents

OpenCode global agents managed in GitHub.

## Structure

- `agents/`: markdown agent definitions for OpenCode

## Install globally via symlink

```bash
mkdir -p ~/.config/opencode
[ -e ~/.config/opencode/agents ] && mv ~/.config/opencode/agents ~/.config/opencode/agents.backup.$(date +%Y%m%d_%H%M%S)
ln -s /Users/geom-eungom/workspace/zerodice0/development/opencode_agents/agents ~/.config/opencode/agents
```

## Verify

```bash
opencode agent list
```
