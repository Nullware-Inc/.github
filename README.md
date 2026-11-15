# Nullware-Inc/.github

Organisation-wide defaults for every Nullware repository.

| Path | What it does |
|---|---|
| `profile/README.md` | The organisation's GitHub profile page |
| `CONTRIBUTING.md`, `SECURITY.md`, `CODE_OF_CONDUCT.md` | Defaults for any repo that has none of its own |
| `ISSUE_TEMPLATE/`, `PULL_REQUEST_TEMPLATE.md` | Issue and PR forms |
| `.github/workflows/flutter-app.yml` | Reusable CI: test the core and build a Flutter app (Windows, Linux, macOS, Android); attaches builds to releases on `v*` tags |
| `.github/workflows/rust-app.yml` | Reusable CI: fmt, clippy and build of the Rust client on all three desktop OSes |

## Using the workflows in an app repo

`.github/workflows/ci.yml` in Null-YT-Client-Desktop-Dart:

```yaml
name: CI
on:
  push: { branches: [main], tags: ["v*"] }
  pull_request:
jobs:
  windows: { uses: Nullware-Inc/.github/.github/workflows/flutter-app.yml@main, with: { platform: windows } }
  linux:   { uses: Nullware-Inc/.github/.github/workflows/flutter-app.yml@main, with: { platform: linux } }
  macos:   { uses: Nullware-Inc/.github/.github/workflows/flutter-app.yml@main, with: { platform: macos } }
```

The Flutter workflow checks out `Nullware-Inc/Null-YT-Core-Dart`, so that repository has to exist on GitHub.
