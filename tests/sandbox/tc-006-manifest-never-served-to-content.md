# tc-sandbox-006 — `manifest.json` and `mimetype` are never served to bundle content

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-006 |
| **Spec section** | Container and Packaging Format § Reserved paths; Viewer Conformance and Security Sandboxing |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> The manifest is parsed by the viewer's privileged host code only. Manifest bytes MUST NOT
> be served to, or otherwise reachable by, bundle content — even via an ordinary in-bundle
> resource request.

## Test bundle

A bundle whose entry script issues `fetch("manifest.json")` and `fetch("mimetype")` against
its own origin (not a traversal attempt — these are legitimate top-level archive entries,
requested by their real, unmodified names).

## Expected viewer behavior

Both requests MUST fail (e.g. a 403/404-equivalent response) — the reserved-path
restriction applies to ordinary same-directory requests, not only to path-traversal
attempts. This is distinct from container-level path traversal (already covered elsewhere in
this suite): here the request path is exactly correct and unmodified, and is still refused
because of *what* it names, not *how* it's phrased.

## Notes

Easy to under-test: a viewer might correctly reject `../../etc/passwd`-style traversal while
still accidentally serving `manifest.json` itself to a plain `fetch()` call, since nothing
about that request looks like an attack. Worth its own test case rather than assuming
traversal coverage implies this too.
