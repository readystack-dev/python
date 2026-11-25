# Python 3.15.2 — ReadyStack release `3.15.2-CE-ubuntu24.04-r5`

Generated 2026-11-20 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/python:3.15.2-CE-ubuntu24.04-r5` (linux/amd64). Index digest `sha256:9d17459d72dc6845dfd4716155f71c8e03fbd8da35388794844bb0ad167a4a4a` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:3462077840ba492828e31c29d7670a9b8f59a72f01d2255f6bc0fe1e02c7698e` [`TARGET_DIGEST.txt`].
- **Upstream:** Python 3.15.2 built from source at `v3.15.2` of https://github.com/python/cpython — upstream notes: https://github.com/python/cpython/releases/tag/v3.15.2 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** `ubuntu:24.04`; runtime user `python`.
- **Build:** `source-rebuild-python`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `3.15.2-CE-ubuntu24.04-r4`.

## What changed in this release

- Upstream version unchanged (3.15.2); ReadyStack rebuild.
- Minimum dependency versions ReadyStack enforces on top of upstream (raised only where upstream's own version was lower); shipped versions from the SBOM [`docs/sbom/SBOM.json`]:
  - `pip` at least `26.3` (shipped: `26.3`)
- Python 3.15.2 is unchanged from the release this supersedes (3.15.2-CE-ubuntu24.04-r4); this release rebuilds it. Changes: the image is rebuilt on the current ubuntu:24.04 image (sha256:9c7f200c07e3…), which its maintainers updated after 3.15.2-CE-ubuntu24.04-r4 was built on sha256:2198e4c65076…. Settings, ports and data volumes are those of 3.15.2-CE-ubuntu24.04-r4: replace the container with this image on the same volumes.

## Security status at release (measured 2026-11-20)

- **Docker Scout:** 0 fixable critical/high vulnerabilities; runs as `python` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/python:3.15.2-CE-ubuntu24.04-r5` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:3462077840ba492828e31c29d7670a9b8f59a72f01d2255f6bc0fe1e02c7698e`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 11 of 11 use cases passed (11 authored) against a container of this image started with `sleep infinity` after the image name instead of the image's default command (`python3`) [`docs/validation/test-results.json`]. A container started the default way can answer differently.

## Known issues

- None found (reviewed by held semantic review (Claude) on 2026-11-20).

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/python:3.15.2-CE-ubuntu24.04-r5
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

