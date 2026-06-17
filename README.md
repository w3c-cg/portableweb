# PortableWeb — W3C Community Group

This is the official repository of the [W3C Portable Web Content Format Community Group](https://www.w3.org/community/portableweb/).

This repository hosts Community Group reports, issues, proposals, meeting notes, status updates, and publication-oriented versions of the specification. Primary project development lives at the PortableWeb GitHub organization:

> **Main project:** [github.com/portableweb](https://github.com/portableweb)

---

## About this Community Group

AI-assisted tools can now generate high-quality interactive web content — games, presentations, simulations, educational materials — in minutes. This has created a massive and growing category of ephemeral web applications that need to be shared and used immediately across devices and platforms, without a traditional server for distribution, without association with a web origin, and without being confined to a web browser.

No existing format treats interactive web content as a portable, self-contained, immediately runnable unit. PDF loses interactivity. EPUB3 is constrained to a document and book model — its JavaScript support is an enhancement to a reading experience, not a general-purpose runtime. Web Bundles never achieved broad implementation and was designed as a network transport optimization, not a portable execution environment. The Web Application Manifest describes server-hosted apps and requires a live web origin. None of these addresses the need for content that has no server, no origin, and no installation — content that should exist, run, and be shared as a single portable file, across all platforms, entirely offline.

The mission of this group is to develop an open specification for a self-contained portable web content format that can be instantly shared and run on any platform — desktop, mobile, or offline — without a server, app store, or deployment pipeline. The format is content-model agnostic, equally supporting books, games, presentations, educational simulations, 3D experiences, scientific models, and collaborative applications.

### Scope of work

- Container and packaging format
- Manifest schema for capability and permission declaration
- Viewer conformance requirements and security sandboxing model
- Storage model — per-bundle isolated storage specification, defining how packaged content can persist state locally, how storage is scoped and sandboxed to the bundle, and guidelines for storage portability across viewer implementations
- Inter-bundle communication model — a permission-gated channel specification enabling bundles to communicate locally via Bluetooth, WiFi Direct, or local network, making offline multiplayer, peer-to-peer, and collaborative interactive experiences possible without any server infrastructure
- Viewer conformance test suite
- Non-normative implementation guide for content creators, AI tools, and viewer developers

---

## What is PortableWeb?

PortableWeb (`.pweb`) is an open file format for self-contained, sandboxed, interactive documents. A `.pweb` file packages HTML, CSS, JavaScript, and media into a single archive, opened by a compatible viewer in its own window, sandboxed from the host system.

Think of it as: *like PDF, but interactive. Like a webpage, but a file you own.*

---

## Two GitHub Spaces

PortableWeb uses two GitHub spaces with complementary purposes.

**PortableWeb project organization — [github.com/portableweb](https://github.com/portableweb)**

This is the primary project space for PortableWeb. It hosts the main specification work, sample viewers, validation tools, packaging utilities, examples, demos, and other implementation-oriented project resources.

**W3C Community Group repository — [github.com/w3c-cg/portableweb](https://github.com/w3c-cg/portableweb)**

This repository hosts a Community Group copy or publication-oriented version of the specification, along with Community Group reports, issues, proposals, meeting notes, and standards-track discussion related to PortableWeb.

This separation is intentional. The PortableWeb GitHub organization remains the primary home for project and specification development, while the W3C Community Group repository provides a community-facing space for review, discussion, reporting, and W3C Community Group publication workflows.

---

## Key Links

| Resource | URL |
|---|---|
| Main project | https://github.com/portableweb |
| Project website | https://portableweb.org |
| IETF Internet-Draft | https://www.ietf.org/archive/id/draft-selvaraj-portableweb-format-01.txt |
| Published spec (this repo) | https://w3c-cg.github.io/portableweb/ |
| W3C CG page | https://www.w3.org/community/portableweb/ |

---

## Repository Structure

```
spec/         Published spec drafts (rendered via GitHub Pages)
status/       Periodic status updates from the editors
meetings/     CG meeting agendas and notes
```

---

## Participating

Anyone can read the spec and open issues. To make substantive contributions (pull requests), you must join the W3C Community Group and agree to the [W3C Community License Agreement (CLA)](https://www.w3.org/community/about/process/cla/).

- **Join the CG:** https://www.w3.org/community/portableweb/
- **Spec feedback and issues:** open an issue in this repository
- **Implementation contributions:** open a PR in the relevant [portableweb org](https://github.com/portableweb) repo
- **General discussion:** use GitHub Discussions in this repository

See [CONTRIBUTING.md](CONTRIBUTING.md) for full contribution guidelines.

---

## Status

Current spec version: **0.1 (Draft)**
IETF draft: **draft-selvaraj-portableweb-format-01**
See [status/](status/) for the latest editor updates.

---

*Spec contributions are made under the [W3C CLA](https://www.w3.org/community/about/process/cla/). See [LICENSE.md](LICENSE.md) for details.*
