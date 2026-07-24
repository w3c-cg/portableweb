# PortableWeb Conformance Test Suite

This directory contains the conformance test suite for the PortableWeb format specification. Tests are organized by specification goal.

## Structure

```
tests/
  manifest.json          ← registry of all test cases
  container/             ← Goal 1: container and packaging format
  manifest-schema/       ← Goal 2: manifest schema and capability declaration
  sandbox/               ← Goal 3: viewer conformance and security sandboxing
  storage/               ← Goal 4: storage model
  inter-bundle/          ← Goal 5: inter-bundle communication
```

## Test case format

Each test case is a markdown file describing:

- **Test ID** — unique identifier (e.g. `tc-container-001`)
- **Spec section** — the normative requirement being tested
- **Test bundle** — description of the `.pweb` file to be used (positive or negative fixture)
- **Expected behavior** — what a conforming viewer MUST do
- **Type** — `positive` (valid bundle, must open) or `negative` (invalid bundle, must reject)

Test bundles (`.pweb` files) are generated using the `@portableweb/cli` tool from the [portableweb org](https://github.com/portableweb/cli). They are not committed as binary files; the test case description is the authoritative source.

## Reporting conformance

Viewer implementors report conformance by running each test case and noting the result. A conformance report template will be added in a future update.

## Status

Active, with draft test cases: **Goal 1 — Container** (4), **Goal 2 — Manifest schema** (6),
**Goal 3 — Sandbox** (6), **Goal 4 — Storage** (3). Goals 2–4's test cases were written
against a working reference implementation (`portableweb/viewer`'s `packages/core` and
`packages/electron`) rather than speculatively — see `status/2026-07-24.md` for what that
implementation actually covers versus what's still open.

**Goal 5 — Inter-bundle communication** remains a stub; no reference implementation exists
yet for this goal, so no test cases have been written against real behavior.

Note: `tc-sandbox-002` is called out in `manifest.json` as a **keystone** test — it validates
the conformance model itself (a viewer implementing zero optional capabilities is still
fully conformant, not partially so), not just one isolated feature. Prioritize this one if
only reviewing a subset.
