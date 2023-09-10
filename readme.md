## taco

![Demo](https://raw.githubusercontent.com/boywithkeyboard/taco/dev/.github/demo.png)

> **Warning**\
> You need to follow Semantic Versioning and Conventional Commits if you want to
> use this tool.

### Usage

```yml
name: publish

on:
  workflow_dispatch:
    inputs:
      kind:
        description: 'Kind of release'
        default: 'minor'
        type: choice
        options:
        - prepatch
        - patch
        - preminor
        - minor
        - premajor
        - major
        required: true

jobs:
  publish:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Publish Release
        uses: boywithkeyboard/taco@v0
        with:
          kind: ${{github.event.inputs.kind}}
```

### Customization

| Name                   | Description                                                              | Default  | Required |
| ---------------------- | ------------------------------------------------------------------------ | -------- | -------- |
| `kind`                 | Any of `prepatch`, `patch`, `preminor`, `minor`, `premajor`, or `major`. |          | Yes      |
| `draft`                | Create the release as a draft.                                           | `false`  | No       |
| `include_author`       | Include the author of the pull request in the release notes.             | `false`  | No       |
| `include_description`  | Include the description of the pull request in the release notes.        | `false`  | No       |
| `prerelease_prefix`    | Specify the prefix for prereleases, e.g. `rc`.                           | `canary` | No       |
| `mention_contributors` | Mention all contributors in the footer of the release notes.             | `false`  | No       |
