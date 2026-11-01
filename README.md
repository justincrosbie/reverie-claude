# Reverie Movies plugin marketplace for Claude

The Claude Code plugin marketplace for [Reverie Movies](https://reveriemovies.com): make AI short films and music videos from a conversation with Claude. Install:

```
/plugin marketplace add justincrosbie/reverie-claude
/plugin install reverie-movies@reverie-movies
```

- `.claude-plugin/marketplace.json`: the marketplace
- `plugins/reverie-movies/`: the plugin (the remote MCP server in `.mcp.json`, the `reverie-filmmaking` skill, README)

Check before publishing: `claude plugin validate .` and `claude plugin validate ./plugins/reverie-movies`. Raise `version` in the plugin's `plugin.json` with each release, because installed copies use it to tell an update exists.

Anthropic's directory doesn't list AI video generators, so this marketplace is how Claude users get Reverie.
