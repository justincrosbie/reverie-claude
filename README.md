# Reverie Movies plugin marketplace for Claude

This folder is the Claude Code plugin marketplace for Reverie Movies. It's published as its own public repository (`justincrosbie/reverie-claude`), because users install from there:

```
/plugin marketplace add justincrosbie/reverie-claude
/plugin install reverie-movies@reverie-movies
```

- `.claude-plugin/marketplace.json`: the marketplace
- `plugins/reverie-movies/`: the plugin (the remote MCP server in `.mcp.json`, the `reverie-filmmaking` skill, README)

Check before publishing: `claude plugin validate .` and `claude plugin validate ./plugins/reverie-movies`. Raise `version` in the plugin's `plugin.json` with each release, because installed copies use it to tell an update exists.

The skill's body is `backend/src/services/mcp_service/filmmaking-guide.txt` word for word, as is the ChatGPT app's skill; the server serves the same text as `get_filmmaking_guide` for clients without the plugin. Edit that file and copy it into both skills; `backend/tests/playbook_sync_test.rs` fails until they match. Anthropic's directory doesn't list AI video generators, so this marketplace is how Claude users get it.
