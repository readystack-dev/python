# Python 3.15.2 — ReadyStack release `3.15.2-CE-ubuntu24.04-r6`

Generated 2026-11-25 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/python:3.15.2-CE-ubuntu24.04-r6` (linux/amd64). Index digest `sha256:46d2d1ab93a527803172587dac8022bed485cdc97eaa37ba4f27022a6c61cb4d` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:0618c30e949f3999fe740e261d61afb259fc8a73dbac8c30700816fb355ac9fc` [`TARGET_DIGEST.txt`].
- **Upstream:** Python 3.15.2 built from source at `v3.15.2` of https://github.com/python/cpython — upstream notes: https://github.com/python/cpython/releases/tag/v3.15.2 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** `ubuntu:24.04`; runtime user `python`.
- **Build:** `source-rebuild-python`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `3.15.2-CE-ubuntu24.04-r5`.

## What changed in this release

- Upstream version unchanged (3.15.2); ReadyStack rebuild.
- Minimum dependency versions ReadyStack enforces on top of upstream (raised only where upstream's own version was lower); shipped versions from the SBOM [`docs/sbom/SBOM.json`]:
  - `pip` at least `26.3` (shipped: `26.3`)
- Python 3.15.2 is unchanged from the release this supersedes (3.15.2-CE-ubuntu24.04-r5); this release rebuilds it. Changes: libexpat1 moves from 2.6.1-2ubuntu0.6 to 2.6.1-2ubuntu0.7 (USN-9196-1). Settings are those of 3.15.2-CE-ubuntu24.04-r5. The image keeps no data and uses no volumes: run this image in place of the old one with the same arguments.

## Security status at release (measured 2026-11-25)

- **Docker Scout:** 0 fixable critical/high vulnerabilities; runs as `python` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/python:3.15.2-CE-ubuntu24.04-r6` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:0618c30e949f3999fe740e261d61afb259fc8a73dbac8c30700816fb355ac9fc`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 11 of 11 use cases passed (11 authored) against a container of this image started with `sleep infinity` after the image name instead of the image's default command (`python3`) [`docs/validation/test-results.json`]. A container started the default way can answer differently.

## Known issues

- None found (reviewed by held semantic review (Claude) on 2026-11-25).

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/python:3.15.2-CE-ubuntu24.04-r6
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

