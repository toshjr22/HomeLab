# Overview of Self Hosted Apps

## Table of Contents
- [Cloud](../Cloud/README.md)
- [Media](../Media/README.md)

## Layout
I organize Docker applications in specialized VMs on Proxmox, each dedicated to a specific service category. Docker files are centralized in the `/docker` directory, using a single `compose.yaml` for simple apps or subdirectories for complex multi-container setups.