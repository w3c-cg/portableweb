# tc-manifest-002 — Manifest missing a required field is rejected

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-002 |
| **Spec section** | Manifest Schema and Capability Declaration § Required fields |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> The manifest MUST contain `spec_version`, `id`, `version`, `title`, and `entry`.

## Test bundle

A `.pweb` archive with a valid `mimetype` entry and a `manifest.json` missing one or more
required fields, e.g.:

```json
{
  "title": "No id, version, spec_version, or entry"
}
```

## Expected viewer behavior

The viewer MUST reject the bundle and MUST NOT attempt to load or execute any content from
it. The viewer SHOULD report which required field(s) are missing.

## Notes

A conforming validator should report *all* missing fields in one pass, not stop at the
first — useful for authoring tools (`pweb validate`, AI-generated bundle linting), not just
viewers. Reference implementation returns a list of every violation, not just the first.
