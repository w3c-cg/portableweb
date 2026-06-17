# tc-container-001 — `mimetype` must be the first ZIP entry

| Field | Value |
|---|---|
| **Test ID** | tc-container-001 |
| **Spec section** | Container Format § Required entries |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> The `mimetype` file MUST be the first entry in the archive.

## Test bundle

A `.pweb` ZIP archive where `manifest.json` appears as the first entry and `mimetype` appears second.

## Expected viewer behavior

The viewer MUST reject the bundle and MUST NOT attempt to load or execute any content from it. The viewer SHOULD display an error indicating the bundle is invalid.

## Notes

This mirrors the EPUB convention. The placement allows `file(1)` and other magic-byte sniffers to identify the format by reading the first ~80 bytes of the file.
