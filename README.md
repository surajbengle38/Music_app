# OK JAANU (Android, v0.5.0)

Offline-first local music player. Kotlin, Jetpack Compose, AndroidX Media3, Room. No account, no network code, no INTERNET permission.

> **Status: all code was written without being able to build or run Android.** Nothing here has been compiled with Gradle, installed,
> or heard playing audio. Only the pure-logic functions were compiled (kotlinc) and exercised. See `docs/VERIFICATION.md` for the honest per-item status.

## Run in Android Studio
1. Install a current stable Android Studio (it bundles a JDK 17+ and offers to install the Android SDK).
2. **File > Open** this folder. If it asks to create or upgrade the Gradle wrapper, accept. (The project ships without `gradlew`.)
3. Open `gradle/libs.versions.toml` and align `agp`, `kotlin`, `ksp`, `composeBom`, `media3`, `room` with versions Android Studio's own "Empty Activity" template uses
   (the numbers here are unverified placeholders; the `ksp` version must start with the exact Kotlin version).
4. Sync, then run the `app` configuration on a device (API 26+) or emulator. Real audio and the equalizer are best tested on a physical phone.
5. Put a few MP3/FLAC/WAV/M4A/OGG files on the device, then use Home > "add music" or "scan a folder".

## Commands (intended; NOT yet run by me)
```
./gradlew assembleDebug                 # debug APK -> app/build/outputs/apk/debug/app-debug.apk
./gradlew testDebugUnitTest             # JVM unit tests
./gradlew connectedDebugAndroidTest     # device/emulator tests (DAO, migration, Compose structure)
./gradlew assembleRelease               # needs a signing config you create
```
Android Studio: **Build > Build APK(s)**; signed release via **Build > Generate Signed App Bundle / APK**.

## Using it
- Home: add music, scan a folder, rescan, search, recently added/played. Tap a song to play the list from it.
- Long-press a Home song: Play, Play next, Add to queue, Add to playlist, Add or remove favourite.
- Now Playing: long-press the artwork for the queue/shuffle/repeat/favourite/equalizer sheet; double-tap the artwork to toggle favourite.
- These gestures exist because the reference screens have no room for extra controls. They are not discoverable by sight.

## Layout
`data/` Room entities, DAOs, repositories, scanner, tag mapping. `playback/` Media3 service, controller, equalizer. `ui/` theme, components, screens, view models, navigation root.

## Known limitations
See `docs/VERIFICATION.md`. Windows: `docs/WINDOWS_PLAN.md` (not implemented).
