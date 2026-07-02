# Typo-Tolerant Input Skill

A lightweight agent skill that lets your AI agent (OpenClaw, Hermes, or any
SKILL.md-compatible agent) silently understand English spelling mistakes in
user messages instead of stopping to ask "did you mean...?" every time.

## Why?

Users type fast and make typos. Most of the time the intended word is
obvious from context — an agent that keeps asking for clarification on
every small typo feels annoying and slow. This skill makes the agent behave
like a fluent human reader: understand first, only ask when it's genuinely
ambiguous.

## Compatibility

- ✅ OpenClaw (SKILL.md-based skill system)
- ✅ Hermes agent
- ✅ Any agent framework that supports Markdown-based skill/instruction files

## Installation

### OpenClaw
1. Clone this repo or download `SKILL.md`
2. Copy `SKILL.md` into your OpenClaw workspace's `skills/` folder (rename
   the folder to `typo-tolerant-input` if your setup expects one folder per
   skill)
3. Restart your agent — the skill will auto-load from the workspace

### Hermes agent
1. Download `SKILL.md`
2. Add its contents to your agent's instruction/skill loading path as per
   your Hermes agent configuration
3. Reload the agent

## How it works

The skill instructs the agent to:
1. Scan incoming messages for likely spelling mistakes
2. Use context to infer the intended word
3. Silently proceed if confident, add a short note if moderately confident,
   or ask ONE clarifying question only if genuinely ambiguous
4. Never block a task just because of a typo

See [`sample-conversations.md`](sample-conversations.md)
for before/after examples.

## Contributing

Pull requests are welcome — especially additions to common typo patterns or
edge cases the skill should handle better.

## License

MIT — see [LICENSE](LICENSE)
