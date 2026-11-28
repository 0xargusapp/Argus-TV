# Security policy

## Reporting a vulnerability

Report security issues privately to **argusapp@proton.me**. Do not open a
public GitHub issue for an unpatched vulnerability.

Include the installed Argus version (`Settings` → `Status`), Android version and
device model, steps to reproduce, and any relevant logs or proof of concept.
No PGP key is required.

## Response timeline

- **Acknowledgement:** within 72 hours.
- **Initial assessment:** within 7 days, with a fix or mitigation plan if
  confirmed.

Because this repository holds only the public release binaries and documentation
while development happens in a private source repository, fixes ship as signed
APK releases on [Releases](https://github.com/0xargusapp/Argus-TV/releases)
once verified.

## Scope

### In scope

- **The Argus Android app (`com.nexusblock`)**: the `VpnService` DNS-only tunnel,
  packet codec, DoH forwarder, signature pinning, self-updater, and Android
  Keystore session storage.
- **The bundled privileged helper**: Argus's vendored Shizuku server/starter
  integration and the catalog/patch verification pipeline (manifest signature,
  SHA-256, and signer-pin checks).
- **The sign-in and account path**: TV QR pairing, tag + PIN authentication, and
  device challenge verification.

### Out of scope

- Third-party patched streaming APKs referenced by the patch catalog.
- Upstream Shizuku bugs that do not affect Argus's binder permissions, command
  quoting, or staging paths.
- Social engineering, physical device access with unlocked ADB already granted, or
  volumetric denial-of-service against GitHub or upstream DNS infrastructure.

## Verifying official releases

Every official APK is signed with the same release certificate:

- **Subject:** `CN=Argus, OU=TV, O=NexusBlock, C=IN`
- **SHA-256 fingerprint:**
  `AD:AB:3A:C6:5B:D7:11:CC:9B:83:C7:C4:74:A7:57:D5:04:41:74:1A:B6:62:5D:90:96:FB:B3:7A:DB:D3:F3:41`

Each release attaches `argus.apk.sha256` alongside `argus.apk` and
`argus-<version>.apk`.
