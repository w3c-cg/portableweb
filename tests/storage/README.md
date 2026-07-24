# Storage Model Tests

Test cases for **Goal 4: Per-bundle isolated storage model**.

3 draft test cases, written against a working reference implementation (a `localStorage`
shim + per-bundle store in `portableweb/viewer`), covering:

- `tc-001` — `storage: "none"` denies access with ordinary web-platform semantics (not a
  novel error type)
- `tc-002` — storage persists across viewer sessions, keyed by manifest `id`
- `tc-003` — storage is isolated by `id`, not by filename/path — two files with the same
  `id` intentionally share storage

**Not yet covered here — genuinely unimplemented, not just untested:**
- Storage quota behavior — no quota enforcement exists yet.
- `exportData()` / `importData()` portability hooks — not implemented. These aren't yet
  normatively specified either (the spec section is still a placeholder bullet list), so no
  test case has been written against unspecified behavior.
- Snapshot bundle behavior ("Save Snapshot" producing a new immutable `.pweb`) — not
  implemented, same reasoning.
- IndexedDB — deliberately not shimmed yet (a real IndexedDB shim is a much larger surface
  than `localStorage`); currently just blocked outright (`indexedDB === undefined`) rather
  than exposed unisolated. Worth a test case once it exists, but there's nothing to test
  against yet beyond "it's unavailable."
