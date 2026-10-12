# STBPlay — Android TV IPTV player starter

STBPlay is an original Android application project intended for Android TV / Google TV first, with phone/tablet support where practical. It uses Kotlin, Jetpack Compose, and AndroidX Media3 (ExoPlayer). No channel list, playlist, subscription, credentials, or copyrighted artwork is bundled.

## Current starter functionality

- Android TV launcher entry and phone/tablet launcher entry
- Original dark STBPlay interface with sidebar navigation and remote-focus styling
- M3U/M3U8 playlist loading from an HTTP(S) URL (HTTP is allowed for providers that require it; prefer HTTPS when supported)
- Common `#EXTINF` fields: title, `tvg-id`, `tvg-logo`, and `group-title`
- Xtream Codes API requests for live channels, movies, and series catalogues
- Live channel search, simple favorites (in-memory for this starter), recent items (in-memory)
- Media3 / ExoPlayer playback screen with playback controls and basic error reporting
- Settings, TV Guide placeholder, and Movies / Series catalogue screens

## Important scope notes

This is a **buildable first project foundation**, not yet a feature-complete replacement for IPTVnator. In particular:

- XMLTV parsing and a full timeline EPG grid are not implemented yet.
- Stalker / Ministra portal authentication and playback are not implemented yet.
- Xtream series detail / episode resolution is not implemented yet; the initial series call lists the catalogue only.
- Local-file playlist picker, persistent Room/DataStore storage, logos/artwork loading, playback resume, catch-up/timeshift, TMDB enrichment, downloads, and production-grade error handling are follow-up tasks.
- Stream compatibility depends on the provider, format, codecs, DRM, and Android device.
- Xtream URLs commonly embed credentials in stream URLs; avoid sharing logs or screenshots containing private account details. Production hardening should use safer credential handling and redact URLs.

## Build with Android Studio

1. Install Android Studio with JDK 17 and Android SDK Platform 35 (or let Android Studio install the requested SDK).
2. Extract/open this `STBPlay` folder in Android Studio using **Open**.
3. Allow Gradle sync and dependency downloads.
4. Choose an Android TV emulator (or a phone/tablet emulator) and press **Run**.
5. In STBPlay, open **Sources** and enter an M3U URL or Xtream Codes server URL, username, and password for a provider you are authorized to use.

To build an APK in Android Studio, choose **Build → Build Bundle(s) / APK(s) → Build APK(s)**. The debug APK is usually produced under `app/build/outputs/apk/debug/`.

## Google AI Studio workflow

Google AI Studio can help generate or revise individual Kotlin files, but it is not a replacement for Android Studio's Android Gradle build, emulator, or APK-signing workflow. Keep this folder as the source of truth; apply AI-generated edits here, then sync/build/test in Android Studio.

## Dependencies

- Android Gradle Plugin 8.7.3
- Kotlin 2.0.21 + Compose compiler plugin
- Compose BOM 2024.12.01
- AndroidX Media3 1.5.1
- Minimum SDK 23; compile/target SDK 35

Dependency versions may need updating to match your installed Android Studio / SDK setup.

## License and relationship to IPTVnator

This project was authored as a new Android implementation using IPTVnator as a **functional reference**; it does not intentionally copy IPTVnator source files or branding. The reference archive's `LICENSE.md` states MIT License, copyright (c) 2019–2026 4gray, with notice-retention conditions for reused portions. If you later copy or adapt any covered IPTVnator source into this project, retain the required copyright and license notice for those portions and review third-party dependency licenses. STBPlay is not affiliated with IPTVnator or its authors.

Use this app only with playlists and streams you have permission to access.

## V0.2 review changes

See `CHANGELOG.md`. The source includes improvements to Xtream categories, series episode selection, M3U parsing, favorite persistence and error privacy. XMLTV and Stalker/Ministra remain planned. A Gradle wrapper properties file is provided, but the wrapper JAR and launch scripts could not be bundled in this environment. In Android Studio, use a locally installed Gradle 8.10.2 to sync, or generate the wrapper with `gradle wrapper --gradle-version 8.10.2` using a local Gradle installation. This project has not been compiled or device-tested here.
