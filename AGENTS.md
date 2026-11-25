# NordicRower development guide

Android application: `com.nordicrower.app`. Read live FitPro USB rower measurements
and expose them as a Bluetooth FTMS rower. Preserve the package and signing identity
so installed applications can update in place.

## Build

Run `bash setup-vendor.sh`, then
`./gradlew :app:testDebugUnitTest :app:lintRelease :app:assembleDebug`.
Requires JDK 17 and Android SDK 35. Vendor code, build output and reference
checkouts are ignored and must not be committed. Preserve dependency licenses.

## Public content

Keep the README, guides, release notes and app copy concise and focused on
installation and use. Refer to other fitness apps generically in setup text.
Do not include personal correspondence, identifying diagnostic material,
research narratives or test results in public product content or release assets.
Never import private reports or historical reference archives into this repository.

## Releases

Tags use `v<major>.<minor>.<patch>`. The release workflow publishes the signed APK,
curated ZIP and checksums. Version/signing details belong in developer docs.
Use English comments and descriptive names. NordicFTMS is a separate project.
