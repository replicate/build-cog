# build-cog

This is a GitHub Action that builds [Cog](https://cog.run) from source.

This is useful for testing unreleased versions of Cog, but **you probably want [replicate/setup-cog](https://github.com/replicate/setup-cog) instead**, which handles more setup like installing Docker buildx, installing NVIDIA's CUDA drivers, installing a release of Cog, logging in to Replicate, etc.

## Usage

Add a step to your workflow that uses this action:

```yml
- name: Build Cog from source
  uses: replicate/build-cog@v1
  with:
    commitish: "3cf1e44" # can be a SHA, branch name, or tag name
```

This will clone the [Cog repository](https://github.com/replicate/cog), checkout the specified commitish, compile the `cog` binary, and make it available in the `PATH`.

Now you can run the `cog` CLI in subsequent steps to `cog run`, `cog build`, `cog push`, etc.

## Inputs

This following input can be specified using the `with` keyword:

### `commitish`

In Git, a commitish is a reference that can be resolved to a commit, such as a commit hash, branch name, or tag name.

All of the following are examples of valid commitishs:

- `3cf1e44`: A commit hash prefix
- `3cf1e448ca54088d797bc774ccc4b7a9f075aae0`: A full commit hash
- `main`: A branch name
- `v0.8.6`: A tag name

This is optional. It defaults to `main`.