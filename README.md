# abnormalhq/homebrew-tap

[![Audit](https://github.com/abnormalhq/homebrew-tap/actions/workflows/audit.yml/badge.svg)](https://github.com/abnormalhq/homebrew-tap/actions/workflows/audit.yml)

The [Homebrew](https://brew.sh/) tap for [Abnormal Mail](https://abnormalhq.com/download/), the desktop mail client for Abnormal mailboxes.

| Cask            | App           | Requires                                    |
| --------------- | ------------- | ------------------------------------------- |
| `abnormal-mail` | Abnormal Mail | macOS 11 or later (Apple Silicon and Intel) |

## Install

```bash
brew install --cask abnormalhq/tap/abnormal-mail
```

Or tap once and install by name:

```bash
brew tap abnormalhq/tap
brew install --cask abnormal-mail
```

### First launch

Abnormal Mail is not signed with an Apple Developer ID yet, so macOS blocks its first launch. Open System Settings > Privacy & Security and click "Open Anyway", or run:

```bash
xattr -dr com.apple.quarantine "/Applications/Abnormal Mail.app"
```

## Update

```bash
brew upgrade --cask abnormal-mail
```

## Uninstall

```bash
brew uninstall --cask abnormal-mail
```

To also delete the app's local data (`~/Library/Application Support/abnormal-mail`):

```bash
brew uninstall --zap --cask abnormal-mail
```

## How the cask is updated

[`Casks/abnormal-mail.rb`](Casks/abnormal-mail.rb) is generated, not written by hand. Each desktop release in [abnormalhq/mail](https://github.com/abnormalhq/mail) uploads the `.dmg` to `downloads.abnormalhq.com`, then `desktop/packaging/release.py` rewrites the cask with the new version and SHA-256 and the release app commits it here. Hand edits to the cask are overwritten by the next release, so change the template in `release.py` instead.

Every pull request and every push to `main`, release commits included, runs [`audit.yml`](.github/workflows/audit.yml) on macOS: `brew style`, `brew audit --cask --strict --online`, and a real install followed by `brew uninstall --zap`.

The cask's `livecheck` reads <https://downloads.abnormalhq.com/desktop/latest.json>, so `brew livecheck abnormal-mail` reports the latest published version.

## Other platforms

Windows installers (x64 and Arm64) are on <https://abnormalhq.com/download/>. See the [desktop client README](https://github.com/abnormalhq/mail/blob/main/desktop/README.md) for features, signing in, and building from source.

## Issues

Report problems with the app or the cask in [abnormalhq/mail](https://github.com/abnormalhq/mail/issues).
