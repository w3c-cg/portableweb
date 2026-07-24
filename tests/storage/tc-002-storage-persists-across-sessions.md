# tc-storage-002 — Storage persists across viewer sessions for the same bundle `id`

| Field | Value |
|---|---|
| **Test ID** | tc-storage-002 |
| **Spec section** | Storage Model |
| **Type** | Positive |
| **Status** | Draft |

## Requirement

> Storage for a bundle MUST persist across viewer restarts, scoped and retrieved by the
> bundle's `id` — not just for the lifetime of one open window.

## Test bundle

A bundle (default `permissions.storage`, i.e. `"isolated"`) whose entry script writes a
value to `localStorage` on first load, then reads it back and displays it.

## Expected viewer behavior

Writing a value, fully closing the bundle/viewer, then reopening the *same* bundle file (or
a different copy of a bundle with the same manifest `id`) MUST make the previously written
value available via `localStorage.getItem`.

## Notes

"Same manifest `id`" is the operative identity, not "same file on disk" — re-opening a
byte-identical copy of the bundle (e.g. re-downloaded, or opened from a different path) MUST
see the same storage, since `id` — not the file path — is the storage key. Conversely,
re-generating a bundle with a *new* `id` (e.g. an AI tool regenerating "the same" content
without deliberately carrying the `id` forward) MUST NOT see the old storage — worth a
companion note in the Storage Model section once authoring-tool guidance is written, since
this is an easy way to silently orphan a user's data.
