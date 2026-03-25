# Storage

## Current Hardware
- HBA: Inspur 9300-8i
- Enclosures: two SilverStone 5-bay HDD enclosures
- Drives:
  - 1x 14 TB Seagate Exos X14
  - 2x 10 TB Seagate Exos X16
  - 3x 16 TB Seagate Exos X16
- ZFS pool: RAID-Z2

## Creating SMB shares using Samba
- Layout: currently using `/tank`
- Set ownership:
  - `sudo chown -R youruser:youruser /mountpoint`
- Set services to auto start on reboot:
  - `sudo systemctl enable smbd`
  - `sudo systemctl enable nmbd`
  - `sudo systemctl restart smbd`
  - `sudo systemctl restart nmbd`
- Install wsdd2 for Windows network discovery:
  - `sudo apt install wsdd2`
  - `sudo systemctl enable wsdd2`
  - `sudo systemctl start wsdd2`

## Connecting to shares
### Linux
You can mount SMB shares temporarily or permanently on Linux clients.

#### Temporary Mount
- Install cifs-utils if not already installed:
  - `sudo apt install cifs-utils`
- Create mount point:
  - `sudo mkdir -p /mnt/data`
- Mount the share (you'll be prompted for password):
  - `sudo mount -t cifs //SERVER-IP/data /mnt/data -o username=youruser`

#### Permanent Mount (fstab)
Create a credentials file:
- `sudo nano /etc/samba/credentials`
- Add:
  ```
  username=youruser
  password=yourpassword
  ```
- Secure it:
  - `sudo chmod 600 /etc/samba/credentials`
- Add to `/etc/fstab`:
  - `//SERVER-IP/data /mnt/data cifs x-systemd.automount,credentials=/etc/samba/credentials,uid=1000,gid=1000 0 0`
- Mount it:
  - `sudo mount -a`

### Windows: Connecting to Shares
From Windows: Since `guest ok = no` is set in the config, Windows requires explicit credentials to connect.

Map Network Drive (Recommended)
- Open File Explorer
- Right-click "This PC" → "Map network drive"
- Enter `\\SERVER-IP\data` (e.g., `\\192.168.1.100\data`)
- Check ✅ "Connect using different credentials"
- Enter your Samba username and password (created with `smbpasswd`)

Quick Access
- Press `Win + R`, type `\\SERVER-IP\data`, and press Enter.
- Enter credentials when prompted.

### iOS
- Open the Files app
- Tap the three dots (...) in the top right → "Connect to Server"
- Enter `smb://SERVER-IP` (e.g., `smb://192.168.1.100`)
- Select "Registered User" and enter your Samba credentials
- Your shares will appear under "Shared" in the Files app

## ZFS
Common commands:
- `zpool status`
- `zpool list`
- `zpool iostat -v`
- `zpool scrub <pool>`
- `zfs list`
- `zfs status`
- `zfs snapshot <pool/dataset>@<name>`
- `zfs rollback <pool/dataset>@<name>`
- `zfs set compression=lz4 <pool/dataset>`

