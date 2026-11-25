# changedetection.io 0.70.4 — ReadyStack release `0.70.4-CE-ubuntu24.04-r2`

Generated 2026-11-25 from this release's build records and strategy. Statements that come from a single record name it in brackets; the others come from this release's strategy and build log.

## Release

- **Image:** `readystack/changedetection:0.70.4-CE-ubuntu24.04-r2` (linux/amd64). Index digest `sha256:fedbcf6fea3056da0e172a4bc6ad821aae7afb194ddad566c4e3f716625c9be9` [`docs/provenance/LOCKED_DIGEST.txt`].
- **Image manifest digest:** `sha256:779b99996967cfecfb493af1464d6feb2ab966155ec47dbaeef103579a342ad2` [`TARGET_DIGEST.txt`].
- **Upstream:** changedetection.io 0.70.4 built from source at `0.70.4` of https://github.com/dgtlmoon/changedetection.io — upstream notes: https://github.com/dgtlmoon/changedetection.io/releases/tag/0.70.4 [`docs/provenance/BUILD_RECIPE.json`].
- **Base image:** `ubuntu:24.04`; runtime user `changedetection`.
- **Build:** `source-rebuild-python`, compiled offline with `--network=none`.
- **Supersedes:** ReadyStack release `0.70.4-CE-ubuntu24.04-r1`.

## What changed in this release

- Upstream version unchanged (0.70.4); ReadyStack rebuild.
- changedetection.io 0.70.4 is unchanged from the release this supersedes (0.70.4-CE-ubuntu24.04-r1); this release rebuilds it. Changes: libssh-4 moves from 0.10.6-2ubuntu0.5 to 0.10.6-2ubuntu0.6 (USN-9187-1). Settings, ports and data volumes are those of 0.70.4-CE-ubuntu24.04-r1: replace the container with this image on the same volumes.

## Security status at release (measured 2026-11-25)

- **Docker Scout:** 0 fixable critical/high vulnerabilities; runs as `changedetection` (non-root); SBOM + provenance attestations present (SPDX SBOM + SLSA v1) [`docs/provenance/SCOUT_VERDICT.json`].
- **OSV cross-check:** no fixable critical/high vulnerability beyond Docker Scout's findings.
- **Signature:** cosign signature verified by ReadyStack's release gate before publishing; check it yourself with `cosign verify --key https://readystack.dev/keys/cosign.pub readystack/changedetection:0.70.4-CE-ubuntu24.04-r2` (signatures are recorded in the public Sigstore transparency log).
- **ReadyStack release check at release:** passed (ReadyStack's own test, not a Docker Scout grade). Vulnerabilities are disclosed every day and the image never changes, so it is re-checked daily, beside Docker Scout's own dated grade, at https://readystack.dev/queue.
- **Before exposing this service:** The web UI has no password by default. Set one under Settings before the port is reachable by anyone else: a user of the UI can make the container fetch URLs and read the results.
- **Before exposing this service:** Keep ALLOW_IANA_RESTRICTED_ADDRESSES unset unless you need to watch internal services; enabling it lets UI users probe your private network through the container.

## Reproducibility

Rebuilds offline from this archive to the identical image digest `sha256:779b99996967cfecfb493af1464d6feb2ab966155ec47dbaeef103579a342ad2`: run `./BUILD_OFFLINE.sh`, then `./VERIFY_OFFLINE.sh` (add `--online` to confirm the Docker Hub tag holds the same digest). Before publishing, ReadyStack rebuilt the kit with `./BUILD_OFFLINE.sh` and compared the result with the published digest [`docs/provenance/REPRO_VERIFICATION.json`], then ran `./BUILD_OFFLINE.sh` and `./VERIFY_OFFLINE.sh` from this archive (without `--online`).

## Validation

- 3 of 3 use cases passed (3 authored) against the running image [`docs/validation/test-results.json`].
- The cases are `GET /` (200), `GET /queue-status` (200), `GET /worker-health` (200); the suite checks nothing else.

## Known issues

- **high** (upstream): Unauthenticated access by default [`RSD-changedetection-59cd53012e`]
- **low** (ReadyStack package): The Fetch Method choice offers WebDriver Chrome/Javascript, but the image lacks the Python imaging library (PIL) that fetcher needs: a watch set to it fails every check with `No module named 'PIL'` [`RSD-changedetection-58c4a9e151`] (carried from `0.60.9-CE-ubuntu24.04-r1`, recorded there as `RSD-changedetection-8f2c10b649`)
- **low** (ReadyStack package): The image sets LC_ALL=en_US.UTF-8 but contains no en_US.UTF-8 locale (only C, C.utf8 and POSIX), so the setting has no effect and every start logs a locale warning [`RSD-changedetection-65011c9fa2`] (carried from `0.60.9-CE-ubuntu24.04-r1`, recorded there as `RSD-changedetection-8f2c10b649`)
- **low** (ReadyStack package): Admin handbook: The route list presented as the endpoints this release serves omits GET /api/v1/changes, which the routing table declares and the API answers. [`RSD-changedetection-a8dd4ec177`] (carried from `0.70.4-CE-ubuntu24.04-r1`, recorded there as `RSD-changedetection-898ac808dd`)
- **low** (ReadyStack package): Database handbook: The route list presented as the endpoints this release serves omits GET /api/v1/changes, which the routing table declares and the API answers. [`RSD-changedetection-8738fb296c`] (carried from `0.70.4-CE-ubuntu24.04-r1`, recorded there as `RSD-changedetection-f76eef9dba`)
- **low** (ReadyStack package): Admin handbook: The route list presented as the endpoints this release serves omits GET /api/v1/changes, which the routing table declares and the API answers. [`RSD-changedetection-5a6614c9d2`] (carried from `0.70.4-CE-ubuntu24.04-r1`, recorded there as `RSD-changedetection-8b9107fb4b`)

## Verify this archive

```
sha256sum -c CHECKSUMS.sha256
./BUILD_OFFLINE.sh && ./VERIFY_OFFLINE.sh --online
cosign verify --key https://readystack.dev/keys/cosign.pub readystack/changedetection:0.70.4-CE-ubuntu24.04-r2
```

ReadyStack records every signature in the public Sigstore transparency log (Rekor), so the command needs no extra flags.

