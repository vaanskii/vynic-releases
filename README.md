# Vynic releases

Official Vynic Windows downloads and signed bootstrap metadata. Application source and private signing keys are excluded. GitHub Releases holds immutable EXE/ZIP assets; the free Render static site serves `public/` at https://releases.vynic.ge.

## Beta 1 — test download

POS 1.0.0 build 16 / Edge and Setup 1.0.0.16, beta channel, Windows amd64. This candidate includes the printer header fix. Backend: https://api.vynic.ge. Build environment `staging` does not isolate cloud data.

Download `VynicSetup-1.0.0-build16-beta.exe` from [v1.0.0-beta.1](https://github.com/vaanskii/vynic-releases/releases/tag/v1.0.0-beta.1). Use a new test PC and synthetic data. Existing 1.0.14 installs cannot normally downgrade to 1.0.0. Do not reset updater counters or replace an existing installation. No Authenticode certificate is included.

The public access-request and invitation flow starts at https://vynic.ge/request-access. Once approved, sign in, open Devices/POS, issue a device code and enter it in POS. Existing restaurants must retain the same venue identity. The user/operator handles accounts and historical data.

## Bootstrap and repair

`windows/beta/bootstrap.json` and `bootstrap/16.json` are the same signed bootstrap. `pos/1.0.0.json` is signed per-version repair metadata. These allow fresh setup and preserve pinned repair identities. **`pos/manifest.json` is deliberately absent: automatic update publication remains held.** No stable channel is published.

Signed envelopes expire 2026-11-23T15:28:45Z and must be renewed before expiry, including retained repair metadata, while preserving the same artifact version/hash/size. Pinned public trust expires 2027-10-24T00:00:00Z. Never upload a private key or replace already published EXE/ZIP bytes.

## Qualification

See [qualification.json](public/windows/beta/qualification.json) and [SHA256SUMS.txt](public/windows/beta/SHA256SUMS.txt). Component software tests passed; ordinary-user clean install/runtime, real enrollment/offline-reconnect, update/repair/recovery and physical printing are still pending. This is a beta test download, not production qualification.

Render auto-deploy and previews are off. Deploy reviewed commits explicitly. Do not add paid resources or overages.
