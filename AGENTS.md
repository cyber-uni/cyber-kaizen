# AGENTS.md

## What this repo is

`cyber-kaizen` is an agent plugin for agent self-improvement, published to npm as `cyber-kaizen`.
It ships skills only. Its retrospective reads what happened in a repository's agent sessions and
turns it into changes to the agent setup that the owner approves one at a time.

The plugin ships no skills yet. The `retro` skill is specified in `packages/cyber-kaizen/.agents/spec/retro/`, and that
spec still has open questions for the owner to answer. Do not build the skill until they are
answered, and do not answer them yourself.

| Where | What |
| --- | --- |
| `packages/cyber-kaizen` | The plugin, and the npm package `cyber-kaizen` that ships it |
| `packages/cyber-kaizen/.agents/spec/` | Design specs for the plugin, one folder per capability |

## Plugin layout

Everything the plugin needs lives in `packages/cyber-kaizen/` and must stay listed in that
package's `files`, or it will not reach consumers.

| Path | Authored? |
| --- | --- |
| `plugin.json` | yes, the canonical manifest ([Agent Plugins 1.0.0](https://agent-plugins.org/schemas/1.0.0/plugin.schema.json)) |
| `skills/<name>/SKILL.md` and files beside it | yes |
| `.claude-plugin/`, `.cursor-plugin/`, `.codex-plugin/` | derived by `pnpm plugin:build`, never hand-edited |

After editing `plugin.json` or `skills/`, run `pnpm plugin:build` and commit the derived files with
the change. `pnpm plugin:check` (part of `pnpm verify`) fails when a derived file drifted.

Versions flow from `packages/cyber-kaizen/package.json` on `pnpm version`: `changeset version`,
then `universal-plugin plugin version --from-package` carries the number into `plugin.json`, then
`pnpm plugin:build`. Never hand-edit a `version` field.

## Commands

```bash
pnpm verify        # biome, plugin build check, manifest validation, typecheck, tests
pnpm plugin:build  # derive the vendor manifests
```

## Commit discipline

- **Unit of work:** one coherent, independently revertable change. Commit it when it is complete
  and `pnpm verify` passes.
- Conventional Commits (`feat:`, `fix:`, `docs:`, `chore:`); `commitlint` checks them.
- Stage files by name; never `git add .` or `git add -A`.
- A change to `packages/cyber-kaizen` that users see gets a changeset (`pnpm cs`).

## Language

Write all content in en-US.
