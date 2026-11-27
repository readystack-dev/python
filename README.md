# Python: ReadyStack build kit

The offline build kit for the Docker image `readystack/python:3.15.2-CE-ubuntu24.04-r6`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [3.15.2-CE-ubuntu24.04-r6](https://github.com/readystack-dev/python/releases/tag/3.15.2-CE-ubuntu24.04-r6)
- Image: [`docker.io/readystack/python:3.15.2-CE-ubuntu24.04-r6`](https://hub.docker.com/r/readystack/python/tags), manifest digest `sha256:0618c30e949f3999fe740e261d61afb259fc8a73dbac8c30700816fb355ac9fc`
- Product page: https://readystack.dev/products/python
- Source and build recipe: https://readystack.dev/products/python/recipe
- Build trail: https://readystack.dev/products/python/trail/3.15.2-CE-ubuntu24.04-r6
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=python

## The image

A language runtime image: use it as the FROM base of your own image, or run a script with `docker run --rm`. It runs no service.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-25 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 87 packages with copyleft licences (GPL, LGPL, MPL), all of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`python`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-25; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/python.

Python is distributed under its upstream licence (Python-2.0); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [3.15.2-CE-ubuntu24.04-r6 release](https://github.com/readystack-dev/python/releases/tag/3.15.2-CE-ubuntu24.04-r6): `ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.tar.gz` (324.6 MB), SHA-256 `8d212699ff592a2248d9af2b54e6e369e3980e3862312698254d4a70b82f9d34`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.rebuild.json.sigstore ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.tar.gz
cd 3.15.2-CE-ubuntu24.04-r6
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/python/recipe. The complete kit is the release download. Each release is a tag here.

— ReadyStack · https://readystack.dev
