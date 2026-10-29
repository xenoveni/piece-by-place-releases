# Piece by Place releases

Signed Android builds of Piece by Place: World Puzzle. This repository holds release files only. The source code is in a private repository.

## Download and install

1. Open the latest release: https://github.com/xenoveni/piece-by-place-releases/releases/latest
2. Download `piece-by-place-<version>.apk` on your Android phone.
3. Open the file and allow installing apps from your browser or file manager when Android asks.

The APK is built for 64-bit ARM phones (arm64-v8a). Each new version installs over the old one and keeps your saved progress, because every release is signed with the same key.

## Files in each release

- `piece-by-place-<version>.apk`: the app.
- `latest.json`: the version number, the APK address, the SHA-256 and the release notes. Installed copies of the app read this file from the latest release to find out whether a newer version exists.
- `SHA256SUMS.txt`: the SHA-256 of the APK.

## Check a download

Compare the hash of the file you downloaded with `SHA256SUMS.txt`. In PowerShell:

    Get-FileHash .\piece-by-place-<version>.apk -Algorithm SHA256

To check the signature, use `apksigner` from the Android SDK build-tools:

    apksigner verify --print-certs piece-by-place-<version>.apk

The signer certificate SHA-256 must be:

    e84866c27a99f57e7d8238c43344c86e1e3dc29ff2ca923c9724043fdce7148f

If it differs, do not install the file.

## For the maintainer

Releases are created by `scripts/release.ps1 -Publish` in the source repository. Do not create releases by hand and do not mark them as draft or pre-release: the app reads `releases/latest/download/latest.json`.
