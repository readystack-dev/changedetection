# Provenance — changedetection.io (`0.70.4-CE-ubuntu24.04-r2`)

Every item below is copied from a record in this archive; the record is named in brackets.

## Source

- Upstream repository: https://github.com/dgtlmoon/changedetection.io
- Revision built: `0.70.4` (commit `3316f256acc5bc01708c85da83b3ee7347c503d8`)
- Source tree: `c7676b461192b13c331a260d9ccf4e0236c321e67962515f3b1909c6cf9e6d48` over 1295 files [`docs/provenance/SOURCE_TREE_HASH.json`]
- Community Edition only: enterprise code is removed or refused before the build (CE audit at acquire).

## Build

- Method: `source-rebuild-python`; base image `ubuntu:24.04`
- Compiled with `--network=none` from vendored source, dependencies and base images; BuildKit pinned to `moby/buildkit:v0.31.2` (shipped in `toolchain/`).
- SOURCE_DATE_EPOCH: `1795543196` [`SOURCE_DATE_EPOCH.txt`]
- Frozen inputs: [`docs/provenance/FREEZE_MANIFEST.json`], build recipe: [`docs/provenance/BUILD_RECIPE.json`].

## Output

- Published image: `readystack/changedetection:0.70.4-CE-ubuntu24.04-r2` — index digest `sha256:fedbcf6fea3056da0e172a4bc6ad821aae7afb194ddad566c4e3f716625c9be9` [`docs/provenance/LOCKED_DIGEST.txt`]
- linux/amd64 image digest `sha256:779b99996967cfecfb493af1464d6feb2ab966155ec47dbaeef103579a342ad2` — reproduced from this archive before publishing [`docs/provenance/REPRO_VERIFICATION.json`].

## Attestations and signature

- SBOM + SLSA provenance attached to the image: attached: an SPDX SBOM and SLSA v1 provenance [`docs/provenance/SCOUT_VERDICT.json`]
- cosign signature by the ReadyStack release key: verified before publishing. Check it: `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/changedetection:0.70.4-CE-ubuntu24.04-r2`

## Pinned inputs, and why

- 24 pinned inputs, each with where it came from, why this one, how it was checked and when it was decided: `docs/PINS.md` [`docs/provenance/PINS.json`] (upstream source 2, base and build images 2, image digests 1, language runtimes and toolchains 1, dependency versions readystack sets 11, pins in the kit's dockerfiles 3, readystack's build engine 2, dependencies upstream chose 2).

## Build trail

- How this release passed through the ReadyStack harness, record by record (every chain, drive, stage, review round, defect and check, each naming the record it is copied from): `ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.trail.json`, published beside this archive and signed with the release key (`ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.trail.json.sigstore`), and readable at https://readystack.dev/products/changedetection/trail/0.70.4-CE-ubuntu24.04-r2.

