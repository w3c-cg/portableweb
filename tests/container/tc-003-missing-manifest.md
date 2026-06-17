# tc-container-003 — Bundle missing `manifest.json`

| Field | Value |
|---|---|
| **Test ID** | tc-container-003 |
| **Spec section** | Container Format § Required entries |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A conforming bundle MUST contain a `manifest.json` entry at the archive root.

## Test bundle

A `.pweb` ZIP archive containing a valid `mimetype` entry (first, uncompressed) and `index.html` but no `manifest.json`.

## Expected viewer behavior

The viewer MUST reject the bundle and MUST NOT attempt to load or execute any content from it.
