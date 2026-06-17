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

Currently active: **Goal 1 — Container and packaging format**

Goals 2–5 are stubs; test cases will be added as the corresponding spec sections are written.
