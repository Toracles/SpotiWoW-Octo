# GitHub release guide — SpotiWoW-Octo (FR/US)

This repository builds two localized add-on variants: **Français (FR)** and **English (US)**. The main Lua logic is shared. French text is in `Interface/AddOns/SpotiWoW-Octo/SpotiWoW-Octo_Locale.lua`; US English text is in `variants/US/SpotiWoW-Octo_Locale.lua`.

## Publish the repository without using the command line
1. Install GitHub Desktop and sign in to your GitHub account.
2. Extract the source kit into a permanent folder.
3. In GitHub Desktop, choose **File > Add local repository**. If it is not already a Git repository, choose **Create a repository here**.
4. Create a public repository named `SpotiWoW-Octo` and publish the local repository.
5. Confirm that `.github/workflows/release.yml`, `Interface`, `variants`, `companion`, and `installer` are present.
6. On GitHub, open **Releases > Draft a new release** and publish a tag such as `v1.4.0`.
7. Open the **Actions** tab and wait for `Build Windows release` to finish. The release should contain `SpotiWoW-Octo-Setup.exe`, `SpotiWoW-Octo-Portable-FR.zip`, and `SpotiWoW-Octo-Portable-US.zip`.
8. Share the release page link. Players only need to download `SpotiWoW-Octo-Setup.exe`.

## Publishing an update
For each update, push your changes to GitHub and publish a new release with a new tag (`v1.4.1`, `v1.5.0`, etc.). The workflow rebuilds the Windows assets and both localized packages.

## Editing translations
- French: `Interface/AddOns/SpotiWoW-Octo/SpotiWoW-Octo_Locale.lua` and the French `.toc` metadata.
- US English: `variants/US/SpotiWoW-Octo_Locale.lua` and `variants/US/SpotiWoW-Octo.toc`.
- Shared behavior lives in `Interface/AddOns/SpotiWoW-Octo/SpotiWoW-Octo.lua`. Any new player-facing strings should be added to both locale tables and referenced with `T("key")`.

## Spotify setup
Each player enters their own Spotify Client ID. Their Spotify Developer app must contain the exact Redirect URI `http://127.0.0.1:8888/callback`. Never ask for or publish a Client Secret, `tokens.json`, `config.json`, or a personal cache.

## What the installer does and does not do
- Detects common OctoWoW/Turtle WoW folders and lets the user browse for the folder containing `VanillaFixes.exe`.
- Installs the selected add-on language (FR or US) and the Windows companion.
- Does not download the WoW client, VanillaFixes, SuperWoW, SuperAPI, or their DLLs.
- The user must already have a compatible client and its required extensions.

## Recommended pre-release test
Install the release on a clean copy of a compatible Turtle WoW client. Test both FR and US packages, Spotify authorization, logs, stopping the bridge from the system-tray menu, and the `Ctrl+Alt+L` shortcut. Lyrics status is local; when enabled, actual lyrics still use the channel configured by the player.
