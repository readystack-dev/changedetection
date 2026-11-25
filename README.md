# changedetection.io: ReadyStack build kit

The offline build kit for the Docker image `readystack/changedetection:0.70.4-CE-ubuntu24.04-r2`. It holds what the image is built from (upstream source, base images, toolchain, pinned dependencies) and the documents, so the image can be rebuilt with no network access (`docker build --network=none`).

- Release: [0.70.4-CE-ubuntu24.04-r2](https://github.com/readystack-dev/changedetection/releases/tag/0.70.4-CE-ubuntu24.04-r2)
- Image: [`docker.io/readystack/changedetection:0.70.4-CE-ubuntu24.04-r2`](https://hub.docker.com/r/readystack/changedetection/tags), manifest digest `sha256:779b99996967cfecfb493af1464d6feb2ab966155ec47dbaeef103579a342ad2`
- Product page: https://readystack.dev/products/changedetection
- Source and build recipe: https://readystack.dev/products/changedetection/recipe
- Build trail: https://readystack.dev/products/changedetection/trail/0.70.4-CE-ubuntu24.04-r2
- Defects: this repository's Issues (defects recorded from 25 November 2026 on) and https://readystack.dev/defects.html?product=changedetection

## The image

Single container. A Python (Flask) self-hosted web-page change-monitoring + notification service. State is JSON (changedetection.json/watch.json) + text history snapshots (brotli-compressed when larger than 20 KB) under /datastore — there is NO SQL database. The image IS the complete running instance (no external DB, no sidecar). The default html_requests fetcher (plain HTTP requests) is the only fetcher that works in this hermetic CE image: Playwright is not installed, and the WebDriver Chrome/Javascript fetch method that the UI offers fails every check with `No module named 'PIL'`, even with a WebDriver server set in WEBDRIVER_URL.

## Who uses changedetection.io and why

People and teams who watch web pages for changes to prices, stock levels, job listings or policies.

changedetection.io checks web pages on a schedule you set, can watch only the part of a page you choose, and sends a notification when that content changes.

A typical use: A small shop tracks the prices its suppliers publish. changedetection.io checks each supplier page during business hours, watches only the price element picked with a CSS selector, and sends an email or webhook when it changes, so nobody has to reload the pages by hand.

From the upstream project's own description: https://github.com/dgtlmoon/changedetection.io.

## This release

- Docker Scout policy grade at release: **A** (94%), graded 2026-11-25 with `docker scout policy` (CLI 1.26.0, docker-default configuration).
  - Docker Scout counts 120 packages with copyleft licences (EPL, GPL, LGPL, MPL), 116 of them operating-system packages (it counts only packages whose licence it can read; the SBOM lists every component).
- Signed with ReadyStack's release key (fingerprint `04daa92344a52dbc`): https://readystack.dev/keys/cosign.pub.
- Runs as a non-root user (`changedetection`).
- Attestations on the image: an SPDX SBOM and SLSA provenance v1.
- Rebuilt from this kit with network egress blocked on 2026-11-25; the rebuilt image digest is the published one.
- Base: Ubuntu 24.04.

The current grade, measured again every day, is on https://readystack.dev/products/changedetection.

changedetection.io is distributed under its upstream licence (Apache-2.0); the kit contains upstream's source under that licence, and each vendored component under its own.

## Download

From the [0.70.4-CE-ubuntu24.04-r2 release](https://github.com/readystack-dev/changedetection/releases/tag/0.70.4-CE-ubuntu24.04-r2): `ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.tar.gz` (416.0 MB), SHA-256 `3dfd003ecc1a2baa4543aada5d39e0722d5675679e1a68217f906e0f2576eb84`.

```sh
sha256sum --check --ignore-missing SHA256SUMS
```

## Verify and rebuild

The rebuild statement is signed with the ReadyStack release key. Check the signature before you rely on it:

```sh
cosign verify-blob --key https://readystack.dev/keys/cosign.pub \
  --bundle ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.rebuild.json.sigstore ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.rebuild.json
```

Unpack with `-p` so file modes are kept, then follow the kit's own README.md and docs/REBUILD.md:

```sh
tar -xpzf ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.tar.gz
cd 0.70.4-CE-ubuntu24.04-r2
less README.md docs/REBUILD.md
```

The build trail (`ReadyStack-changedetection-0.70.4-CE-ubuntu24.04-r2.trail.json`, signed the same way, and its Markdown copy) records how this release was built and checked.

## This repository

`recipe/` holds the kit's recipe files (Dockerfiles, build scripts, pins) as published at https://readystack.dev/products/changedetection/recipe. The complete kit is the release download. Each release is a tag here.

— ReadyStack · https://readystack.dev
