# My Homelab in ansible
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
1. Setup the user as described in [SETUP.md](SETUP.md)
2. Run the playbook using `ansible-playbook -i inventory/hosts.yml site.yml `

## TODO
- Setup Navidrome
 - Write a python script to retreive music to store in the local navidrome library
- Setup Immich
- Add [hdd-spindown.sh](https://github.com/lynix/hdd-spindown.sh) to the setup role
  
## License
See [LICENSE](LICENSE).
