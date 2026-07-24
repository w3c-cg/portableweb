# tc-manifest-004 — Non-SemVer `version` is rejected

| Field | Value |
|---|---|
| **Test ID** | tc-manifest-004 |
| **Spec section** | Manifest Schema and Capability Declaration § Required fields |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> `version` MUST follow [Semantic Versioning 2.0.0](https://semver.org/).

## Test bundle

An otherwise-valid bundle whose manifest `version` is not valid SemVer, e.g. `"1.0"`,
`"v1.0.0"`, or `"latest"`.

## Expected viewer behavior

The viewer MUST reject the bundle.
