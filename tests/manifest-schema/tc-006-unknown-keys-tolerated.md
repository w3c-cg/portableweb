# tc-manifest-006 — Unknown manifest keys and permission names are tolerated

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-006 |
| **Spec section** | Manifest Schema and Capability Declaration |
| **Type** | Positive |
| **Status** | Draft |

## Requirement

> Future versions of this specification may define additional permission keys. Viewers MUST
> ignore unknown permission keys when the bundle targets a spec version the viewer supports.
> A viewer SHOULD similarly ignore unrecognized top-level manifest fields not required for
> safe processing.

## Test bundle

An otherwise-valid, minimal manifest with an extra unrecognized top-level field and a
`permissions` object containing a made-up permission name:

```json
{
  "spec_version": "0.1",
  "id": "org.example.hello",
  "version": "1.0.0",
  "title": "Hello",
  "entry": "index.html",
  "some_future_field": "ignored",
  "permissions": { "totally_made_up_permission": true }
}
```

## Expected viewer behavior

The viewer MUST open the bundle normally. Neither the unknown top-level field nor the
unrecognized permission name causes rejection — and critically, declaring an unrecognized
(or a recognized-but-viewer-unsupported) permission MUST NOT grant it. A viewer with no
implementation for a given capability must deny it exactly as if it hadn't been declared at
all — **declaration is never itself a grant.**

## Notes

This is the single most load-bearing conformance property in the whole format: it's what
lets a v0.1 viewer implementing zero optional capabilities remain fully conformant (rather
than "partially implemented") and what lets future spec versions add permission keys
without breaking older viewers. The reference implementation's fixture corpus calls the
all-permissions-declared-but-viewer-implements-none case out explicitly as a keystone test
(their `F12`) for exactly this reason — worth this suite adopting the same framing rather
than treating it as an ordinary tolerance check.
