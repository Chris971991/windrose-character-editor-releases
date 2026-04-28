# Windrose Character Editor — Releases

[![Latest release](https://img.shields.io/github/v/release/Chris971991/windrose-character-editor-releases?style=flat-square)](https://github.com/Chris971991/windrose-character-editor-releases/releases/latest)

Public binary releases for the **Windrose Character Editor** — a save-game editor for [Windrose](https://store.steampowered.com/app/3349750/Windrose/).

The editor reads & writes the game's RocksDB save under `%LOCALAPPDATA%\R5\Saved\SaveProfiles\…`, with full byte-equal BSON round-trip. PAK-derived stat math (Health, Defence, Attack Power, talent bonuses) ships baked-in, so you don't need .NET, Python, or any UE5 modding tooling.

## Install

1. Download the latest release from the [Releases page](https://github.com/Chris971991/windrose-character-editor-releases/releases).
2. **NSIS installer** (`Windrose Character Editor-<version>-x64.exe`) — runs an install wizard, creates Start Menu + desktop shortcuts. Per-user install, no admin required.
3. **Portable** (`Windrose Character Editor-<version>-x64.exe` portable variant, when shipped) — single .exe, runs from anywhere.
4. Auto-updates: once installed, the app checks this repo for new releases on launch and prompts to install.

## SmartScreen warning

Until the .exe is code-signed, Windows will show **"Windows protected your PC"** the first time you run the installer. Click **More info** → **Run anyway**. Subsequent launches won't show the warning.

## Catalog hot-patches

When Windrose patches between editor releases, a fresher PAK-derived catalog is published as a release asset (alongside the .exe) without bumping the editor version. The running app picks it up automatically on next launch, so stat math stays accurate without waiting for a full editor update.

## Compatibility

- **Game**: Windrose 0.10.0+ (Early Access)
- **OS**: Windows 10 / Windows 11 (x64)
- **Game install**: must own & have Windrose installed via Steam — the editor reads PAKs from your local install for asset path resolution.

## Source

The source code is private. Issues, feature requests, and bug reports go here:

- [Open an issue](https://github.com/Chris971991/windrose-character-editor-releases/issues)
- Discord: Gorgon Drifters guild

## License

See `LICENSE` in this repo.

## Disclaimer

This tool is for **single-player and your-own-server** use. Editing your character on shared / dedicated servers may be considered cheating by other players or admins — use accordingly. The editor has no telemetry, analytics, or phone-home behaviour; everything runs locally and only contacts GitHub for update checks.
