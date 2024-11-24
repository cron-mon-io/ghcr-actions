# `ghcr-actions`

Reusable GitHub actions for GitHub Container Registry stuff within Cron Mon.

## `build-and-push`

Builds a Docker image and pushes it to `ghcr.io`.

```yaml
jobs:
...
  build_and_push:
    name: Build image and push to ghcr.io
    # These permissions are required for this workflow.
    permissions:
      contents: read
      packages: write
      attestations: write
      id-token: write
    uses: cron-mon-io/ghcr-actions/.github/workflows/build-and-push.yml@main
```

## `retag`

Retags an existing image in `ghcr.io` with a given tag.

```yaml
on:
  release:
    types: [ published ]

jobs:
  retag:
    name: Retag container image
    # These permissions are required for this workflow.
    permissions:
      contents: read
      packages: write
      attestations: write
      id-token: write
    uses: cron-mon-io/ghcr-actions/.github/workflows/retag.yml@main
    with:
      tag: ${{ github.event.release.tag_name }}
```
