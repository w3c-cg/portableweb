# tc-manifest-005 — Invalid `entry` path is rejected

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-005 |
| **Spec section** | Manifest Schema and Capability Declaration § Required fields |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> `entry` MUST be a path within the archive to the entry HTML file. It MUST end in `.html`
> or `.htm` and MUST NOT start with `/`.

## Test bundle

Three otherwise-valid bundles, each with a different invalid `entry` value:

1. `"entry": "/index.html"` — absolute path
2. `"entry": "index.js"` — wrong extension
3. `"entry": ""` — empty

## Expected viewer behavior

The viewer MUST reject each bundle.

## Notes

This is a manifest-*shape* check, independent of whether the referenced file actually
exists in the archive. A bundle can fail this check even if `index.html` genuinely exists
at the archive root, if the manifest itself points somewhere invalid.

**Related open question, not yet a test case here:** what a viewer MUST do when `entry` is
well-formed but the referenced file is *absent* from the archive — reject outright, or
render a defined error page — isn't decided yet (tracked as an open item in the reference
implementation's checklist). Worth a decision before a `tc-container-00X` for that case is
written.
