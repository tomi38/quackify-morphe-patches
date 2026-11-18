# Quackify Morphe Patches

Community [Morphe](https://github.com/MorpheApp) patches for [Quackify](https://github.com/23fpsz/Quackify), the open-source native Android Spotify client.

## Usage

In Morphe Manager, add this repository as a patch source:

```
https://github.com/tomi38/quackify-morphe-patches
```

Or download the latest `patches-*.mpp` from [Releases](https://github.com/tomi38/quackify-morphe-patches/releases) and load it manually.

Supported packages (all three [Quackify release](https://github.com/23fpsz/Quackify/releases) flavors):

| Flavor | Package |
|--------|---------|
| standard | `com.quackify.app` |
| spotify | `com.spotify.music` |
| apple | `com.apple.android.music` |

The `spotify` and `apple` flavors reuse those apps' package names, so Morphe Manager also lists this patch for the official apps. The patch checks that the APK really is Quackify and fails otherwise.

## Patches

<!-- PATCHES_START EXPANDED -->
| 💊&nbsp;Patch | 📜&nbsp;Description |
|----------|----------------|
| Spotify branding | Renames Quackify to Spotify and replaces the launcher (both icon choices), splash, widget and notification icons with the Spotify mark. |
<!-- PATCHES_END -->

## Building

The Morphe Gradle plugin is hosted on GitHub Packages, so a token with `read:packages` is required:

```sh
GITHUB_ACTOR=<user> GITHUB_TOKEN=<token> ./gradlew :patches:buildAndroid
```

Quackify's launcher icons are WebP bitmaps, so the patch bundles pre-rendered PNGs in `patches/src/main/resources/quackify/branding/`. Regenerate them with:

```sh
java scripts/RenderIcons.java patches/src/main/resources/quackify/branding
```

Releases are created automatically by semantic-release from Conventional Commits on `main` (`feat:` → minor, `fix:` → patch).

## License

GPLv3. See [LICENSE](LICENSE) and [NOTICE](NOTICE).
