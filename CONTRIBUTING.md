# Contributing to Nullware

Thanks for helping. This guide applies to every repository in the organisation unless that repo has its own.

## Before you start

- **Bugs:** open an issue with the bug template. Include your OS, the app version, and the yt-dlp version (Settings → Engine).
- **Features:** open an issue first so we can agree on the approach before you write code.
- **Small fixes** (typos, obvious bugs) can go straight to a pull request.

## Repository layout

The Flutter apps share one codebase, `Null-YT-Core-Dart`. Check it out **next to** the app repo, because the apps depend on it by relative path:

```
Nullware/
├─ Null-YT-Core-Dart/            ← all UI and logic
├─ Null-YT-Client-Desktop-Dart/  ← desktop shell
└─ Null-YT-Client-Mobile-Dart/   ← Android shell
```

Most changes belong in the core. The shells only hold window chrome and platform glue.

## Code style

- **Dart:** `flutter analyze` must pass, and `flutter test` in the core must pass.
- **Rust:** `cargo fmt` and `cargo clippy` should be clean.
- Keep commits focused, and write the message in the imperative ("Add …", "Fix …").
- Every new user-facing option goes into Settings and into the settings JSON export.

## Things we won't merge

- Code that uploads user data anywhere other than YouTube itself.
- Telemetry or analytics.
- Changes that store Google passwords. Sign-in always happens on Google's own page.

## Windows development

Flutter needs **Developer Mode** turned on to build Windows apps with plugins: Settings → System → For developers.
