# Spaccato review gate

A second, opt-in plugin: the Stop hook alone. Install the main `spaccato` plugin first (it has the skill and the tools), then this one when you want a card at every stop:

    /plugin install spaccato-gate@spaccato

When the agent says it is done, `spaccato hook stop` writes a card for the work since the last card (nothing happens when the working tree is unchanged) and, if the brief says the agent is not done, blocks the stop with the brief as the reason. It costs a run per stop. Uninstall the plugin to turn it off.
