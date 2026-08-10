# Raspberry Pi Home Server

A lightweight self-hosted home server built with a Raspberry Pi 4 Model B.

**Learn • Build • Self-Host**

---

## About

This project turns a Raspberry Pi 4 Model B into a lightweight home server for running useful self-hosted services on a local network.

The server uses DietPi as the operating system and CasaOS as a simple web-based interface for managing applications.

### Services

- Pi-hole — Network-wide DNS filtering
- Jellyfin — Personal media server
- Navidrome — Personal music server
- CasaOS — Server and application management

The project is also a practical home lab for learning Linux, networking, Docker, storage management, server administration, and self-hosting.

---

## Features

### Self-Hosted Home Server

Run useful services locally on your own Raspberry Pi instead of depending entirely on cloud services.

### Media Streaming

Use Jellyfin to organize and stream personal movies and TV shows across devices on the home network.

### Music Streaming

Use Navidrome to access and stream a personal music collection from computers, phones, and other supported devices.

### Network-Wide DNS Filtering

Pi-hole provides DNS-based ad and tracker blocking for devices connected to the home network.

### Simple Server Management

CasaOS provides a convenient web interface for managing applications and services running on the server.

### Lightweight Linux Server

DietPi provides a lightweight Linux environment designed to keep resource usage low on Raspberry Pi hardware.

---

# System Architecture

```text
                         +---------------------+
                         |      Internet       |
                         +----------+----------+
                                    |
                         +----------v----------+
                         |    Home Router      |
                         |   Network / DHCP    |
                         +----------+----------+
                                    |
                              Ethernet
                                    |
                         +----------v----------+
                         |   Raspberry Pi 4    |
                         |      Model B        |
                         +----------+----------+
                                    |
                         +----------v----------+
                         |       DietPi        |
                         |      Linux OS       |
                         +----------+----------+
                                    |
                         +----------v----------+
                         |       CasaOS         |
                         |  Server Management  |
                         +----------+----------+
                                    |
                +-------------------+-------------------+
                |                   |                   |
        +-------v-------+   +-------v------+   +--------v--------+
        |    Jellyfin   |   |  Navidrome  |   |     Pi-hole     |
        |  Media Server |   | Music Server|   |   DNS Filtering |
        +-------+-------+   +------+-------+   +-----------------+
                |                  |
                +--------+---------+
                         |
                  +------v------+
                  |  USB SSD/HDD|
                  |             |
                  |  Movies     |
                  |  TV Shows   |
                  |  Music      |
                  +-------------+
```

---

# Hardware

| Component | Description |
|---|---|
| Raspberry Pi | Raspberry Pi 4 Model B |
| System Storage | microSD card |
| Media Storage | USB SSD/HDD |
| Network | Ethernet |
| Power | Raspberry Pi-compatible power supply |
| Display | Optional |
| Keyboard | Optional |

> Recommendation: Use a USB 3 SSD/HDD for the media library instead of storing large amounts of media on the microSD card.

---

# Software

| Software | Purpose |
|---|---|
| DietPi | Lightweight Linux operating system |
| CasaOS | Web-based server management |
| Pi-hole | DNS-based ad and tracker blocking |
| Jellyfin | Media server |
| Navidrome | Music server |
| Docker | Container management |

---

# Storage Structure

```text
/mnt/storage/
└── media/
    ├── movies/
    ├── tv/
    └── music/
```

### Movies

```text
movies/
├── Movie 1/
│   └── Movie 1.mkv
├── Movie 2/
│   └── Movie 2.mp4
└── Movie 3/
    └── Movie 3.mkv
```

### TV Shows

```text
tv/
├── Show 1/
│   ├── Season 01/
│   │   ├── S01E01.mkv
│   │   └── S01E02.mkv
│   └── Season 02/
└── Show 2/
    └── Season 01/
```

### Music

