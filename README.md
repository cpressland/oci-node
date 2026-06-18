# oci-node

A minimal OCI image that packages [Node.js](https://nodejs.org/) for use in devcontainer builds.

## What it does

The `Containerfile` downloads a pinned release of Node.js from the official distribution and produces a scratch-based image containing only the runtime. This keeps the image as small as possible with no extra dependencies.

The image is built for `linux/amd64` and `linux/arm64` via GitHub Actions and published to the GitHub Container Registry at:

```
ghcr.io/thredd-platform/oci-node:latest
```

## Usage

Copy the runtime into your devcontainer image:

```dockerfile
COPY --from=ghcr.io/thredd-platform/oci-node:latest / /
```

## Version updates

[Renovate](https://docs.renovatebot.com/) is configured to automatically open pull requests when new releases of Node.js are published, keeping `NODE_VERSION` in the `Containerfile` up to date.
