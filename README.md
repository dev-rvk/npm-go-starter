# create-starterpack

Scaffold a new app from the [starterpack](https://github.com/dev-rvk/starter)
monorepo template.

```bash
bun create starterpack my-app     # via bun's create-* resolver
bunx create-starterpack my-app    # via npm/bunx
npm create starterpack@latest my-app
```

If you omit the name it will prompt for one. The CLI downloads the template from
GitHub, renames the root `package.json`, reinitialises git, and prints the
`make setup` next steps.

## Flags

| Flag | Meaning |
|------|---------|
| `[name]` | Target directory / project name (prompted if omitted) |
| `--ref <branch\|tag>` | Template ref to fetch (default: repo default branch) |
| `--no-git` | Skip `git init` + initial commit |

`STARTERPACK_TEMPLATE` overrides the source repo (default `github:dev-rvk/starter`).

## Repo layout

This repo holds **only the CLI**. The project template lives in a separate repo
([dev-rvk/starter](https://github.com/dev-rvk/starter)) and is fetched at run time
via `giget`. Override the source with `STARTERPACK_TEMPLATE` (default
`github:dev-rvk/starter`).

## Test locally (before publishing)

```bash
bun install                      # or: npm install — installs giget + @clack
node index.mjs /tmp/test-app     # scaffold into a scratch dir
```

## Publish

The package name **must** start with `create-` for `bun create starterpack` /
`npm create starterpack` to resolve it.

```bash
npm publish        # access:public is set in package.json
```

Because the template is fetched from GitHub at run time, you only republish this
CLI when its own logic changes — template updates ship by pushing to the template
repo.