```text
music/
├── Artist 1/
│   └── Album/
│       ├── 01 - Song.mp3
│       └── 02 - Song.mp3
└── Artist 2/
    └── Album/
        └── 01 - Song.flac
```

---

# Installation

## 1. Install DietPi

Download the latest Raspberry Pi version of DietPi:

https://dietpi.com/

Flash the DietPi image to a microSD card using Raspberry Pi Imager or balenaEtcher.

Insert the microSD card into the Raspberry Pi.

Connect:

- Ethernet cable
- Power supply
- Optional HDMI display
- Optional keyboard

Power on the Raspberry Pi and complete the initial DietPi setup.

---

## 2. Connect Using SSH

Find the Raspberry Pi's IP address:

```bash
hostname -I
```

Example:

```text
192.168.1.100
```

Connect from another computer:

```bash
ssh root@192.168.1.100
```

Replace the IP address with the actual address of your Raspberry Pi.

---

# 3. Update DietPi

Update the package list:

```bash
apt update
```

Upgrade installed packages:

```bash
apt upgrade -y
```

Reboot:

```bash
reboot
```

Reconnect using SSH after the Raspberry Pi starts again.

---

# 4. Configure the Network

A wired Ethernet connection is recommended for this server.

Check network interfaces:

```bash
ip addr
```

Check the current IP:

```bash
hostname -I
```

For a home server, the Raspberry Pi should have a predictable IP address.

### Recommended

Create a DHCP reservation in your router.

Example:

```text
Raspberry Pi
      |
      +-- 192.168.1.100
```

This allows services to remain accessible at the same IP address.

---

# 5. Install CasaOS

CasaOS provides a web interface for managing applications and services.

Install CasaOS:

```bash
curl -fsSL https://get.casaos.io | sudo bash
```

After installation, open:

```text
http://<RASPBERRY_PI_IP>
```

Example:

```text
http://192.168.1.100
```

Complete the initial CasaOS configuration.

> Note: Check the current CasaOS documentation for supported operating systems and installation requirements before installing on a new system.

---

# 6. Connect External Storage

Connect the USB SSD/HDD to the Raspberry Pi.

List available drives:

```bash
lsblk
```

Example:

```text
sda
└── sda1

mmcblk0
├── mmcblk0p1
└── mmcblk0p2
```

Create a mount directory:

```bash
mkdir -p /mnt/storage
```

Mount the external drive:

```bash
mount /dev/sda1 /mnt/storage
```

Check the mounted storage:

```bash
df -h
```

Create the media directories:

```bash
mkdir -p /mnt/storage/media
mkdir -p /mnt/storage/media/movies
mkdir -p /mnt/storage/media/tv
mkdir -p /mnt/storage/media/music
```

Final structure:

```text
/mnt/storage/
└── media/
    ├── movies/
    ├── tv/
    └── music/
```

> Important: /dev/sda1 is only an example. Always verify the correct drive using lsblk before mounting or formatting anything.

---

# 7. Install Pi-hole

Pi-hole provides network-wide DNS filtering.

Install Pi-hole using the official installation method:

```bash
curl -sSL https://install.pi-hole.net | bash
```

During installation:

1. Select the correct network interface.
2. Confirm the Raspberry Pi's IP address.
3. Select an upstream DNS provider.
4. Enable the web interface.
5. Set the administrator password.

## Open Pi-hole

```text
http://<RASPBERRY_PI_IP>/admin
```

Example:

```text
http://192.168.1.100/admin
```

## Configure Router DNS

To use Pi-hole for the home network, configure the router's DNS server to use the Raspberry Pi.

Example:

```text
Primary DNS:
192.168.1.100
```

The exact procedure depends on the router.

> Make sure Pi-hole is working correctly before changing DNS settings for the entire network.

Check Pi-hole status:

```bash
pihole status
```

---

# 8. Install Jellyfin

Jellyfin is used as the personal media server.

Open CasaOS:

```text
http://<RASPBERRY_PI_IP>
```

