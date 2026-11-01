# Reverie Movies for Claude

Make AI short films and music videos with Claude. This plugin connects Claude Code (and other Claude surfaces that load plugins) to Reverie Movies and teaches it how to make a film well: plan scenes and shots, keep characters and objects consistent from shot to shot, render continuous camera moves across several shots, check each shot before building on it, and export the finished film.

## What it adds

- **The Reverie Movies MCP server** at `https://api.reveriemovies.com/mcp`. When Claude first uses it you're sent to Reverie to sign in and approve access (OAuth). Signing in creates an account with free starter credits.
- **The `reverie-filmmaking` skill**: the workflows (from an idea, a script, a song or an existing film), continuity and shot craft learned making real films, model choice, and how spending works.

## Install

```
/plugin marketplace add justincrosbie/reverie-claude
/plugin install reverie-movies@reverie-movies
```

Then ask Claude for a film, for example: "Make a 60-second short about a paper boat's journey to the sea."

## What it sends, and what it costs

The plugin runs no code on your machine. Claude talks to Reverie's server over HTTPS as you, using the access you approved. It can see and change your Reverie projects and your credit balance, never your email, password or payment details. Anything that costs credits (renders, images, exports) is quoted first and runs only after you approve it. Credits are bought at reveriemovies.com, not in Claude.

Privacy policy: https://reveriemovies.com/privacy · Terms: https://reveriemovies.com/terms · Docs: https://reveriemovies.com/docs/mcp · Support: justin@reveriemovies.com
