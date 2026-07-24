# tc-storage-001 — `storage: "none"` denies access with ordinary web-platform semantics

| Field | Value |
|---|---|
| **Test ID** | tc-storage-001 |
| **Spec section** | Manifest Schema § Capability declaration and permissions; Storage Model |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A bundle declaring `"permissions": { "storage": "none" }` MUST have no persistent storage
> available. Denial MUST be indistinguishable from ordinary web-platform storage denial
> (e.g. `SecurityError`), not a novel PortableWeb-specific error type.

## Test bundle

A bundle with `"permissions": { "storage": "none" }` whose entry script calls
`localStorage.setItem("k", "v")` (or merely accesses `localStorage`).

## Expected viewer behavior

Accessing `localStorage` MUST throw — matching the same error a browser raises for storage
access in a sandboxed context without `allow-same-origin` (a `SecurityError` DOMException,
not a bespoke error).

## Notes

The "ordinary web-platform denial, never a novel error type" property matters beyond this
one API: it means bundle authors' existing error-handling code (written against normal
browser storage-denial behavior, e.g. private-browsing mode) already covers the
undeclared/denied case, with no PortableWeb-specific code path required.
