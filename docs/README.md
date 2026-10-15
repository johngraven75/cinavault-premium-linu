# CinaVault Premium (Linux) documentation

Windows Premium ([johngraven75/CinaVault-Premium](https://github.com/johngraven75/CinaVault-Premium))
is the functional and visual reference for this edition. Product guides land with the
application port; this index lists the rules, guidelines and process docs that govern the repository.

## Process and quality gates

| Document | Topic |
|---|---|
| [MASTER_BUILD_COMPLETION_GATE.md](MASTER_BUILD_COMPLETION_GATE.md) | What must pass before a build counts as complete |
| [CARRY_FORWARD.md](CARRY_FORWARD.md) | Registry of accepted features that every build must keep (checked in CI) |
| [AGENTS.md](AGENTS.md) | Owner's standing build and upload instructions |

## Reference

| Document | Topic |
|---|---|
| [DOMAIN_LANGUAGE.md](DOMAIN_LANGUAGE.md) | Terms used for accounts, servers, clients and remote access |
| [PACKAGE_SIGNING.md](PACKAGE_SIGNING.md) | Signing the `.deb` package with GPG |

## Architecture decisions

| Document | Decision |
|---|---|
| [adr/0001-owned-server-and-rendezvous-architecture.md](adr/0001-owned-server-and-rendezvous-architecture.md) | Owned server with a rendezvous control plane |
| [adr/0002-wireguard-device-profiles.md](adr/0002-wireguard-device-profiles.md) | WireGuard device profiles |