Open the application store and install Jellyfin.

Configure the media storage so Jellyfin can access:

```text
/mnt/storage/media
```

Recommended libraries:

```text
Movies
└── /media/movies

TV Shows
└── /media/tv
```

## Open Jellyfin

Jellyfin normally uses port 8096.

```text
http://<RASPBERRY_PI_IP>:8096
```

Example:

```text
http://192.168.1.100:8096
```

Complete the Jellyfin setup wizard:

1. Select language.
2. Create administrator account.
3. Add media libraries.
4. Select media folders.
5. Configure playback settings.
6. Finish setup.

## Raspberry Pi 4 Transcoding

The Raspberry Pi 4 can run Jellyfin, but heavy video transcoding can put significant load on the system.

Whenever possible, use:

```text
Direct Play
```

instead of requiring the Raspberry Pi to transcode video.

---

# 9. Install Navidrome

Navidrome is used as the personal music server.

Create the music directory:

```bash
mkdir -p /mnt/storage/media/music
```

Install Navidrome through CasaOS/Docker.

Configure its music library to:

```text
/mnt/storage/media/music
```

Navidrome normally uses port 4533.

Open:

```text
http://<RASPBERRY_PI_IP>:4533
```

Example:

```text
http://192.168.1.100:4533
```

---

# 10. Add Music

Copy music files into:

```text
/mnt/storage/media/music
```

Example:

```text
music/
├── Artist 1/
│   └── Album 1/
│       ├── 01 - Song.mp3
│       ├── 02 - Song.mp3
│       └── 03 - Song.mp3
└── Artist 2/
    └── Album 1/
        └── 01 - Song.flac
```

Navidrome will scan the music library and organize the collection using the available metadata.

---

# Service Access

| Service | Port | Address |
|---|---:|---|
| CasaOS | 80 | http://192.168.1.100 |
| Pi-hole | 80 | http://192.168.1.100/admin |
| Jellyfin | 8096 | http://192.168.1.100:8096 |
| Navidrome | 4533 | http://192.168.1.100:4533 |

> Ports may differ depending on your installation and configuration.

---

# Docker

CasaOS uses Docker for many applications.

Check Docker:

```bash
docker --version
```

List running containers:

```bash
docker ps
```

List all containers:

```bash
docker ps -a
```

View container logs:

```bash
docker logs <container_name>
```

Restart a container:

```bash
docker restart <container_name>
```

Stop a container:

```bash
docker stop <container_name>
```

Start a container:

```bash
docker start <container_name>
```

---

# Useful Linux Commands

## Check CPU and RAM

```bash
htop
```

## Check storage

```bash
df -h
```

## List disks

```bash
lsblk
```

## Check IP address

```bash
hostname -I
```

## Check network interfaces

```bash
ip addr
```

## Check listening ports

```bash
ss -tulpn
```

## Check memory

```bash
free -h
```

## Check Raspberry Pi temperature

```bash
vcgencmd measure_temp
```

## Update packages

```bash
sudo apt update
sudo apt upgrade -y
```

## Reboot

```bash
sudo reboot
```

## Shutdown

```bash
sudo shutdown now
```

---

# Security

This server is primarily designed for use on a trusted home network.

Recommended practices:

- Use strong passwords.
- Keep DietPi updated.
- Keep CasaOS updated.
- Keep applications updated.
- Avoid exposing administration panels directly to the internet.
- Use SSH keys where possible.
- Keep important data backed up.
- Use a firewall where appropriate.
- Do not expose Pi-hole administration publicly.
- Avoid unnecessary port forwarding.

## Remote Access

If remote access is required, use a secure VPN or another properly configured remote-access solution rather than directly exposing administration interfaces to the public internet.

---

# Backup

The Raspberry Pi should not be considered a backup by itself.

Important data should be copied to another storage device.

```text
                 Raspberry Pi
                      |
              +-------+-------+
              |               |
          Main SSD        Backup Drive
              |               |
          Media Files       Backup
```

