# Sandbox and Viewer Conformance Tests

Test cases for **Goal 3: Viewer conformance requirements and security sandboxing model**.

6 draft test cases, written against a working reference implementation
(`portableweb/viewer`'s Electron adapter, verified to actually open a bundle end-to-end and
enforce these), covering:

- `tc-001` — two bundles never share storage (origin isolation)
- `tc-002` — **keystone**: declaring a permission the viewer doesn't implement still denies
  it — the test that validates the conformance model itself, not just one feature
- `tc-003` — popups/new windows are always blocked
- `tc-004` — top-level navigation away from the bundle is blocked
- `tc-005` — service worker registration is permanently denied (not a grantable permission)
- `tc-006` — `manifest.json`/`mimetype` are refused even via an ordinary, non-traversal
  resource request

Not yet covered here (either not implemented by the reference viewer, or not yet tested
even where implemented): CSP header contents as a *tested* requirement (the reference
implementation has one, but this suite doesn't yet pin down what it must contain);
decompression-bomb / duplicate-filename ZIP protections (`CONTAINER.md` §10 lists these as
SHOULDs — the reference implementation doesn't defend against them yet, so no test case
claims it does); filesystem/surveillance-API blocking beyond what's covered by
`tc-sandbox-002`'s general capability-denial mechanism.
