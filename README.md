# mason-registry

Personal [Mason](https://github.com/mason-org/mason.nvim) registry. Packages here take precedence over the default registry when listed first.

## Packages

| Package | Source |
|---|---|
| `gitlab-ci-ls` | [RiceKrisBs/gitlab-ci-ls](https://github.com/RiceKrisBs/gitlab-ci-ls), a fork of [alesbrelih/gitlab-ci-ls](https://github.com/alesbrelih/gitlab-ci-ls) |

## Usage

`gitlab-ci-ls` ships a prebuilt binary for Apple Silicon macOS only. No Rust toolchain is needed.

```lua
require("mason").setup({
  registries = {
    "github:RiceKrisBs/mason-registry",
    "github:mason-org/mason-registry",
  },
})
```

Then `:MasonInstall gitlab-ci-ls`. The registry must come first, otherwise the upstream package of the same name is used.

## Updating a package

Tag a release in the package's repo, wait for its release workflow to attach the binary, then update the version in `source.id` in `packages/<name>/package.yaml` and push to `main`. The release workflow publishes `registry.json.zip` when anything under `packages/` changes. Mason users pick it up on their next registry update.
