# tc-sandbox-002 — Declaring a permission the viewer doesn't implement still denies it (keystone)

| Field | Value |
|---|---|
| **Test ID** | tc-sandbox-002 |
| **Spec section** | Viewer Conformance and Security Sandboxing; Manifest Schema § Capability declaration and permissions |
| **Type** | Negative |
| **Status** | Draft |

## Requirement

> A manifest's declared capabilities are inputs to the viewer's security policy, not
> security guarantees by themselves. A viewer MUST apply a deny-by-default policy and allow
> only capabilities permitted by *both* the manifest and the viewer's own implementation —
> a capability the viewer has no implementation for MUST be denied regardless of what the
> manifest declares.

## Test bundle

A single bundle whose manifest declares **every** currently-defined permission as granted
(`camera`, `microphone`, `geolocation`, `internet.read`, `internet.write`, `inter-bundle`,
all `true`), containing a script that probes each corresponding Web API and reports the
outcome.

## Expected viewer behavior

For every capability the viewer doesn't actually implement, the probe MUST observe ordinary
web-platform denial (e.g. `NotAllowedError` from `getUserMedia`, `fetch` rejecting/erroring
for non-bundle origins) — **not** a novel PortableWeb-specific error, and not a grant. A
viewer implementing zero optional capabilities beyond mandatory baseline behavior (container
processing, isolation, universal denial) is fully conformant on its own — this is what makes
partial/staged implementation a legitimate, permanent viewer shape rather than a stage of
incompleteness to apologize for.

## Notes

**This is the single most load-bearing test case in the whole suite** — it's the one that
validates the conformance model itself, not just one feature. The reference implementation's
fixture corpus has an identical test (their `F12`, explicitly called the "keystone fixture")
and reports it passing against a real, running viewer that has zero capability modules
beyond storage. Recommend this test case (or one very close to it) be treated as
load-bearing for any future formal conformance-class definition, the same way it's treated
in the reference implementation's own test corpus.
