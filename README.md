# HomeLab
My home lab setup with various containers/VMs that I am self hosting! Pretty much everything I have is due to other creators which I have followed.

## Table of Contents
- Apps
- Media
- Cloud
- [Storage](https://github.com/toshjr22/HomeLab/tree/main/Storage)

## Hardware
Two Proxmox nodes running distinct roles for NAS/testing and production workloads.

| Node | Model | CPU | RAM | Storage | Filesystem | Role |
|------|-------|-----|-----|---------|------------|------|
| Node 1 | HP EliteDesk 800 G4 | Intel Core i5-8500 | 64 GB | 512 GB NVMe (ZFS RAID-Z2 pool, ~35 TB usable) | ZFS RAID-Z2 | NAS + light application/testing |
| Node 2 | Minisforum MS-O2 Ultra | Intel Core Ultra 5 235HX | 64 GB DDR5 SO-DIMM | 2 x 2 TB SN850x NVMe | local NVMe | Main production |

## Networking
- Current ISP: Xfinity 1.2 Gbps
- Current gateway: ISP gateway (Xfinity)
- Planned upgrade: Ubiquiti modem, router, and access points

## Software/Services
- Proxmox VE with containers/VMs
- ZFS storage and backup snapshots
- Monitoring and automation to be documented
