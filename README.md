# dsh-agent-kit

A personal bundle for [DeepSeek Harness](https://github.com/deepseek-ai) (DSH): one package that
carries an agent preset tailored to a TypeScript fullstack stack together with its skills and
MCP servers, so the working environment installs, updates and travels as a unit.

> Status: personal, work in progress. Version `0.1.0`.

## Target stack

The preset, the skills and the MCP servers are picked for a TypeScript fullstack project:

| Layer | Choice |
| --- | --- |
| Runtime and monorepo | Bun, Turborepo |
| Web app | TanStack Start, React 19, TanStack Router, TanStack Query, Tailwind CSS v4 |
| Server | Hono |
| Data | Drizzle ORM on PostgreSQL |
| Auth | Better-Auth |
| API and validation | oRPC, Zod |
| Tooling | oxlint, oxfmt, Docker and docker-compose |

## What is inside

| Part | Where | Notes |
| --- | --- | --- |
| Agent preset `Fullstack` | `cordis.patch.yml` | Based on the stock `standard` preset, with its own persona, tool set, plan mode, compaction and delegation groups |
| Eight skills | `skills/` | Mounted into the preset through `@deepseek-ai/dsh-skill-filesystem` |
| Six MCP servers | `cordis.patch.yml` | `better-t-stack`, `context7`, `shadcn`, `better-auth`, `playwright`, `chrome-devtools` |
| Plugin card text | `locale/en.json` | Title and description shown in the plugin inventory |

The bundle is configuration-only: no Host or Client entry files, no build step, no runtime
dependencies. It contributes Loader rows and nothing else.

Skills included: `commit-message-format`, `frontend-design`, `frontend-design-direction`,
`make-interfaces-feel-better`, `react-hooks-best-practices`, `reactuse`,
`vercel-react-best-practices`, `web-design-guidelines` — they cover the web layer of the stack.

## Requirements

- DSH with the `standard` preset available (the `@deepseek-ai/dsh-web-app` bundle).
- Network access for the MCP servers: `context7`, `shadcn`, `playwright` and
  `chrome-devtools` start through `npx`, `better-t-stack` through `bunx`, and `better-auth` is a
  public HTTPS endpoint contacted at session start.

## Install

Install through the DSH Plugin Manager, pointing `install_bundle` at the absolute path of this
directory:

```
plugin_manager  action: install_bundle  target: /absolute/path/to/dsh-agent-kit
```

The manager performs the package installation and the bundle selection itself; there is no need
to edit the profile's `package.json` or to run a package manager by hand. Afterwards the profile
records the package as a `link:` dependency and adds its name to `dsh.profile.bundles`.

Once installed, `Fullstack` appears in the Agent Preset list. Pick it for a new session to
activate the preset and its skills; an already running session keeps the composition it started
with.

## How the bundled skills are mounted

The preset does not hardcode a path. It asks the Loader to compute one on the installing machine,
the same way the stock `cordis` preset mounts its own skills:

```yaml
- id: skill-filesystem
  name: '@deepseek-ai/dsh-skill-filesystem'
  config:
    customSkillDirs:
      - !!js process.getBuiltinModule('node:path').join(process.getBuiltinModule('node:path').dirname(process.getBuiltinModule('node:module').createRequire(baseUrl).resolve('dsh-agent-kit/package.json')), 'skills')
```

`baseUrl` is the profile's config-tree anchor; `createRequire` resolves this package from there
and `skills` is appended. **The string inside `resolve(...)` must match the `name` field in
[package.json](package.json)** — if you fork and rename the package, change both.

## Repository layout

```
cordis.patch.yml        the bundle patch: inserts the preset-fullstack row
package.json            manifest: dsh.bundle.patch points at the patch above
locale/en.json          plugin card title and description
skills/                 the eight skills mounted by the preset
LICENSE                 MIT
```

## Notes and limitations

- The preset declares `id: fullstack`. A profile must define that id exactly once — a hand
  written row and this bundle together would collide.
- Sessions remember the preset they were created with (`agentPreset` in the session store). A
  session created under an earlier preset id will not resolve after that id is renamed or
  removed; start a new session to pick up this preset.
- The preset does **not** change which preset a new session starts with; that stays with the
  profile's `agent-preset-registry` (`default` / `selectedDefault`).
- `tool-bash` is disabled on Windows and `tool-pwsh` everywhere else, decided by `!!js`
  expressions in the patch.
- `"private": true` in the manifest keeps the package from being published to npm by accident.
  Remove it only when the package is meant to be published.

## License

MIT — see [LICENSE](LICENSE). Bundled third-party skill content keeps its own terms.
