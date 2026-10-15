<!-- Describe the change so a reader understands it in plain language. -->

## Summary

**Before:** <!-- what the app or repo does today -->

**After:** <!-- what it does with this change -->

**How:** <!-- one short paragraph on the approach -->

## Completion report
<!-- Required by AGENTS.md. Use "not applicable" where a layer does not apply. -->

- **Purpose:** the problem solved and intended outcome.
- **Front end:** user-visible changes and validation, or "not applicable".
- **Connector / integration:** IPC, APIs, storage, provider or platform wiring and validation, or "not applicable".
- **Back end:** domain logic, services, persistence and validation, or "not applicable".
- **Completion:** files changed, tests run and results, remaining risks, and release status.

## Checklist

- [ ] `npm run lint` passes
- [ ] `npm test` passes
- [ ] `cargo test --manifest-path src-tauri/Cargo.toml` passes (if Rust changed)
- [ ] Accepted features preserved (see `docs/CARRY_FORWARD.md`)
- [ ] Parity with the Windows reference considered (see `docs/MASTER_BUILD_COMPLETION_GATE.md`)
- [ ] No secrets, signing keys or credentials committed