Important data to back up:

- Movies
- TV shows
- Music
- Jellyfin configuration
- Navidrome configuration
- Navidrome database
- Pi-hole configuration
- CasaOS application data

---

# Monitoring

Useful information to monitor:

```text
CPU Usage
RAM Usage
Storage Usage
Temperature
Network Activity
Docker Containers
Service Availability
```

Useful commands:

```bash
htop
```

```bash
df -h
```

```bash
free -h
```

```bash
vcgencmd measure_temp
```

---

# Testing

After completing the installation, test each service.

### CasaOS

```text
http://<RASPBERRY_PI_IP>
```

### Pi-hole

```text
http://<RASPBERRY_PI_IP>/admin
```

### Jellyfin

```text
http://<RASPBERRY_PI_IP>:8096
```

### Navidrome

```text
http://<RASPBERRY_PI_IP>:4533
```

---

# Client Devices

Services can be accessed from computers, phones, TVs, and other devices connected to the home network.

```text
                    Home Network
                         |
          +--------------+--------------+
          |              |              |
        Laptop         Phone         Smart TV
          |              |              |
          +--------------+--------------+
                         |
                  Raspberry Pi 4
                         |
          +--------------+--------------+
          |              |              |
       Jellyfin      Navidrome      Pi-hole
```

---

# What I Learned

This project provides practical experience with:

- Linux administration
- SSH
- Networking
- DNS
- DHCP
- Docker
- Container management
- Storage management
- Media servers
- Music servers
- Server security
- Raspberry Pi administration
- Self-hosting

---

# Future Improvements

- [ ] Automated backups
- [ ] Uptime Kuma
- [ ] Samba file sharing
- [ ] Home Assistant
- [ ] WireGuard VPN
- [ ] Server monitoring dashboard
- [ ] Network monitoring
- [ ] UPS battery backup
- [ ] SSD boot
- [ ] Automatic backup system
- [ ] Additional self-hosted applications

---

# Project Gallery

Add your project images to the images directory.

```text
images/
├── server.jpg
├── casaos.jpg
├── jellyfin.jpg
├── navidrome.jpg
└── pihole.jpg
```

Use them in the README:

```markdown
![Raspberry Pi Home Server](images/server.jpg)

![CasaOS Dashboard](images/casaos.jpg)

![Jellyfin](images/jellyfin.jpg)

![Navidrome](images/navidrome.jpg)

![Pi-hole](images/pihole.jpg)
```

---

# Repository Structure

```text
Raspberry-Pi-Home-Server/
|
├── README.md
|
├── images/
|   ├── server.jpg
|   ├── casaos.jpg
|   ├── jellyfin.jpg
|   ├── navidrome.jpg
|   └── pihole.jpg
|
└── documentation/
    └── notes.md
```

---

# Project Information

| Category | Details |
|---|---|
| Project Type | Home Server / Homelab |
| Hardware | Raspberry Pi 4 Model B |
| Operating System | DietPi |
| Management | CasaOS |
| Media Server | Jellyfin |
| Music Server | Navidrome |
| DNS Filtering | Pi-hole |
| Network | Ethernet |
| Storage | USB SSD/HDD |
| Status | Active |

---

# Official Documentation

- Raspberry Pi: https://www.raspberrypi.com/
- DietPi: https://dietpi.com/
- CasaOS: https://casaos.io/
- Pi-hole: https://pi-hole.net/
- Jellyfin: https://jellyfin.org/
- Navidrome: https://www.navidrome.org/

---

# Author

**Gavindu Kavishka**

Technology enthusiast building and learning through practical projects.

- GitHub: https://github.com/gavindu2006
- Portfolio: https://gavindu2006.pages.dev/

---

<p align="center">
  <strong>Learn. Build. Master.</strong>
</p>

<p align="center">
  Built with ❤️ using Raspberry Pi
</p>
