# tc-sandbox-003 — Popups and new windows are always blocked

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-003 |
| **Spec section** | Viewer Conformance and Security Sandboxing |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A viewer MUST prevent active content from escaping the sandbox through navigation, popups,
> downloads, same-origin confusion, or unrestricted access to host-provided APIs.

## Test bundle

A bundle whose entry script calls `window.open("https://example.com")` on load.

## Expected viewer behavior

The call MUST NOT result in a new window or tab being opened, with or without a declared
`internet.read`/`internet.write` permission — this is a Core-class, always-on restriction,
not something any permission can lift.

## Notes

Reference implementation blocks this via `setWindowOpenHandler` returning a deny action,
independent of and in addition to the CSP/network layer that would separately block the
destination URL itself — belt-and-braces, matching the container security section's general
posture of not relying on a single enforcement point.
