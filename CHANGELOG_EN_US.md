# Changelog

## v1.4.1
- Fixed the GitHub Actions release workflow by passing absolute icon and script paths to PyInstaller, preventing it from looking for the icon under `build/launcher`.
- Updated GitHub Actions to Node.js 24-compatible major versions to address the Node.js 20 deprecation warning.

## v1.4.0
- Added full French (FR) and US English add-on variants.
- Official add-on author: CloudNine_Ex.
- Localized local system messages, help, tooltips, and now-playing announcements.
- Ctrl+Alt+L still works without typing a command into the in-game chat. ON/OFF status is shown only in the local chat frame.
- The installer lets users choose a language and downloads the matching package.
- Technical identifiers and existing SavedVariables are retained for compatibility.
