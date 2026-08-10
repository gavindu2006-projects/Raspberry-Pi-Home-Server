<div align="center">

# 🏠 Raspberry Pi Home Server

### 🥧 Self-Hosted • 🎬 Media • 🎵 Music • 🛡️ Network

A lightweight self-hosted home server built with a **Raspberry Pi 4 Model B**.

<br>

[![Raspberry Pi](https://img.shields.io/badge/Raspberry%20Pi-4%20Model%20B-C51A4A?style=for-the-badge&logo=raspberrypi&logoColor=white)](https://www.raspberrypi.com/)
[![DietPi](https://img.shields.io/badge/DietPi-Linux-0F6B3A?style=for-the-badge&logo=linux&logoColor=white)](https://dietpi.com/)
[![CasaOS](https://img.shields.io/badge/CasaOS-Server-4CAF50?style=for-the-badge&logo=linux&logoColor=white)](https://casaos.io/)
[![Jellyfin](https://img.shields.io/badge/Jellyfin-Media-00A4DC?style=for-the-badge&logo=jellyfin&logoColor=white)](https://jellyfin.org/)
[![Navidrome](https://img.shields.io/badge/Navidrome-Music-5C6BC0?style=for-the-badge)](https://www.navidrome.org/)
[![Pi-hole](https://img.shields.io/badge/Pi--hole-DNS-96060C?style=for-the-badge&logo=pihole&logoColor=white)](https://pi-hole.net/)

<br>

**Learn • Build • Self-Host**

</div>

---

## 📖 About

This project turns a **Raspberry Pi 4 Model B** into a personal home server for running useful self-hosted services on a local network.

The system uses **DietPi** as the lightweight operating system and **CasaOS** as the main web-based management interface.

The server is designed as both a useful home server and a practical learning environment for **Linux, networking, Docker, storage, DNS, media servers, and self-hosting**.

---

## ✨ Features

| 🏠 Feature | 📝 Description |
|---|---|
| 🛡️ **Pi-hole** | Network-wide DNS filtering and ad/tracker blocking |
| 🎬 **Jellyfin** | Personal movie and TV media server |
| 🎵 **Navidrome** | Personal music streaming server |
| 🖥️ **CasaOS** | Simple web interface for managing applications |
| 🐧 **DietPi** | Lightweight Linux operating system |
| 💽 **External Storage** | USB SSD/HDD for media and server data |
| 🌐 **Local Network** | Services accessible across the home network |
| 🐳 **Docker** | Containerized applications and services |

---

## 🏗️ System Architecture

```text
                              🌐 INTERNET
                                  │
                                  ▼
                         ┌─────────────────┐
                         │  🛜 HOME ROUTER │
                         │   DHCP / LAN    │
                         └────────┬────────┘
                                  │
                              Ethernet
                                  │
                                  ▼
                     ┌────────────────────────┐
                     │   🥧 RASPBERRY PI 4    │
                     │       MODEL B          │
                     └────────────┬───────────┘
                                  │
                                  ▼
                     ┌────────────────────────┐
                     │        🐧 DIETPI       │
                     │      Linux Server      │
                     └────────────┬───────────┘
                                  │
                                  ▼
                     ┌────────────────────────┐
                     │        🏠 CASAOS       │
                     │  Server Management UI  │
                     └────────────┬───────────┘
                                  │
              ┌───────────────────┼───────────────────┐
              │                   │                   │
              ▼                   ▼                   ▼
      ┌───────────────┐   ┌───────────────┐   ┌───────────────┐
      │  🎬 JELLYFIN  │   │ 🎵 NAVIDROME  │   │   🛡️ PI-HOLE  │
      │ Media Server  │   │ Music Server  │   │ DNS Filtering │
      └───────┬───────┘   └───────┬───────┘   └───────────────┘
              │                   │
              └─────────┬─────────┘
                        │
                        ▼
               ┌──────────────────┐
               │   💽 USB SSD/HDD │
               │                  │
               │  🎬 Movies       │
               │  📺 TV Shows     │
               │  🎵 Music        │
               │  ⚙️ Server Data  │
               └──────────────────┘
```

---

## 🧰 Hardware

| 🔧 Component | 📋 Details |
|---|---|
| 🥧 Raspberry Pi | Raspberry Pi 4 Model B |
| 💾 System Storage | microSD card |
| 💽 Main Data Storage | USB SSD/HDD |
| 🌐 Network | Ethernet |
| 🔌 Power | Raspberry Pi-compatible power supply |
| 🖥️ Display | Optional |
| ⌨️ Keyboard | Optional |

> 💡 **Tip:** A USB 3 SSD/HDD is recommended for large media libraries instead of using the microSD card for everything.

---

## 💻 Software Stack

| 🧩 Software | 🎯 Purpose |
|---|---|
| 🐧 **DietPi** | Lightweight Linux operating system |
| 🏠 **CasaOS** | Server and application management |
| 🛡️ **Pi-hole** | DNS filtering |
| 🎬 **Jellyfin** | Movies and TV streaming |
| 🎵 **Navidrome** | Music streaming |
| 🐳 **Docker** | Application containers |

---

## 💽 Storage Layout

```text
/mnt/storage/
│
└── media/
    │
    ├── 🎬 movies/
    │   ├── Movie 1/
    │   ├── Movie 2/
    │   └── Movie 3/
    │
    ├── 📺 tv/
    │   ├── Show 1/
    │   │   ├── Season 01/
    │   │   └── Season 02/
    │   │
    │   └── Show 2/
    │
    └── 🎵 music/
        ├── Artist 1/
        └── Artist 2/
```

---

# 🚀 Installation

## 1️⃣ Install DietPi

Download DietPi for Raspberry Pi:

👉 https://dietpi.com/

Flash the image to a microSD card using:

- 🥧 Raspberry Pi Imager
- 💿 balenaEtcher

Insert the card into the Raspberry Pi and connect:

- 🌐 Ethernet
- 🔌 Power
- 🖥️ Optional HDMI display
- ⌨️ Optional keyboard

Complete the initial DietPi setup.

---

## 2️⃣ 🔐 Connect Using SSH

Find the Raspberry Pi IP address:

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

> 🔒 Replace the example IP address with the actual IP address of your Raspberry Pi.

---

## 3️⃣ 🔄 Update DietPi

```bash
apt update
```

```bash
apt upgrade -y
```

Reboot:

```bash
reboot
```

---

## 4️⃣ 🌐 Configure the Network

A wired Ethernet connection is recommended.

Check network interfaces:

```bash
ip addr
```

Check the current IP:

```bash
hostname -I
```

### ⭐ Recommended: DHCP Reservation

Create a DHCP reservation in your router so the Raspberry Pi keeps the same local IP.

Example:

```text
🥧 Raspberry Pi
       │
       └── 192.168.1.100
```

This makes accessing the services easier and more reliable.

---

## 5️⃣ 🏠 Install CasaOS

Install CasaOS using its installation method:

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

> ⚠️ Check the current CasaOS documentation for supported operating systems and installation requirements before installing on a new system.

---

## 6️⃣ 💽 Connect External Storage

Connect the USB SSD/HDD.

Check available drives:

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

Create the mount directory:

```bash
mkdir -p /mnt/storage
```

Mount the drive:

```bash
mount /dev/sda1 /mnt/storage
```

Check storage:

```bash
df -h
```

Create media directories:

```bash
mkdir -p /mnt/storage/media
mkdir -p /mnt/storage/media/movies
mkdir -p /mnt/storage/media/tv
mkdir -p /mnt/storage/media/music
```

> ⚠️ **Important:** `/dev/sda1` is only an example. Always verify the correct drive using `lsblk` before mounting or formatting a drive.

---

# 🛡️ Pi-hole

## 7️⃣ Install Pi-hole

Pi-hole provides network-wide DNS filtering.

Install using the official installation method:

```bash
curl -sSL https://install.pi-hole.net | bash
```

During installation:

1. 🌐 Select the correct network interface.
2. 📍 Confirm the Raspberry Pi IP address.
3. 🌎 Select an upstream DNS provider.
4. 🖥️ Enable the web interface.
5. 🔐 Set the administrator password.

### Open Pi-hole

```text
http://<RASPBERRY_PI_IP>/admin
```

Example:

```text
http://192.168.1.100/admin
```

### 🌐 Configure Router DNS

Configure your router to use the Raspberry Pi as the DNS server.

Example:

```text
Primary DNS:
192.168.1.100
```

> ⚠️ Make sure Pi-hole works correctly before changing DNS settings for the entire network.

Check status:

```bash
pihole status
```

---

# 🎬 Jellyfin

## 8️⃣ Install Jellyfin

Open CasaOS:

```text
http://<RASPBERRY_PI_IP>
```

Open the application store and install **Jellyfin**.

Configure the media storage.

Recommended libraries:

```text
🎬 Movies
└── /media/movies

📺 TV Shows
└── /media/tv
```

### 🌐 Open Jellyfin

Default port:

```text
8096
```

Open:

```text
http://<RASPBERRY_PI_IP>:8096
```

Example:

```text
http://192.168.1.100:8096
```

Complete the Jellyfin setup wizard.

### ⚡ Raspberry Pi 4 Transcoding

The Raspberry Pi 4 can run Jellyfin, but heavy video transcoding can place significant load on the system.

Whenever possible, use:

```text
▶️ Direct Play
```

instead of requiring the Raspberry Pi to transcode the media.

---

# 🎵 Navidrome

## 9️⃣ Install Navidrome

Navidrome is used as the personal music server.

Create the music directory:

```bash
mkdir -p /mnt/storage/media/music
```

Install Navidrome through CasaOS/Docker.

Configure the music library:

```text
/mnt/storage/media/music
```

Default port:

```text
4533
```

Open:

```text
http://<RASPBERRY_PI_IP>:4533
```

Example:

```text
http://192.168.1.100:4533
```

---

## 🎧 Add Music

Example structure:

```text
🎵 music/
│
├── Artist 1/
│   └── Album 1/
│       ├── 01 - Song.mp3
│       ├── 02 - Song.mp3
│       └── 03 - Song.mp3
│
└── Artist 2/
    └── Album 1/
        └── 01 - Song.flac
```

Navidrome scans the music library and organizes the collection using available metadata.

---

# 🌐 Service Access

| 🧩 Service | 🔌 Port | 🌐 Example |
|---|---:|---|
| 🏠 CasaOS | `80` | `http://192.168.1.100` |
| 🛡️ Pi-hole | `80` | `http://192.168.1.100/admin` |
| 🎬 Jellyfin | `8096` | `http://192.168.1.100:8096` |
| 🎵 Navidrome | `4533` | `http://192.168.1.100:4533` |

> ℹ️ Ports may differ depending on your installation and configuration.

---

# 🐳 Docker

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

# 🔧 Useful Linux Commands

| 🛠️ Command | 🎯 Purpose |
|---|---|
| `htop` | 📊 CPU and RAM monitoring |
| `df -h` | 💽 Storage usage |
| `lsblk` | 💾 List disks |
| `hostname -I` | 🌐 Show IP address |
| `ip addr` | 🌐 Network interfaces |
| `ss -tulpn` | 🔌 Listening ports |
| `free -h` | 🧠 Memory usage |
| `vcgencmd measure_temp` | 🌡️ Raspberry Pi temperature |

### 🔄 Update

```bash
sudo apt update
sudo apt upgrade -y
```

### 🔁 Reboot

```bash
sudo reboot
```

### 🛑 Shutdown

```bash
sudo shutdown now
```

---

# 🔐 Security

This server is primarily designed for a trusted home network.

### ✅ Recommended

- 🔑 Use strong passwords
- 🔄 Keep DietPi updated
- 🔄 Keep CasaOS updated
- 📦 Keep applications updated
- 🔐 Use SSH keys where possible
- 💾 Keep important data backed up
- 🧱 Use a firewall where appropriate
- 🚫 Avoid unnecessary port forwarding
- 🌐 Avoid exposing administration panels directly to the internet

### 🌍 Remote Access

If remote access is required, use a secure VPN or another properly configured remote-access solution instead of directly exposing administration interfaces to the public internet.

---

# 💾 Backup

The Raspberry Pi should not be considered a backup by itself.

Important data should be copied to another storage device.

### Important data to back up

- 🎬 Movies
- 📺 TV Shows
- 🎵 Music
- 🎬 Jellyfin configuration
- 🎵 Navidrome configuration
- 🗄️ Navidrome database
- 🛡️ Pi-hole configuration
- 🏠 CasaOS application data

---

# 🧪 Testing

After installation, test each service.

| 🧪 Service | 🌐 Test Address |
|---|---|
| 🏠 CasaOS | `http://<RASPBERRY_PI_IP>` |
| 🛡️ Pi-hole | `http://<RASPBERRY_PI_IP>/admin` |
| 🎬 Jellyfin | `http://<RASPBERRY_PI_IP>:8096` |
| 🎵 Navidrome | `http://<RASPBERRY_PI_IP>:4533` |

---

# 📚 What I Learned

This project provides practical experience with:

| 📚 Area | 💡 Skills |
|---|---|
| 🐧 Linux | Server administration |
| 🌐 Networking | IP, Ethernet, DHCP |
| 🛡️ DNS | Pi-hole and DNS configuration |
| 🐳 Docker | Containers and applications |
| 💽 Storage | Mounting and organizing storage |
| 🎬 Media | Jellyfin media server |
| 🎵 Music | Navidrome music server |
| 🔐 Security | Basic server security |
| 🥧 Raspberry Pi | Hardware and Linux administration |
| 🏠 Self-Hosting | Running services locally |

---

# 🚀 Future Improvements

- [ ] 💾 Automated backups
- [ ] 📊 Uptime Kuma
- [ ] 📁 Samba file sharing
- [ ] 🏠 Home Assistant
- [ ] 🔐 WireGuard VPN
- [ ] 📊 Server monitoring dashboard
- [ ] 🌐 Network monitoring
- [ ] 🔋 UPS battery backup
- [ ] 💽 SSD boot
- [ ] 🔄 Automatic backup system
- [ ] 📦 Additional self-hosted applications

---

# 📌 Project Information

| 📋 Category | 🔎 Details |
|---|---|
| 🏠 Project Type | Home Server / Homelab |
| 🥧 Hardware | Raspberry Pi 4 Model B |
| 🐧 Operating System | DietPi |
| 🏠 Management | CasaOS |
| 🎬 Media Server | Jellyfin |
| 🎵 Music Server | Navidrome |
| 🛡️ DNS Filtering | Pi-hole |
| 🌐 Network | Ethernet |
| 💽 Storage | USB SSD/HDD |
| 🟢 Status | Active |

---

# 🔗 Official Documentation

| 🧩 Project | 🔗 Documentation |
|---|---|
| 🥧 Raspberry Pi | https://www.raspberrypi.com/ |
| 🐧 DietPi | https://dietpi.com/ |
| 🏠 CasaOS | https://casaos.io/ |
| 🛡️ Pi-hole | https://pi-hole.net/ |
| 🎬 Jellyfin | https://jellyfin.org/ |
| 🎵 Navidrome | https://www.navidrome.org/ |

---

# 👨‍💻 Author

<div align="center">

## Gavindu Kavishka (@gavindu2006)

**Technology enthusiast building and learning through practical projects.**

<br>

[![GitHub (Main)](https://img.shields.io/badge/GitHub-gavindu2006-181717?style=for-the-badge&logo=github)](https://github.com/gavindu2006)
[![GitHub (Project)](https://img.shields.io/badge/GitHub-gavindu2006-181717?style=for-the-badge&logo=github)](https://github.com/gavindu2006-projects)

<br>

[![Portfolio](https://img.shields.io/badge/Portfolio-gavindu2006.pages.dev-4285F4?style=for-the-badge&logo=googlechrome&logoColor=white)](https://gavindu2006.pages.dev)

</div>
