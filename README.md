# FinanceWiki Updates

Public signed application update artifacts only. This repository does not contain FinanceWiki knowledge data.

## Production updater owner

`financewiki-updates/.github/workflows/publish-financewiki.yml` is the production release boundary for FinanceWiki desktop updates.

- It pins one immutable commit from private `financewiki-park/financewiki-app`.
- Windows x64 updater artifacts are built from that pinned commit.
- A release is published only after the Windows build and Tauri updater signature check succeed.
- `latest.json` contains the `windows-x86_64` entry only.
- Existing version releases are immutable and must not be overwritten.
- The Tauri updater signing key lives only in Actions secrets, never in this repository.
- Production publishing is started only with `workflow_dispatch` and an immutable, full 40-character `financewiki-app` SHA. Updating this workflow must never publish a duplicate app version by itself.

## macOS status

macOS distribution is intentionally deferred. No macOS artifact, signature, notarization, or `darwin-aarch64` manifest entry is published until a separately approved cross-platform release restores Apple signing and notarization validation.

The application-side release contract is documented in `financewiki-app/docs/CROSS_PLATFORM_RELEASE.md`.
The operational procedure and v0.2.71 incident record are in `financewiki-app/docs/WINDOWS_UPDATER_RELEASE_RUNBOOK.md`.
