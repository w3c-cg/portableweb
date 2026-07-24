# tc-sandbox-005 — Service worker registration is permanently denied, not a grantable permission

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-005 |
| **Spec section** | Viewer Conformance and Security Sandboxing § Blocked APIs |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> Bundle content MUST NOT be able to register a service worker, under any circumstances —
> this is a fixed property of a conforming viewer, not a permission a manifest can request or
> a viewer can choose to grant.

## Test bundle

A bundle whose entry script calls `navigator.serviceWorker.register("sw.js")`.

## Expected viewer behavior

The call MUST fail (e.g. `navigator.serviceWorker` is `undefined`, or `register()` rejects).
No manifest permission key exists, or should ever exist, that changes this outcome.

## Notes

Worth stating explicitly and permanently in the spec, not just as an implementation detail:
service workers can outlive the page, intercept requests for other resources under the same
scope, and persist across sessions in ways that are very hard to reason about for an
archival, sandboxed format — this is categorically different from the other capabilities in
the permissions table (which are merely default-off) and shouldn't be modeled as one more
row in that table with a `false` default. The reference implementation encodes this as an
unconditional override at the JS-API level (`navigator.serviceWorker = undefined`),
independent of its permission-handling code path entirely — worth the spec being equally
unambiguous that this is a different *kind* of restriction, not just a stricter default.
