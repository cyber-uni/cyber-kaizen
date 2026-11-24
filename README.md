# self-improve

An agent self-improvement loop for any coding-agent harness. A retrospective reads what happened in
use, challenges each candidate lesson against the repository as it stands, proposes each survivor in
its cheapest durable form, and writes only what the owner approves. Published to npm as
`@cyber-uni/self-improve`.

The plugin ships no skills yet. The first, `/self-improve:retro`, is being designed in
[`packages/self-improve/.agents/spec/retro`](./packages/self-improve/.agents/spec/retro/README.md). The rationale is the research topic
[agent-self-improvement](https://github.com/repobuddy/buddy-agent-harness/tree/main/.research/agent-self-improvement).

## Install

**Claude Code**

```text
/plugin marketplace add cyber-uni/marketplace
/plugin install self-improve@cyber-uni
```

**Codex**

```text
codex plugin marketplace add cyber-uni/marketplace
codex plugin add self-improve@cyber-uni
```

**GitHub Copilot CLI**

```text
copilot plugin marketplace add cyber-uni/marketplace
copilot plugin install self-improve@cyber-uni
```

## Development

The plugin is in `packages/self-improve`. Edit its `plugin.json` and `skills/`, then derive the
per-vendor manifests:

```bash
pnpm plugin:build
```

`pnpm verify` runs everything CI runs.

## License

MIT
