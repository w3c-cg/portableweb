# tc-sandbox-001 — Two bundles never share storage

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-001 |
| **Spec section** | Viewer Conformance and Security Sandboxing § Origin isolation |
| **Type** | Positive |
| **Status** | Draft |

## Requirement

> Each bundle MUST run in a synthetic isolated origin with no access to the viewer's storage,
> DOM, or execution context — and no access to any *other* bundle's storage.

## Test bundle

Two distinct bundles, `org.example.a` and `org.example.b`, each with `permissions.storage`
at its default (`"isolated"`), each writing a value to `localStorage` under the same key
name.

## Expected viewer behavior

Opening bundle `a`, writing `localStorage.setItem("k", "a-value")`, then opening bundle `b`
and reading `localStorage.getItem("k")` MUST return `null` (or `b`'s own independently
written value) — never `"a-value"`. This MUST hold even across viewer restarts, not just
within one running session.

## Notes

Reference implementation: the Electron viewer scopes each bundle to its own
`session.fromPartition('persist:bundle-<id>')` *and* its own on-disk store file keyed by
`manifest.id` — isolation is enforced at two independent layers, not just one. Verified
manually (two synthetic bundles produced separate storage directories on disk); not yet a
fully automated cross-bundle integration test.
