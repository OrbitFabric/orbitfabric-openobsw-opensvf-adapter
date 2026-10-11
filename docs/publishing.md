# Maintainer / Publisher Guide

Current published release: [`v0.1.1`](https://github.com/OrbitFabric/orbitfabric-openobsw-opensvf-adapter/releases/tag/v0.1.1) (2026-09-25). See [0.1.1 release notes](releases/0.1.1.md). Sections explicitly labeled `v0.1.0` preserve historical publisher evidence and its original FAROTECH release identity.

This section is for maintainers preparing, proving and publishing an adapter release.

It is intentionally separate from normal user installation. A consumer should install already-published release assets through OrbitFabric Adapter Manager and should never need to build the adapter wheel or Release Descriptor locally.

## Publisher responsibility

The publisher turns an accepted source commit into one immutable, verifiable release:

```text
accepted main commit
    -> release tag
    -> wheel
    -> Adapter Release Descriptor
    -> SHA256SUMS
    -> local verification
    -> draft GitHub Release
    -> immutable publication
    -> published-asset verification
    -> final external greenfield acceptance
    -> architecture evidence retention
```

For `v0.1.0`, the authoritative publisher-owned binary/material set is:

```text
orbitfabric_openobsw_opensvf_adapter-0.1.0-py3-none-any.whl
adapter-release.json
SHA256SUMS
release notes
```

The Project Lock is consumer-project state and is not publisher release membership.

## v0.1.0 completed publication

The first stable release completed the full publication sequence on **2026-09-03**.

Final status:

```text
P1-P13: PASS
immutable GitHub Release: PASS
GitHub release attestation: PASS
public Adapter Manager install: PASS
external greenfield acceptance: PASS
native OpenOBSW/OpenSVF closed loop: PASS
```

Detailed cross-repository publication evidence is retained separately in the OrbitFabric Architecture Lab. This repository keeps the reusable product, lifecycle and publisher guidance rather than release-specific audit records.

## Before publication

For future releases, the exact source commit selected for release must pass the release-relevant product controls, including:

```text
Python compatibility checks
Ruff
adapter consistency
unit and negative tests
wheel/package validation
MkDocs strict build
OpenOBSW native compatibility
OpenSVF native compatibility
installed Adapter Manager lifecycle
release / Project Lock proof
publisher release-only proof
product examples through Adapter Manager
native closed-loop evidence where claimed
```

Do not publish from a pull-request synthetic merge ref or from an unreviewed working tree.

The reusable publication sequence and boundaries are documented in [Release Lifecycle](release-lifecycle.md).

## v0.1.0 provenance boundary

The first release proves provenance through exact source and byte identity:

```text
accepted main commit
    + exact v0.1.0 tag
    + immutable GitHub Release
    + published SHA-256 values
    + Release Descriptor binding
    + GitHub-generated immutable-release attestation
```

`v0.1.0` does not introduce an adapter-authored signing scheme or an OrbitFabric-specific signature format.

GitHub's provider-generated release attestation is part of publication evidence. Any future adapter-authored signing or additional trust mechanism remains a separate capability with its own implementation and verification evidence.

## Release construction

From an accepted source commit:

```bash
python -m build --wheel

python tools/build_release_bundle.py \
  --wheel dist/orbitfabric_openobsw_opensvf_adapter-0.1.1-py3-none-any.whl \
  --authority github.com/OrbitFabric \
  --publisher orbitfabric \
  --name openobsw-opensvf \
  --release-only
```

This produces the publisher-owned Release Descriptor and checksum summary.

The command above describes the published `v0.1.1` release construction lane. For any future release, use the matching accepted source, version and artifact identity rather than reusing either `v0.1.0` or `v0.1.1` publication bytes.

## Publication and final acceptance

GitHub Releases is the first concrete publication backend for this adapter. Publication is complete only after the exact tag, immutable release state, published asset digests and provider-generated release attestation are verified.

Final acceptance must then be repeated from a new consumer workspace using the published assets rather than a locally built adapter bundle:

```text
install Core
    -> obtain published release assets
    -> Adapter Manager install
    -> verify
    -> execute product examples
    -> native downstream acceptance where claimed
```

For `v0.1.0`, that path has been completed successfully.

## Current consumer acquisition boundary

The published Core `v1.4.0` and GitHub Release Source `v0.1.0` support Catalog-based exact-release selection and provider acquisition, including this published adapter `v0.1.1`:

```text
Core Catalog exact selection
    -> GitHub Release Source acquisition and byte verification
    -> Adapter Manager install / verify
```

The earlier explicit-source path remains supported, including the historical `v0.1.0` acceptance route:

```text
manual GitHub Release asset acquisition
    -> Adapter Manager install / verify
```

The Catalog retains the exact historical FAROTECH identity; neither release is republished or reidentified.

## Publisher references

- [Release Lifecycle](release-lifecycle.md)
- [Adapter Readiness Checklist](adapter-readiness-checklist.md)
- [Evidence and Traceability](evidence-and-traceability.md)
- [Integration Coverage](integration-coverage.md)
- [Adapter Identity](adapter-identity.md)

The detailed release sequence remains in [Release Lifecycle](release-lifecycle.md). This page is the role-oriented entry point for maintainers and publishers.
