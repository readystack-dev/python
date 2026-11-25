# Python: ReadyStack build kit

The offline build kit for the Docker image `readystack/python:3.15.2-CE-ubuntu24.04-r5`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [3.15.2-CE-ubuntu24.04-r5](https://github.com/readystack-dev/python/releases/tag/3.15.2-CE-ubuntu24.04-r5)
- Image: [`docker.io/readystack/python:3.15.2-CE-ubuntu24.04-r5`](https://hub.docker.com/r/readystack/python/tags), manifest digest `sha256:3462077840ba492828e31c29d7670a9b8f59a72f01d2255f6bc0fe1e02c7698e`
- Product page: https://readystack.dev/products/python
- Source and build recipe: https://readystack.dev/products/python/recipe
- Build trail: https://readystack.dev/products/python/trail/3.15.2-CE-ubuntu24.04-r5
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=python

## The image

A language runtime image: use it as the FROM base of your own image, or run a script with `docker run --rm`. It runs no service.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-20 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 87 packages with copyleft licences (GPL, LGPL, MPL), all of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`python`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-20; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/python.

Python is distributed under its upstream licence (Python-2.0); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [3.15.2-CE-ubuntu24.04-r5 release](https://github.com/readystack-dev/python/releases/tag/3.15.2-CE-ubuntu24.04-r5): `ReadyStack-python-3.15.2-CE-ubuntu24.04-r5.tar.gz` (324.6 MB), SHA-256 `4a8285355d4fd7262a462e253c98533b2b3b27702b421caaa1562488cd200a40`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-python-3.15.2-CE-ubuntu24.04-r5.rebuild.json.sigstore ReadyStack-python-3.15.2-CE-ubuntu24.04-r5.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-python-3.15.2-CE-ubuntu24.04-r5.tar.gz
cd 3.15.2-CE-ubuntu24.04-r5
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-python-3.15.2-CE-ubuntu24.04-r5.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/python/recipe. The complete kit is the release download. Each release is a tag here.

— ReadyStack · https://readystack.dev
