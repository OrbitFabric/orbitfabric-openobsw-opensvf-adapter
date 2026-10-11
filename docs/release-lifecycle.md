# Release Lifecycle

Current published release: [`v0.1.1`](https://github.com/OrbitFabric/orbitfabric-openobsw-opensvf-adapter/releases/tag/v0.1.1) (2026-09-25). See [0.1.1 release notes](releases/0.1.1.md). The historical `v0.1.0` publication and its original FAROTECH Source Coordinate remain unchanged.

This repository separates publisher release construction, consumer project selection and publication transport.

Reusable publication guidance is maintained here and in the [Maintainer / Publisher Guide](publishing.md).

## Historical v0.1.0 publication and acceptance

`v0.1.0` was published on **2026-09-03** as an immutable GitHub Release.

Post-publication verification has confirmed:

```text
exact v0.1.0 tag
immutable GitHub Release
published asset SHA-256 identities
GitHub-generated release attestation
Adapter Manager install / inspect / verify from public release assets
Examples 01 and 02 from the published adapter
native OpenOBSW/OpenSVF Closed-Loop Ping acceptance
```

The public greenfield run completed the native OpenSVF campaign with a 100% pass rate. Publication gates P1-P13 are complete, including final Architecture Lab evidence retention.

The `v0.1.0` public greenfield acceptance used explicit-source installation after downloading the published Release Descriptor and wheel. The current Core 1.4.0 / GitHub Release Source 0.1.0 onboarding also supports Catalog-based acquisition of exact published releases, including `v0.1.1`, without changing historical release identities.

## Historical stable source identity

The `0.1.0` source baseline declares:

```text
version:          0.1.0
logical key:      orbitfabric/openobsw-opensvf
source authority: github.com/FAROTECH
classification:   OrbitFabric-maintained stable adapter
```

Its semantic scope is the reviewed first-release scope recorded by the Integration Coverage Matrix. Source acceptance and publication of immutable release assets remain separate states.

The repository is public. The source version alone is not release identity: `v0.1.0` is established by the exact tag, immutable GitHub Release and published asset identities.

## Three distinct objects

```text
Adapter Release Descriptor
    publisher-owned exact release definition

Adapter Project Lock
    consumer-project exact selected resolution

GitHub Release
    first concrete storage, immutability and transport backend
```

These roles must remain separate.

## Build a release wheel

From the matching accepted source baseline (the example below is `v0.1.1`):

```bash
python -m build --wheel
```

Expected artifact name:

```text
orbitfabric_openobsw_opensvf_adapter-0.1.1-py3-none-any.whl
```

The wheel owns the namespaced package:

```text
orbitfabric_openobsw_opensvf_adapter
```

including its unique `integration_package.json`, Profile schema and target resources.

## Publisher-owned release construction

For release construction (shown for `v0.1.1`), use:

```bash
python tools/build_release_bundle.py \
  --wheel dist/orbitfabric_openobsw_opensvf_adapter-0.1.1-py3-none-any.whl \
  --authority github.com/OrbitFabric \
  --publisher orbitfabric \
  --name openobsw-opensvf \
  --release-only
```

This produces:

```text
adapter-release.json
SHA256SUMS
```

The `v0.1.1` publisher release membership is therefore:

```text
v0.1.1 tag
orbitfabric_openobsw_opensvf_adapter-0.1.1-py3-none-any.whl
adapter-release.json
SHA256SUMS
release notes
```

The release-only checksum file covers the exact wheel and Release Descriptor bytes.

The Integration Package Manifest digest is bound inside the Release Descriptor and the manifest bytes are packaged inside the wheel.

GitHub-generated source archives are provider conveniences and are not OrbitFabric adapter release membership.

## Project Lock lifecycle proof

The default tool mode additionally derives:

```text
adapter-project-lock.json
```

This is required for exact lifecycle proof:

```text
Source Coordinate
release version
Release Descriptor SHA-256
artifact id
artifact SHA-256
installation backend id
```

The permanent CI proves:

```text
initial state MISSING
    -> install exact release from lock
    -> MATCH
    -> second identical request NOOP / MATCH
    -> verify
    -> remove
    -> empty inventory
```

The lock used by CI is engineering evidence for a consumer selection. It is not canonical publisher release membership.

## Current published Source Coordinate

The post-migration `v0.1.1` release uses:

```text
authority = github.com/OrbitFabric
publisher = orbitfabric
name      = openobsw-opensvf
```

Rendered as the exact published Source Coordinate:

```text
github.com/OrbitFabric:orbitfabric/openobsw-opensvf
```

The authority identifies the concrete post-migration source context; it does not define GitHub as a universal OrbitFabric registry. The earlier `v0.1.0` release retains the historical `github.com/FAROTECH:orbitfabric/openobsw-opensvf` Source Coordinate.

A future source authority may change without changing the logical product key:

```text
orbitfabric/openobsw-opensvf
```

## Stable validation gates

The exact `0.1.0` source baseline must pass:

```text
Python 3.11 / 3.12
Ruff
adapter consistency
unit and negative tests
wheel/package validation
MkDocs strict build
OpenOBSW / SRDB native compatibility
OpenSVF native compatibility
installed Adapter Manager lifecycle
Release Descriptor / Project Lock proof
release-only publisher artifact proof
product examples through Adapter Manager
native closed-loop acceptance evidence
```

Core conformance and downstream-native acceptance remain separate evidence layers.

## v0.1.0 provenance boundary

The first release proves release provenance through exact source and byte identity plus the provider-generated immutable-release record:

```text
accepted main commit
    + exact v0.1.0 tag
    + immutable GitHub Release
    + exact published SHA-256 values
    + Release Descriptor binding to the wheel and packaged manifest
    + GitHub-generated release attestation
```

`v0.1.0` does not introduce an adapter-authored signing scheme or an OrbitFabric-specific signature format.

GitHub Immutable Releases automatically generate a cryptographically verifiable release attestation containing the release tag, commit SHA and release assets. That attestation is provider-owned publication evidence and is verified after publication alongside exact asset digests.

Any future adapter-authored signing or additional trust mechanism remains a separate capability with its own implementation and evidence.

## GitHub publication boundary

GitHub Releases is the first concrete publication backend for this adapter.

The `v0.1.0` publication and acceptance sequence is:

```text
1. merge the exact green publication-preparation candidate
2. record the accepted main source commit
3. confirm the release-relevant CI on that accepted commit
4. confirm GitHub Immutable Releases configuration
5. create v0.1.0 against the exact accepted source commit
6. build the definitive wheel, adapter-release.json and SHA256SUMS from that source
7. verify the definitive asset digests and Release Descriptor locally
8. create v0.1.0 as a draft GitHub Release
9. attach only the definitive wheel, adapter-release.json and SHA256SUMS
10. verify the draft tag, release notes and uploaded/downloaded asset digests
11. publish the verified draft under the immutable-release policy
12. confirm final immutable release state
13. verify tag -> intended stable commit
14. download the public assets and re-verify their digests
15. verify the GitHub-generated release attestation
16. repeat the external greenfield consumer acceptance from published assets
17. retain final Architecture Lab publication evidence
```

All 17 steps are complete for `v0.1.0`; final publication evidence is retained in Architecture Lab Evidence 046.

All normative assets must be attached and verified before immutable publication because the release must not rely on post-publication mutation.

GitHub release URLs and the generated release attestation are provider publication metadata/evidence. They do not replace the OrbitFabric Release Descriptor.

## Release classification

`0.1.0` is an:

```text
OrbitFabric-maintained stable adapter
```

It is intentionally not yet called a registry-classified official OrbitFabric adapter.

The technical release has strong conformance, compatibility, immutability and provenance requirements. Formal official classification remains tied to future promoted publisher/source-authority governance rather than being self-declared by release bytes.

## Source provenance

Released source provenance must identify the exact stable source commit.

Do not use a synthetic pull-request merge ref as normative release provenance.

The final tag and definitive release build must operate from the accepted stable commit.

The exact tag-to-commit association, published asset digests and GitHub-generated release attestation are retained as publication evidence.

## External greenfield acceptance

The `v0.1.0` external greenfield acceptance is complete.

The final acceptance did not rebuild or source-install the adapter. It followed the published distribution path:

```text
install OrbitFabric Core
    -> download public v0.1.0 release assets
    -> verify SHA256SUMS
    -> Adapter Manager install
    -> inspect / verify
    -> execute product examples
    -> native closed-loop acceptance
```

The adapter repository source archive was used only to obtain product example inputs and runner scripts. The adapter installation bytes came from the public immutable GitHub Release.

## Evidence

The `release-proof` CI job retains two related evidence sets.

### Lifecycle evidence

```text
Adapter Release Descriptor
Project Lock used by the proof
SHA-256 summary
Adapter Manager before/install/check/verify/remove reports
```

### Publisher-release evidence

```text
stable wheel
adapter-release.json
release-only SHA256SUMS
```

Architecture Lab evidence retains:

```text
accepted source commit
exact v0.1.0 tag association
immutable GitHub Release identity/state
published asset SHA-256 values
GitHub-generated release attestation verification
post-publication Adapter Manager verification
external greenfield product-example evidence
```
