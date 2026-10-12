# Evidence index

Each evidence item has an ID that the control, risk, and finding tables refer to. Raw captures contain private addresses and names, so they are kept private. This page records what each one is and what it showed.

Evidence types: **Command output** (captured from the server), **Document** (a file in this repo or in [homelab-docs](https://github.com/tbrown70128/homelab-docs)), **Owner attestation** (stated by the administrator, not captured).

| ID | Date | Type | What it shows |
| --- | --- | --- | --- |
| E-01 | 2026-10-12 | Document | Service inventory, hardware list, and compose files in [homelab-docs](https://github.com/tbrown70128/homelab-docs/blob/main/docs/architecture.md) |
| E-02 | 2026-10-12 | Command output | SSH server settings show password login off. A password attempt was refused. Key login worked from both admin machines |
| E-03 | 2026-10-12 | Command output | Every running container uses a versioned image tag. No floating tags remain |
| E-04 | 2026-10-12 | Command output | Container mount listings show no Docker socket in the monitoring containers, apart from the read-only filtering proxy |
| E-05 | 2026-10-12 | Command output | An encrypted backup was decrypted with the offline key. The archive listing showed the database snapshot and the key file |
| E-06 | 2026-10-12 | Command output | Host firewall rule listings before and after removing rules for a retired VPN |
| E-07 | 2026-10-12 | Command output | File permissions on service secret files, before and after the fix |
| E-08 | 2026-10-12 | Owner attestation | Reverse proxy certificate list is empty. The dynamic DNS account has no domains and the token was regenerated |
| E-09 | 2026-10-12 | Command output | Scheduled job listing and monitor list, before and after removing retired VPN items |
| E-10 | Ongoing | Document | Blameless [incident write-ups](https://github.com/tbrown70128/homelab-docs/tree/main/docs/incidents) |
| E-11 | Ongoing | Document | [Decision records](https://github.com/tbrown70128/homelab-docs/tree/main/docs/decisions) |
| E-12 | 2026-10-12 | Document | [Security controls table](https://github.com/tbrown70128/homelab-docs/blob/main/docs/security-controls.md), corrected after the configuration audit |
| E-13 | 2026-10-12 | Owner attestation | Router administrator password was changed and automatic firmware updates are on |
| E-14 | 2026-10-12 | Owner attestation | Two-factor authentication is on Home Assistant and not yet on every service |
| E-15 | 2026-10-12 | Owner attestation | Household members have separate logins |
| E-16 | 2026-10-12 | Command output | Backup script change reviewed as a diff, and a manual run logged the local and Nextcloud copies. Old unencrypted archives were deleted and the folder listing confirmed it |
| E-17 | 2026-10-12 | Command output | Disk usage and volume group free space on the server |
| E-18 | 2026-10-12 | Command output | Tailscale device list showing a device offline for months |
| E-19 | 2026-10-12 | Owner attestation | The Nextcloud backup folder is not shared with anyone |
| E-20 | 2026-10-12 | Owner attestation | The server has no battery backup. Disks are not encrypted |
| E-21 | 2026-10-12 | Command output | A search of the administrator's user profile found no unencrypted vault backup archives |
| E-22 | 2026-10-12 | Owner attestation | The device that had been offline for months was removed from the private network admin console |
| E-23 | 2026-10-12 | Command output | The file sharing services are inactive and disabled, and their ports are closed. The only share was an empty folder |
| E-24 | 2026-10-12 | Command output | After extending the system volume, the file system grew online and usage fell from 76 percent to 51 percent |
