# tc-sandbox-004 — Top-level navigation away from the bundle is blocked

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-004 |
| **Spec section** | Viewer Conformance and Security Sandboxing |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A viewer MUST prevent active content from escaping the sandbox through navigation... or
> same-origin confusion.

## Test bundle

A bundle whose entry HTML contains a link or script-driven navigation
(`location.href = "https://example.com"` or `<a href="https://example.com">`) targeting an
external URL.

## Expected viewer behavior

The viewer MUST NOT navigate the bundle's view to the external URL. External links MAY be
surfaced to the user as an explicit "open in your default browser?" prompt, but silent or
automatic navigation away from the bundle's own content MUST NOT occur.

## Notes

Distinct from `tc-sandbox-003` (popups/new windows) — this covers navigating the *existing*
view away from the bundle, which is the more damaging escape since it can look like the
bundle itself redirected the user without any new-window signal to notice.
