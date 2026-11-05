# Spaccato for Claude Code

Spaccato explains what a coding agent changed as a one-minute card for the person driving it, and gives the agent a brief to act on. This repository is the Claude Code plugin marketplace; the service is at https://spaccato.dev.

Install, inside Claude Code:

    /plugin marketplace add wildbit/spaccato-plugin
    /plugin install spaccato@spaccato

Then, in any repository, type `/spaccato:card` (Claude Code names a plugin's skills `/<plugin>:<skill>`) or just ask what changed. The first time, the agent opens an approval page at spaccato.dev; sign in with GitHub and click Connect, and that machine is connected to your account. Cards appear on your dashboard under "From your terminal".

Two plugins:

- `spaccato`: the `/spaccato:card` skill and a local MCP server with the tools `spaccato_card`, `spaccato_login` and `spaccato_status`. The program (`spaccato/bin/spaccato.mjs`, Node 20 or newer) reads the change from git and your conversation from the session on your machine and sends them to spaccato.dev, which writes the card. It also works as a command: `node spaccato/bin/spaccato.mjs login`, `… --format agent`, `… setup`.
- `spaccato-gate`, opt in: the Stop hook. When the agent says it is done, a card is written for the work since the last card and, if the brief says the agent is not done, the stop is blocked with the brief as the reason. A run per stop. `/plugin install spaccato-gate@spaccato`.

What leaves your machine, and only after you approved it: the diff, the files the model may read (the repository's text files, trimmed to fit), and your conversation with the agent as the program digests it (your prompts and the agent's replies, never its tool output), with obvious secrets such as API keys, tokens and private keys taken out first. See the Privacy Policy at https://spaccato.dev/privacy.

Claude Code's auto mode may block the first call as data exfiltration, since the tool does send the conversation off the machine. That is the right question to ask; if the answer is yes, allow the tool `mcp__plugin_spaccato_spaccato__spaccato_card` under `/permissions` and call it again.

On a branch, the card covers everything since the branch left the main line, commits and uncommitted work alike; on the main line, the uncommitted work; `base` picks another point.

This repository is generated from Spaccato's source by `pnpm cli:build`; the program is a build output, not something to edit here.
