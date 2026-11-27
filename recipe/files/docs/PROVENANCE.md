# Provenance — Python (`3.15.2-CE-ubuntu24.04-r6`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/python/cpython
- Revision built: `v3.15.2` (commit `5e58eaad7c58df58dfa8ea549c87996e01dd1077`)
- Source tree: `c39e6ce79eef9148fe893ee08e13bf6cd2350f8549c20587afeed3c639740352` over 5636 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-python`; base image `ubuntu:24.04`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795644296` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/python:3.15.2-CE-ubuntu24.04-r6` — index digest `sha256:46d2d1ab93a527803172587dac8022bed485cdc97eaa37ba4f27022a6c61cb4d` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:0618c30e949f3999fe740e261d61afb259fc8a73dbac8c30700816fb355ac9fc` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/python:3.15.2-CE-ubuntu24.04-r6`

## Pinned inputs, and why

- 16 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 1, image digests 1, language runtimes and toolchains 1, dependency versions readystack sets 5, components from other repositories 1, pins in the kit's dockerfiles 2, readystack's build engine 1, dependencies upstream chose 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.trail.json`, published beside this archive and signed with the release key (`ReadyStack-python-3.15.2-CE-ubuntu24.04-r6.trail.json.sigstore`), and readable at https://readystack.dev/products/python/trail/3.15.2-CE-ubuntu24.04-r6.

