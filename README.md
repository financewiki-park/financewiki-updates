# FinanceWiki Updates

Public signed application update artifacts only. This repository does not contain FinanceWiki knowledge data.

## Production updater owner

`financewiki-updates/.github/workflows/publish-financewiki.yml` is the production release boundary for FinanceWiki desktop updates.

- It pins one immutable commit from private `financewiki-park/financewiki-app`.
- Windows x64 and macOS Apple Silicon updater artifacts must be built from that same commit.
- A release is published only after both platform builds and signature checks succeed.
- `latest.json` must contain both `windows-x86_64` and `darwin-aarch64` entries.
- Existing version releases are immutable and must not be overwritten.
- The Tauri updater signing key and Apple signing/notarization credentials live only in Actions secrets, never in this repository.

The application-side release contract is documented in `financewiki-app/docs/CROSS_PLATFORM_RELEASE.md`.
