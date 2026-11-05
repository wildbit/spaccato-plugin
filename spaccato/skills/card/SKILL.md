---
name: card
description: Explain the change made in this session as a Spaccato card for the person you work with, and act on what the card finds. Use when they ask what changed, for a card or a briefing they can share, when you have finished a piece of work, or when they type /spaccato:card.
---

Call the `spaccato_card` tool (from the spaccato MCP server) with the repository's root as `cwd`. It reads what changed: on a branch, everything since it left the main line, commits and uncommitted work alike; on the main line, the uncommitted work (`base` for another point, `since` such as "2h" to read more of the conversation). It reads this session's transcript for the person's prompts and your replies since that commit, sends both to spaccato.dev where a separate model writes the card, and returns the brief for you: the verdict, the claims the code does not bear out, what needs a look, what was done without being asked, and the card's address.

When the terminal is not connected yet, the tool opens an approval page in the person's browser and says so: tell them to click Connect there, then call `spaccato_card` again. (`spaccato_login` does the same on its own.)

The tool sends the diff, the repository's text files the model may read, and this session's prompts and replies (obvious secrets taken out, never tool output) to the person's own Spaccato account. If Claude Code's permissions block the call, tell the person exactly that and that they can allow the tool `mcp__plugin_spaccato_spaccato__spaccato_card` under /permissions; do not run the program directly to get around a block. If the tools are missing altogether, the same program is at `${CLAUDE_PLUGIN_ROOT}/bin/spaccato.mjs` (`node "${CLAUDE_PLUGIN_ROOT}/bin/spaccato.mjs" --format agent --no-open`).

Act on the brief before you tell the person you are done: fix a claim the code does not bear out, or say why not; address each item under needs a look; stop and ask before anything that cannot be undone. Then give the person the headline and the card's address in one or two lines. Do not retell the card yourself. If the tool says nothing has changed, say so.
