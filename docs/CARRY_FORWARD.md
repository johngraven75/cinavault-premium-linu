# CinaVault Premium (Linux) — Master Carry-Forward Registry

> **Rule:** No accepted feature from any prior build may be removed or hidden without explicit owner approval and a documented entry in the release notes for that build. This file is the authoritative source of truth and is verified automatically on every CI run.

---

## How This Works

On every push and pull request, the CI pipeline runs `tests/carryForwardVerification.test.mjs`, which checks that every feature token listed in the **Feature Registry** below is still present in the active source files. If any token is missing, the build fails with a clear report of what regressed.

Each new build must:
1. Add its features to the **Feature Registry** below.
2. Write a `RELEASE_NOTES_BUILD{N}.md` file in the repo root.
3. Pass all carry-forward governance tests before the `.deb` package is built.

---

## Parity baseline

Windows Premium ([johngraven75/CinaVault-Premium](https://github.com/johngraven75/CinaVault-Premium)) is the functional and visual reference (see [MASTER_BUILD_COMPLETION_GATE.md](MASTER_BUILD_COMPLETION_GATE.md)). Every accepted Windows feature is expected to reach the Linux edition with the same user-facing function, options, design intent and security behavior, implemented with Linux-native mechanisms. As the application source is ported into this repository, each feature's token and source file are recorded in the **Feature Registry** below, and the carry-forward test is activated against them.

---

## Feature Registry

> The registry is populated as the application source lands. Each entry records the
> feature, a token that must remain present in the source, and the source file that
> holds it — the same format used by the Windows reference repository.

| Feature | Token to Verify | Source File |
|---|---|---|
| _(populated as source is ported)_ | | |
