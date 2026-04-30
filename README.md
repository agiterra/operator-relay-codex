# operator-relay-codex

Codex CLI plugin for operator-prompt relay. Exposes the relay-management MCP tools to codex agents.

## ⚠️ Auto-forwarding does NOT work in Codex

operator-relay's mechanism for actually intercepting operator prompts and forwarding them to the manager is the Claude Code `UserPromptSubmit` hook. **Codex CLI has no equivalent per-turn hook surface** — codex's plugin model is MCP tools + slash commands only.

Calling `operator_relay_start` from a codex agent will register a relay config in `~/.wire/operator-relay.json` (so the manager can see the registration), but no hook fires to act on it. Operator prompts to the codex agent reach the agent's screen session but are **not** relayed to the manager.

**Workaround for manager-visibility on codex spawns**: brief the codex engineer in their spawn prompt to mirror significant operator directives back via `wire-ipc.send_message`. Manual but explicit. The asymmetry vs. the CC adapter is documented per the 2026-04-30 Linzer/Dacquoise debugging session.

If/when codex CLI adds a per-turn hook surface, this plugin's UserPromptSubmit-equivalent can be wired in.

## MCP tools (provisional)

- `operator_relay_start` — registers config; in codex this is currently a no-op (no hook to fire)
- `operator_relay_stop` — clears the config

## Source

- Tools: [@agiterra/operator-relay-tools](https://github.com/agiterra/operator-relay-tools)
- Claude Code adapter (where this actually works): [@agiterra/operator-relay-claude-code](https://github.com/agiterra/operator-relay-claude-code)
