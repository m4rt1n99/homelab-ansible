# Raspberry Pi Homelab
The purpose of this repo is to share my local homelab setup. While mainly NAS focused, I'm always looking for software and other tools that can benefit my quality of life.
I chose ansible for the ease of deployment of new services, simple syntax, and prior experience.

## Current setup
- Raspberry Pi 5 8GB running Raspberry Pi OS headless
- Argon NEO 5 case with active cooling and NVMe support
- Two USB-connected 3.5" HDD in RAID 1 ZFS pool for data safety
- 1TB NVMe drive connected by case PCIe

## What the playbook does
- Updates the system packages and prepares for upcoming roles
- Sets up samba sharing using a dedicated user
- Sets up mirrored zfs pool on two HDDs

## Setup
See [SETUP.md](SETUP.md) for the full setup and run instructions.

## TODO
- Navidrome
- Immich
- Jellyfin
- [hdd-spindown.sh](https://github.com/lynix/hdd-spindown.sh)
  
## License
See [LICENSE](LICENSE).
