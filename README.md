# Reverie Movies plugin marketplace for Claude

This folder is the Claude Code plugin marketplace for Reverie Movies. It's published as its own public repository (`justincrosbie/reverie-claude`), because users install from there:

```
/plugin marketplace add justincrosbie/reverie-claude
/plugin install reverie-movies@reverie-movies
```

- `.claude-plugin/marketplace.json`: the marketplace
- `plugins/reverie-movies/`: the plugin (the remote MCP server in `.mcp.json`, the `reverie-filmmaking` skill, README)

Check before publishing: `claude plugin validate .` and `claude plugin validate ./plugins/reverie-movies`. Raise `version` in the plugin's `plugin.json` with each release, because installed copies use it to tell an update exists.

The skill mirrors the server's connection instructions (`SERVER_INSTRUCTIONS` in `backend/src/services/mcp_service.rs`) and the ChatGPT app's skill (`integrations/chatgpt-app/skills/ai-filmmaking/SKILL.md`), plus shot craft from making real films. Change them together. Anthropic's directory doesn't list AI video generators, so this marketplace is how Claude users get it.
