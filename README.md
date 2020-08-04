# Typescript Library Monorepo Template

## Features

- Full TypeScript support, linting, formatting, ESM and CommonJS bundles and many other developer's goodies with [tsdx](https://github.com/formium/tsdx).
- Linting on precommit with `husky` and `lint-staged`.
- Multiple packages management with Lerna.
- Scoped private NPM packages with GitHub Packages.
- Basic extendable CI process with GitHub Actions.

## GitHub Packages

To use Github Packages registry you must [provide](https://github.com/settings/tokens/new) `Personal access token` with `read:packages` and `write:packages` scopes.

It can be stored in `.npmrc` file in the root directory:

```
//npm.pkg.github.com/:_authToken=GITHUB_PERSONAL_ACCESS_TOKEN
@OWNER:registry=https://npm.pkg.github.com
always-auth=true
```

`OWNER` is the name of the user or organization account that owns the repository.

### Multiple packages

[GitHub docs on multiple packages at the same repository](https://docs.github.com/en/packages/using-github-packages-with-your-projects-ecosystem/configuring-npm-for-use-with-github-packages#publishing-multiple-packages-to-the-same-repository)

In `package.json` of every package:

```json
"repository" : {
    "type" : "git",
    "url": "ssh://git@github.com/OWNER/REPOSITORY.git",
    "directory": "packages/name"
  },
```

`OWNER` is the name of the user or organization account that owns the repository.
`REPOSITORY` is the name of the repositroy containing the package.

## Publish

```
yarn lerna publish
```

Publish every changed package to registry. It will build packages before publish.
