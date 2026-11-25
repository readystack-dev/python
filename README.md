# Python: ReadyStack build kit

The offline build kit for the Docker image `readystack/python:3.15.2-CE-ubuntu24.04-r5`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [3.15.2-CE-ubuntu24.04-r5](https://github.com/readystack-dev/python/releases/tag/3.15.2-CE-ubuntu24.04-r5)
- Image: [`docker.io/readystack/python:3.15.2-CE-ubuntu24.04-r5`](https://hub.docker.com/r/readystack/python/tags), manifest digest `sha256:3462077840ba492828e31c29d7670a9b8f59a72f01d2255f6bc0fe1e02c7698e`
- Product page: https://readystack.dev/products/python
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=python

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
