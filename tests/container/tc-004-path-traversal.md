# tc-container-004 — ZIP path traversal attack

| Field | Value |
|---|---|
| **Test ID** | tc-container-004 |
| **Spec section** | Security Considerations |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> Implementations MUST defend against ZIP-based attacks including path traversal via `../` sequences.

## Test bundle

A `.pweb` ZIP archive containing a valid `mimetype` and `manifest.json`, but also an entry with the path `../../malicious.js` (path traversal via `../`).

## Expected viewer behavior

The viewer MUST reject the bundle or MUST sanitize all entry paths before extraction, ensuring no file is written or accessible outside the bundle's isolated scope. The viewer MUST NOT allow the traversal path to resolve to a location outside the bundle root.
