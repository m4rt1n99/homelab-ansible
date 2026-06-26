# Raspberry Pi Homelab
The purpose of this repo is to share my local homelab setup. While mainly NAS focused, I'm always looking for software and other tools that can benefit my quality of life.
I chose ansible for the ease of deployment of new services, simple syntax, and prior experience.

## Current setup
- Raspberry Pi 5 8GB running Raspberry Pi OS headless
- Argon NEO 5 case with active cooling and NVMe support
- Two USB-connected 3.5" HDD in RAID 1 ZFS pool for data safety
- 1TB NVMe drive connected by case PCIe

## What the playbook does
The playbook is split into roles. The base roles prepare the host and storage:

- Update system packages and prepare the host for the roles below
- Set up Samba sharing served by a dedicated user
- Create a mirrored (RAID 1) ZFS pool across the two HDDs
- Install and manage hdd-spindown for automatic HDD standby
- Deploy **[Homepage](https://github.com/gethomepage/homepage)**, a dashboard that links to every service below

It then deploys the following services as Podman containers:

### Movies & TV
- **[Jellyfin](https://github.com/linuxserver/docker-jellyfin):** Media server for streaming movies and TV shows.
- **[Seerr](https://seerr.dev/):** Request management and media discovery; users request movies/TV that Radarr and Sonarr then fetch.
- **[Radarr](https://github.com/linuxserver/docker-radarr):** Movie collection management and automation.
- **[Sonarr](https://github.com/linuxserver/docker-sonarr):** TV show collection management and automation.
- **[Prowlarr](https://github.com/linuxserver/docker-prowlarr):** Indexer manager that feeds Radarr and Sonarr.
- **[FlareSolverr](https://github.com/FlareSolverr/FlareSolverr):** Cloudflare challenge solver for Prowlarr indexers.
- **[qBittorrent](https://github.com/linuxserver/docker-qbittorrent):** BitTorrent client, using Gluetun as a VPN.
- **[Gluetun](https://github.com/qdm12/gluetun):** WireGuard VPN container that qBittorrent runs behind.

### Music
- **[Navidrome](https://github.com/navidrome/navidrome):** Music streaming server and library.
- **[slskd](https://github.com/slskd/slskd):** Soulseek client for grabbing music.
- **[MusicGrabber](https://gitlab.com/g33kphr33k/musicgrabber):** Music downloader for singles.
- **[SoulSync](https://github.com/Nezreka/SoulSync):** Music discovery and automation that downloads via slskd and organizes into the Navidrome library.

### Photos
- **[Immich](https://github.com/immich-app/immich):** Self-hosted photo and video backup and management.

## Setup
See [SETUP.md](SETUP.md) for the full setup and run instructions.

## Disclaimer: Use of AI
An AI model was used in this project to help with readability and comments.

## License
See [LICENSE](LICENSE).
