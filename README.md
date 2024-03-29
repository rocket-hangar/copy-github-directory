# `copy-github-directory`

![Test](https://github.com/rocket-hangar/copy-github-directory/workflows/Test/badge.svg)
[![codecov](https://codecov.io/gh/rocket-hangar/copy-github-directory/branch/master/graph/badge.svg)](https://codecov.io/gh/rocket-hangar/copy-github-directory)

Get a Github directory quickly by a simple command.

# Usage

<p align="center" style="text-align: center">

  <img src="https://raw.githubusercontent.com/rocket-hangar/copy-github-directory/master/doc-assets/1.url.png" width="700" style="max-width: 700px">

  <p align="center" style="text-align: center">Copy the URL on your web browser.</p>

</p>

<p align="center">

  <img src="https://raw.githubusercontent.com/rocket-hangar/copy-github-directory/master/doc-assets/2.ghdir.png" width="900" style="max-width: 900px">

  <p align="center" style="text-align: center">Run <code>copy-github-directory</code> command with the URL. (It is similar <code>git clone</code>)</p>

</p>

<p align="center">

  <img src="https://raw.githubusercontent.com/rocket-hangar/copy-github-directory/master/doc-assets/3.result.png" width="600" style="max-width: 600px">

  <p align="center" style="text-align: center">That's it!</p>

</p>

# Install

You don't need to install it.

```sh
npx copy-github-directory <url> [directory]
```

Just use it with `npx` command.

But, if you install (`npm install -g copy-github-directory`), you can get the short command `ghcopy` instead
of `copy-github-directory`.

# Command

```sh
npx copy-github-directory https://github.com/rocket-hangar/workspace-template
# It will be made `workspace-template` directory on your current location

npx copy-github-directory https://github.com/rocket-hangar/workspace-template project
# It will be made `project` directory on your current location

npx copy-github-directory https://github.com/rocket-hangar/workspace-template .
# It will be made files on your current location
```

# Workspaces

If you use it in a `yarn` workspaces. (If there are exists `yarn.lock` and `workspaces` property on `package.json`)

It adds workspaces information to package.json files.

For example,

```sh
cd my-monorepo
npx copy-github-directory https://github.com/rocket-hangar/templates/tree/main/web project
```

It will write `package.json` files like below.

```json
// $PWD/package.json
{
  "workspaces": ["project"]
}
```

```json
// $PWD/project/package.json
{
  "name": "project"
}
```

If you don't want to modify package.json files use the option `--no-workspace <url>`.

# Alias

If you have URLs that you use frequently, you can give them aliases.

Make `.ghcopy.json` file on your home directory like below. (`$HOME/.ghcopy.json`)

```json
{
  "alias": {
    "workspace": "https://github.com/rocket-hangar/workspace-template",
    "web": "https://github.com/rocket-hangar/templates/tree/main/web",
    "packages": "https://github.com/rocket-hangar/templates/tree/main/packages"
  }
}
```

Then you can use command with the alias.

```sh
copy-github-directory web my-web-project
```

## Pre-configured alias

- `workspace`: `https://github.com/rocket-hangar/workspace-template` yarn berry based workspace template
- `web`: `https://github.com/rocket-hangar/templates/tree/main/web` vite.js based web app template
- `packages`: `https://github.com/rocket-hangar/templates/tree/main/packages` rocket-punch based multi-package template
