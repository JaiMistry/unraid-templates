<p align="center">
  <img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/internal/web/static/img/logo-mark.svg" width="160" height="160" alt="AutoThrottle logo">
</p>

<h1 align="center">AutoThrottle</h1>

<p align="center">
  <strong>Intelligently throttles download clients while a media server has active playback.</strong>
</p>

<p align="center">
  <a href="https://github.com/JaiMistry/autothrottle/actions/workflows/ci.yml"><img src="https://img.shields.io/github/actions/workflow/status/JaiMistry/autothrottle/ci.yml?branch=main&label=build" alt="Build status"></a>
  <a href="https://codecov.io/gh/JaiMistry/autothrottle"><img src="https://codecov.io/gh/JaiMistry/autothrottle/branch/main/graph/badge.svg" alt="Coverage"></a>
  <a href="https://github.com/JaiMistry/autothrottle/releases/latest"><img src="https://img.shields.io/docker/v/jaimistry/autothrottle?sort=semver&label=version" alt="Latest version"></a>
  <a href="https://hub.docker.com/r/jaimistry/autothrottle"><img src="https://img.shields.io/docker/pulls/jaimistry/autothrottle" alt="Docker pulls"></a>
  <a href="https://hub.docker.com/r/jaimistry/autothrottle"><img src="https://img.shields.io/docker/image-size/jaimistry/autothrottle/latest?label=size" alt="Size"></a>
  <a href="https://ca.unraid.net/apps/autothrottle-0xufrs017fz9b0"><img src="https://img.shields.io/badge/Unraid-Community%20Apps-f15a2c" alt="Unraid Community Apps"></a>
</p>

AutoThrottle dynamically lowers your download client speeds while something is playing on your media server, and restores them when playback stops. Set it up once and it looks after itself from then on. The throttling is aware of what is actually happening. A paused stream stays throttled, one that has sat paused or stalled for 30 minutes is let go, and playback on your own network can be ignored. When you want full speed regardless, one click turns throttling off until you turn it back on.

## ⭐ Features

- **Live dashboard:** A modern reactive UI with live updates as they occur.
- **Near-real-time detection:** Listens to each server's live feed.
- **Autoplay-aware:** Back-to-back episodes being played will hold throttling, preventing unnecessary rate changes.
- **Pause-aware:** A paused stream stays throttled until a 30-minute timeout.
- **Local playback exemption:** Streams on your own network can be ignored, so only remote connections count.
- **Mappings:** Control which media servers throttle which download clients.
- **Restart/crash-safe:** Rates are reapplied on startup, so nothing stays stuck slow.
- **Throttle history:** A 7- and 30-day heatmap of when your downloads were held back.
- **Secure:** All sensitive credentials are securely encrypted and never leaked.
- **Lightweight:** A single distroless image with a minimal footprint.
- **Runs anywhere:** Docker on amd64 and arm64, Unraid Community Apps, and as a native Windows service.

## 🧩 Supported versions

| | Media server | Version |
|:-:|---|---|
| <a href="https://www.plex.tv"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/plex.svg" width="18" height="18" alt="Plex Media Server"></a> | Plex Media Server | 1.43+ |
| <a href="https://jellyfin.org"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/jellyfin.svg" width="18" height="18" alt="Jellyfin"></a> | Jellyfin | 10.11+ |
| <a href="https://emby.media"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/emby.svg" width="18" height="18" alt="Emby"></a> | Emby | 4.9+ |

| | Download client | Version |
|:-:|---|---|
| <a href="https://www.qbittorrent.org"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/qbittorrent.svg" width="18" height="18" alt="qBittorrent"></a> | qBittorrent | 5.2+ |
| <a href="https://transmissionbt.com"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/transmission.svg" width="18" height="18" alt="Transmission"></a> | Transmission | 4.1+ |
| <a href="https://deluge-torrent.org"><img src="https://raw.githubusercontent.com/JaiMistry/autothrottle/main/.github/assets/logos/deluge.svg" width="18" height="18" alt="Deluge"></a> | Deluge | 2.1+ |

## ⚙️ Environment variables

All are optional.

| Variable | Default | What it does |
|---|---|---|
| `TZ` | Unraid's time zone | Time zone for timestamps. |
| `PUID` | `99` | User that owns the data folder. |
| `PGID` | `100` | Group that owns the data folder. |
| `AUTH_USERNAME` | | Sign-in username from the environment instead of creating an account. Set with `AUTH_PASSWORD`. |
| `AUTH_PASSWORD` | | Sign-in password from the environment. Set with `AUTH_USERNAME`. |
| `AUTH_DISABLED` | `false` | Turns off sign-in. Only use this behind a proxy that handles it. |

## 🛠️ First-time setup

Open `http://<your-server>:7676` and create your account. Everything else
happens on the **Configuration** page:

1. **Add a media server** with its URL and token or API key. For Plex you can
   sign in with your Plex account instead of pasting a token.
2. **Add a download client** with two pairs of rates:
   - **Default rates**, applied when nothing is playing.
   - **Throttled rates**, applied while a mapped server is playing.

   Rates are in KB/s, and `0` means unlimited.
3. **Map them.** Choose which media servers throttle which download clients.

## License

[GPL-3.0](https://github.com/JaiMistry/autothrottle/blob/main/LICENSE)

<p align="center"><sub>Made with ❤️ by <a href="https://github.com/JaiMistry">JaiMistry</a></sub></p>
