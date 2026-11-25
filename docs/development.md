# Development

## Build

Requires JDK 17 and Android SDK 35. Set `ANDROID_HOME` to your SDK location.

```sh
bash setup-vendor.sh
./gradlew :app:testDebugUnitTest :app:lintDebug :app:assembleDebug
```

The development APK is `app/build/outputs/apk/debug/app-debug.apk`.
The ignored USB dependency is fetched at a pinned revision and patched by
`setup-vendor.sh`. See the [dependency notes](hyperborea-dependency.md).

## Releases

Push a tag such as `v1.0.1` to run `.github/workflows/release.yml`. The workflow
builds, verifies, signs and publishes the APK, installation ZIP and SHA-256
checksums as the repository's latest release when signing secrets are configured.
Without signing configuration, CI checks the source and a maintainer publishes
locally signed assets. Release notes come from
`docs/release-notes.md`; keep them brief and focused on user-visible changes.

Configure these repository secrets for automatic signing:

- `NORDICROWER_KEYSTORE_BASE64`
- `NORDICROWER_KEYSTORE_PASSWORD`
- `NORDICROWER_KEY_ALIAS`
- `NORDICROWER_KEY_PASSWORD`

Keep the existing signing identity to preserve in-place updates. The packaging
script verifies its public certificate fingerprint and rejects other signers.
Never commit keystores, signing credentials or diagnostic reports.

For a local signed release, set `NORDICROWER_KEYSTORE_PATH` and the three signing
credential environment variables, then run:

```sh
./gradlew -PVERSION_NAME=1.0.1 :app:testDebugUnitTest :app:lintRelease :app:assembleRelease
python3 package-release.py --version 1.0.1
```

Outputs are written to `build/release/`. The Android version code is derived from
major.minor.patch; preserve this scheme so updates remain compatible.

## Diagnostics

The app keeps bounded journals and can save/share a report. Saving also writes
an ADB-readable snapshot to
`/sdcard/Android/data/com.nordicrower.app/files/diagnostics/latest-report.txt`.
The Windows collector in `scripts/` collects that snapshot and system information
without changing the console. Public APKs do not allow private `run-as` reads.

Synthetic BLE fixtures exist only in the separate instrumentation test APK.
Do not include that APK in releases.
