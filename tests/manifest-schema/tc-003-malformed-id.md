# tc-manifest-003 — Malformed `id` is rejected

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-003 |
| **Spec section** | Manifest Schema and Capability Declaration § Required fields |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> `id` MUST be a globally unique reverse-domain identifier (e.g. `"org.example.my-bundle"`) —
> lowercase, alphanumeric, dots, and hyphens only.

## Test bundle

An otherwise-valid bundle whose manifest `id` fails this shape, e.g. `"Not An ID!!"`,
`"nodots"` (missing the reverse-domain dot separator), or `"UPPERCASE.example"`.

## Expected viewer behavior

The viewer MUST reject the bundle.

## Notes

`id` is load-bearing beyond identity — it's the per-bundle storage isolation key (see the
storage test cases) and the synthetic origin discriminator
(`bundle://<id>/`). Accepting a malformed `id` risks storage-key collisions between bundles,
not just a cosmetic validation failure.
