# tc-container-002 — Bundle missing `mimetype` entry

| Field | Value |
|---|---|
| **Test ID** | tc-container-002 |
| **Spec section** | Container Format § Required entries |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A conforming bundle MUST contain a `mimetype` entry at the archive root.

## Test bundle

A `.pweb` ZIP archive containing `manifest.json` and `index.html` but no `mimetype` file.

## Expected viewer behavior

The viewer MUST reject the bundle and MUST NOT attempt to load or execute any content from it.
