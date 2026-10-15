# Security policy

## Supported versions

The Linux edition is in active development and has not cut a public release yet. Once builds are published, the latest build is the supported one and this table is updated to match.

| Version | Supported |
|---|---|
| Linux edition (in development) | Tracking the latest build |

## Reporting a vulnerability

Please report security issues privately through GitHub: open the repository's **Security** tab and choose **Report a vulnerability**. Do not open a public issue for a security problem.

Include the version (Settings > About), the steps to reproduce the problem, and what an attacker could do with it. You will get an acknowledgement, and a fix will ship in the next build once the report is confirmed.

## How the app protects you

- **Secrets:** metadata provider keys and the parental PIN are never stored in this repository. Keys are kept in the Secret Service keyring (GNOME Keyring / libsecret), and the PIN and API keys are stored only as salted hashes.
- **Media server:** remote clients must sign in or present an API key, router ports and the relay open only when you start remote connectivity, and turning off the Remote Access switch refuses remote clients outright.
- **Playback:** the built-in player streams over loopback with a per-session token.
- **Privilege:** operations that need elevation (WireGuard tunnel setup, system package changes) use polkit/`pkexec`; the app never assumes or requires running as root.
- **Supply chain:** dependencies are locked, CodeQL runs on every pull request, and a scheduled job audits dependencies weekly.
