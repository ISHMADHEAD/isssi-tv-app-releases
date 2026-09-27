# ISSSI TV — releases

Published builds of the ISSSI TV Android app, and the feed its updater reads.

**Bring your own subscription.** ISSSI TV is a player. It ships with no
channels, no films and no series: it plays whatever the M3U link or Xtream
Codes login you give it points at, and nothing else. Getting that source, and
the right to watch what is on it, is between you and whoever provides it.

The app sends nothing anywhere except to that provider and, to check for a
newer build, to this page.

The app source is not here; it lives on the developer's machine. This
repository exists only so an installed copy of the app can find out that a
newer one has been published.

## What a release contains

| File | Purpose |
|---|---|
| `app-release.apk` | The signed build |
| `updates.json` | What the in-app updater reads |

## The feed

The app fetches `updates.json` from the **latest** release, so the URL never
changes as versions come and go:

```
https://github.com/ISHMADHEAD/isssi-tv-app-releases/releases/latest/download/updates.json
```

```json
{
  "version": "1.0.0",
  "build": 1,
  "apkUrl": "…/releases/download/v1.0.0/app-release.apk",
  "notes": "What changed",
  "minSupported": 1,
  "sha256": "…",
  "sizeBytes": 16904312
}
```

`build` is the Android `versionCode` and is the only field compared when
deciding whether something newer exists. `sha256` is checked against the
downloaded bytes before the installer is allowed near them — a mismatch is
discarded rather than installed.

## Installing by hand

Download `app-release.apk` from the latest release and install it. Android
will refuse to install over a copy signed with a different key; if that
happens, uninstall the old one first.
