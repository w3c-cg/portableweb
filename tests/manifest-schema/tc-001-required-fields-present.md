# tc-manifest-001 — Minimal valid manifest opens

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-001 |
| **Spec section** | Manifest Schema and Capability Declaration § Required fields |
| **Type** | Positive |
| **Status** | Draft |

## Requirement

> The manifest MUST contain `spec_version`, `id`, `version`, `title`, and `entry`.

## Test bundle

A `.pweb` archive with a valid `mimetype` entry and a `manifest.json` containing only the
five required fields (no recommended fields):

```json
{
  "spec_version": "0.1",
  "id": "org.example.minimal",
  "version": "1.0.0",
  "title": "Minimal Example",
  "entry": "index.html"
}
```

## Expected viewer behavior

The viewer MUST open the bundle and load `index.html`.

## Notes

Reference implementation: `@portableweb/core`'s `validateManifest()`
(`packages/core/src/manifest.ts` in the `portableweb/viewer` repo) enforces
exactly these five fields as required; the example above is byte-identical
to `MANIFEST.md`'s own "minimal valid manifest" example. Covered by an
automated test (`packages/core/test/manifest.test.ts`).
