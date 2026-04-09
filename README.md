# operator-relay-codex

Codex CLI plugin for operator-prompt relay — forwards operator prompts on ephemeral agents to managing agents via Wire.

## Usage

Install via Codex CLI:

```
codex plugin install agiterra/operator-relay-codex
```

## Skills

- `/operator-relay:start` — Start the relay (register this ephemeral agent with a manager)
- `/operator-relay:stop` — Stop the relay

## Hooks

- **UserPromptSubmit** — Intercepts operator prompts and forwards them to the managing agent

## Source

- Tools: [@agiterra/operator-relay-tools](https://github.com/agiterra/operator-relay-tools)
- Claude Code adapter: [@agiterra/operator-relay-claude-code](https://github.com/agiterra/operator-relay-claude-code)
