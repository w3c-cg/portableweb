# tc-storage-003 — Storage is isolated per `id`, not per file path or filename

| Field | Value |
|---|---|
| **Test ID** | tc-storage-003 |
| **Spec section** | Storage Model; Manifest Schema § Required fields |
| **Type** | Positive |
| **Status** | Draft |

## Requirement

> Storage MUST be scoped and isolated using the bundle's `id`, independent of the bundle's
> filename or file path on disk.

## Test bundle

Two copies of the *same* bundle (identical `manifest.json`, identical `id`), saved under two
different filenames (e.g. `my-app.pweb` and `my-app-copy.pweb`, or in two different
directories).

## Expected viewer behavior

A value written to storage while the bundle is open from one filename/path MUST be visible
when the identical-`id` bundle is opened from the other filename/path. Storage identity
follows `id`, never the filename.

## Notes

This is the flip side of `tc-sandbox-001` (two *different* `id`s never share storage): here,
two files with the *same* `id` are expected to intentionally share storage — renaming or
moving a `.pweb` file MUST NOT orphan its saved state, matching ordinary user expectations
("I renamed the file, my progress is still there").
