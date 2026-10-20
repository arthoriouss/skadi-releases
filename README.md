# SKADI releases

Public binaries and the update feed for **SKADI**, a TV and desktop client for your own **Plex**, **Jellyfin** and **Emby** media servers.

> SKADI is an unofficial, third-party client. It is **not affiliated with, endorsed by or sponsored by** Plex Inc., Jellyfin or Emby. All product names are trademarks of their respective owners.

This repository only hosts releases (`appcast.xml` is the Windows update feed). The source code is not published here.

## Platforms

| Platform | Status | Distribution |
| --- | --- | --- |
| Windows x64 | Beta | Installer `.exe` with built-in updates (WinSparkle), portable `.zip` |
| Linux x64 | Beta | `.deb`, `.rpm`, `.flatpak`, `.tar.gz` |
| Fire TV | Beta, coming | Amazon Live App Testing (by invitation) |
| Android TV | Coming soon | - |
| LG webOS | Closed beta, coming soon | - |

Supported servers: Plex, Jellyfin, Emby.

## Download

Get the latest release: <https://github.com/arthoriouss/skadi-releases/releases/latest>

| You are on | Download |
| --- | --- |
| Windows, normal install (recommended, updates itself) | `SKADI-Setup-<version>-windows-x64.exe` |
| Windows, no installer | `SKADI-<version>-windows-x64-portable.zip` |
| Debian, Ubuntu and derivatives | `SKADI-<version>-linux-amd64.deb` |
| Fedora and RPM-based distributions | `SKADI-<version>-linux-x86_64.rpm` |
| Any distribution with Flatpak | `SKADI-<version>-linux-x86_64.flatpak` |
| Any distribution, no package manager | `SKADI-<version>-linux-x64.tar.gz` |

The `*-manifest.json`, `release-index.json` and `appcast.xml` files are used by the release tooling and the updater; you do not need them.

### Verify your download

Each release includes `SHA256SUMS.txt`. Compare the hash of your file with the matching line.

Windows (PowerShell):

```powershell
Get-FileHash .\SKADI-Setup-<version>-windows-x64.exe -Algorithm SHA256
```

Linux:

```bash
sha256sum SKADI-<version>-linux-amd64.deb
# or check every file you downloaded next to SHA256SUMS.txt:
sha256sum --check --ignore-missing SHA256SUMS.txt
```

## Install

### Windows

Run the installer, or unzip the portable archive and start SKADI from it. Installing a newer version over an existing one updates it in place.

The installer is signed only when the release was built with a code-signing certificate. If Windows SmartScreen warns about an unrecognized app, check the SHA-256 hash above before choosing to run it.

### Linux

- **Flatpak** (application id `com.skadi.client`):
  ```bash
  flatpak install ./SKADI-<version>-linux-x86_64.flatpak
  flatpak run com.skadi.client
  ```
  The bundle points to Flathub for the Freedesktop 25.08 runtime, so no manual remote setup should be needed. The Flatpak ships its own pinned mpv.
- **Debian / Ubuntu:** `sudo apt install ./SKADI-<version>-linux-amd64.deb` (installs to `/opt/skadi`, command `skadi`).
- **Fedora:** `sudo dnf install ./SKADI-<version>-linux-x86_64.rpm`
- **tar.gz:** extract it anywhere and run the `skadi` executable from the extracted folder.

The `.deb` and `.rpm` rely on the distribution's `libmpv` package.

## Reporting a bug

Open an issue on this repository: <https://github.com/arthoriouss/skadi-releases/issues>. Please include your SKADI version, platform and OS version, and the server type (Plex, Jellyfin or Emby). Do not paste server URLs or tokens. Issue templates are coming soon.

## Privacy

Crash reports and playback compatibility reports are **opt-in** and off by default; they are two separate choices. Reports are limited to technical data (for example device model, OS version, formats and codecs, playback outcome). Titles, server names and addresses, URLs, media paths, tokens, user names and e-mail addresses are not sent; free text is redacted before sending.

- Privacy policy: coming soon
- End-user license agreement (EULA): coming soon
