# Spaccato for Claude Code

Install it from inside Claude Code, nothing to copy or put on the PATH:

    /plugin marketplace add wildbit/spaccato-plugin
    /plugin install spaccato@spaccato

Then, in any repository, type `/spaccato:card`, or ask what changed. The first time, the `spaccato_login` tool opens the browser on an approval page at spaccato.dev; approve it signed in with GitHub and the terminal is connected to your account.

What the plugin holds: the `/spaccato:card` skill and a local MCP server (`bin/spaccato.mjs mcp`, the one-file command built by `pnpm cli:build`) with the tools `spaccato_card`, `spaccato_login` and `spaccato_status`. The Stop hook is the separate, opt-in `spaccato-gate` plugin in the same marketplace (`../spaccato-gate`): a card at every stop, the stop blocked with the brief when the agent is not done, a run per stop.

The same file also works as a command on the PATH (`spaccato login`, `spaccato`, `spaccato setup` for the user-level skill without the plugin).
