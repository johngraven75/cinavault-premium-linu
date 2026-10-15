# Signing the Linux `.deb` package

The Linux edition is distributed as a `.deb` package. Unlike Windows, Debian/Ubuntu does not
show an "unknown publisher" prompt on install, but a signed package lets users verify the
package is authentic and unmodified. The release workflow
(`.github/workflows/linux-package.yml`) signs each `.deb` with a detached GPG signature
(`dpkg-sig`) as soon as a signing key is configured. Until then, the `.deb` is published
unsigned and users confirm the published `SHA256SUMS.txt` checksum instead.

## How it works

1. The release workflow builds the `.deb` with `npm run tauri:build:linux`.
2. If the `DEB_GPG_PRIVATE_KEY` secret is present, the workflow imports the key and runs
   `dpkg-sig --sign builder` on every built `.deb`. If it is absent, the build stays
   unsigned and the run shows a warning naming what is missing.
3. The workflow publishes the `.deb` and a `SHA256SUMS.txt` to the GitHub release.

## One-time setup (owner)

1. Create a dedicated GPG signing key (do this on a trusted machine, not in CI):
   ```bash
   gpg --full-generate-key          # choose RSA 4096, a sensible expiry, no passphrase-less key in CI
   gpg --list-secret-keys --keyid-format=long   # note the key id
   gpg --armor --export-secret-keys <KEY_ID> > cinavault-signing.asc
   ```
2. In GitHub, go to **Settings > Secrets and variables > Actions** and add:

   | Kind | Name | Value |
   | --- | --- | --- |
   | Secret | `DEB_GPG_PRIVATE_KEY` | Contents of `cinavault-signing.asc` (the ASCII-armored private key) |
   | Secret | `DEB_GPG_PASSPHRASE` | The key's passphrase (if set) |
   | Variable | `DEB_GPG_KEY_ID` | The signing key id from step 1 |

3. Publish the **public** key so users can verify:
   ```bash
   gpg --armor --export <KEY_ID> > cinavault-signing.pub.asc
   ```
   Attach it to releases or host it, and document the fingerprint in the release notes.

The next release (trigger-file commit or a manual workflow run) is then signed.

## What users can do

Verify a downloaded package before installing:

```bash
# Checksum (always available)
sha256sum -c SHA256SUMS.txt

# Signature (once signing is enabled)
gpg --import cinavault-signing.pub.asc
dpkg-sig --verify cinavault-premium_*_amd64.deb
```

## Keep the key safe

The signing key is a credential: never commit it to the repository, never print it in logs,
and store it only in GitHub Actions secrets or an equivalent secrets manager. Rotate it if it
is ever exposed, and publish the new public key with the fingerprint change noted in the
release notes.
