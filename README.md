# cyber-kaizen

An agent self-improvement loop for any coding-agent harness. A retrospective reads what happened in
use, challenges each candidate lesson against the repository as it stands, proposes each survivor in
its cheapest durable form, and writes only what the owner approves. Published to npm as
`cyber-kaizen`.

The plugin ships no skills yet. The first, `/cyber-kaizen:retro`, is being designed in
[`.agents/spec/retro`](./.agents/spec/retro/README.md). The rationale is the research topic
[agent-self-improvement](https://github.com/repobuddy/buddy-agent-harness/tree/main/.research/agent-self-improvement).

## Install

**Claude Code**

```text
/plugin marketplace add cyber-uni/marketplace
/plugin install cyber-kaizen@cyber-uni
```

**Codex**

```text
codex plugin marketplace add cyber-uni/marketplace
codex plugin add cyber-kaizen@cyber-uni
```

**GitHub Copilot CLI**

```text
copilot plugin marketplace add cyber-uni/marketplace
copilot plugin install cyber-kaizen@cyber-uni
```

## Development

The plugin is in `packages/cyber-kaizen`. Edit its `plugin.json` and `skills/`, then derive the
per-vendor manifests:

```bash
pnpm plugin:build
```

`pnpm verify` runs everything CI runs.

## License

MIT
