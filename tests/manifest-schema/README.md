# Manifest Schema Tests

Test cases for **Goal 2: Manifest schema and capability declaration**.

6 draft test cases, written against a working reference implementation
(`packages/core/src/manifest.ts` in `portableweb/viewer`), covering:

- `tc-001` — minimal valid manifest opens
- `tc-002` — missing a required field is rejected
- `tc-003` — malformed `id` is rejected
- `tc-004` — non-SemVer `version` is rejected
- `tc-005` — invalid `entry` path is rejected
- `tc-006` — unknown top-level/permission keys are tolerated, not rejected

Not yet covered here: the full capability schema (domain lists for `internet.read`,
justification strings for `camera`/`microphone`/`geolocation`) — the spec section itself
notes this "will be specified as this section matures."

**Known discrepancy worth resolving before more tests are added:** the spec draft's
permissions table uses a split `internet.read`/`internet.write` model, while the IETF
Internet-Draft and the reference implementation's actual manifest schema still use a single
boolean `network` field. These need reconciling one way before the capability-schema test
cases can be written meaningfully.
