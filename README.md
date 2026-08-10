# 🏠 Raspberry Pi Home Server

<p align="center">
  <img src="https://img.shields.io/badge/Raspberry%20Pi-4%20Model%20B-C51A4A?style=for-the-badge&logo=raspberrypi&logoColor=white" alt="Raspberry Pi">
  <img src="https://img.shields.io/badge/DietPi-Linux-0F6B3A?style=for-the-badge&logo=linux&logoColor=white" alt="DietPi">
  <img src="https://img.shields.io/badge/CasaOS-Server-4CAF50?style=for-the-badge&logo=linux&logoColor=white" alt="CasaOS">
  <img src="https://img.shields.io/badge/Jellyfin-Media-00A4DC?style=for-the-badge&logo=jellyfin&logoColor=white" alt="Jellyfin">
  <img src="https://img.shields.io/badge/Navidrome-Music-5C6BC0?style=for-the-badge&logo=navidrome&logoColor=white" alt="Navidrome">
  <img src="https://img.shields.io/badge/Pi--hole-DNS-96060C?style=for-the-badge&logo=pihole&logoColor=white" alt="Pi-hole">
</p>

<p align="center">
  A lightweight self-hosted home server built with a Raspberry Pi 4 Model B.
</p>

<p align="center">
  <strong>Learn • Build • Self-Host</strong>
</p>

---

## 📖 About

This project turns a **Raspberry Pi 4 Model B** into a lightweight home server for running useful self-hosted services on a local network.

The server uses **DietPi** as the operating system and **CasaOS** as a web-based interface for managing applications.

The main services running on the server are:

- 🛡️ **Pi-hole** — Network-wide DNS filtering
- 🎬 **Jellyfin** — Personal media streaming
- 🎵 **Navidrome** — Personal music streaming

The project is also being used as a practical home lab for learning **Linux, networking, Docker, storage management, server administration, and self-hosting**.

---

## ✨ Features

### 🖥️ Self-Hosted Home Server

Run useful services locally on your own Raspberry Pi instead of depending entirely on cloud services.

### 🎬 Media Streaming

Use Jellyfin to organize and stream personal movies and TV shows across devices on the home network.

### 🎵 Music Streaming

Use Navidrome to access and stream a personal music collection from computers, phones, and other supported clients.

### 🛡️ Network-Wide DNS Filtering

Pi-hole provides DNS-based ad and tracker blocking for devices connected to the home network.

### ⚙️ Simple Management

CasaOS provides a convenient web interface for managing applications and services running on the server.

### 🐧 Lightweight Linux Server

DietPi provides a lightweight Linux environment designed to keep resource usage low on Raspberry Pi hardware.

---

# 🏗️ System Architecture

```text
                         ┌─────────────────────┐
                         │      Internet       │
                         └──────────┬──────────┘
                                    │
                                    │
                         ┌──────────▼──────────┐
                         │    Home Router      │
                         │   Network / DHCP    │
                         └──────────┬──────────┘
                                    │
                              Ethernet
                                    │
                         ┌──────────▼──────────┐
                         │   Raspberry Pi 4     │
                         │      Model B         │
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │       DietPi        │
                         │      Linux OS       │
                         └──────────┬──────────┘
                                    │
                         ┌──────────▼──────────┐
                         │       CasaOS        │
                         │  Server Management  │
                         └──────────┬──────────┘
                                    │
                ┌───────────────────┼───────────────────┐
                │                   │                   │
        ┌───────▼───────┐   ┌──────▼──────┐   ┌────────▼────────┐
        │    Jellyfin   │   │  Navidrome  │   │     Pi-hole     │
        │  Media Server │   │ Music Server│   │   DNS Filtering │
        └───────┬───────┘   └──────┬──────┘   └─────────────────┘
                │                   │
                └──────────┬────────┘
                           │
                  ┌────────▼────────┐
                  │   USB SSD/HDD   │
                  │                 │
                  │  Movies         │
                  │  TV Shows       │
                  │  Music          │
                  └─────────────────┘
🧰 Hardware
Component	Description
🥧 Raspberry Pi	Raspberry Pi 4 Model B
💾 System Storage	microSD card
💽 Media Storage	USB SSD/HDD
🌐 Network	Ethernet
🔌 Power	Raspberry Pi-compatible power supply
🖥️ Display	Optional monitor for initial setup
⌨️ Keyboard	Optional for initial setup

Recommendation: Use a USB 3 SSD/HDD for large media libraries instead of storing everything on the microSD card.

💻 Software
Software	Purpose
DietPi	Lightweight Linux operating system
CasaOS	Web-based server/application management
Pi-hole	DNS-based ad and tracker blocking
Jellyfin	Media server
Navidrome	Music server
Docker	Container management for supported applications
📁 Storage Structure

The external storage is organized like this:

/mnt/storage/
│
└── media/
    │
    ├── movies/
    │
    ├── tv/
    │
    └── music/
Movies
movies/
├── Movie 1/
│   └── Movie 1.mkv
│
├── Movie 2/
│   └── Movie 2.mp4
│
└── Movie 3/
    └── Movie 3.mkv
TV Shows
tv/
├── Show 1/
│   ├── Season 01/
│   │   ├── S01E01.mkv
│   │   └── S01E02.mkv
│   │
│   └── Season 02/
│
└── Show 2/
    └── Season 01/
Music
music/
├── Artist 1/
│   └── Album/
│       ├── 01 - Song.mp3
│       └── 02 - Song.mp3
│
└── Artist 2/
    └── Album/
        └── 01 - Song.flac
🚀 Installation
1. Install DietPi

Download the Raspberry Pi version of DietPi from:

https://dietpi.com/

Flash the DietPi image to a microSD card using a suitable imaging tool.

Recommended tools:

Raspberry Pi Imager
balenaEtcher

Insert the microSD card into the Raspberry Pi.

Connect:

Ethernet cable
Power supply
Optional HDMI display
Optional keyboard

Power on the Raspberry Pi and complete the initial DietPi setup.

2. Connect to the Raspberry Pi

After booting, find the Raspberry Pi's IP address.

You can check it with:

hostname -I

Example:

192.168.1.100

From another computer, connect using SSH:

ssh root@192.168.1.100

Replace the IP address with the actual address of your Raspberry Pi.

🔄 3. Update DietPi

Update the package lists:

apt update

Upgrade installed packages:

apt upgrade -y

Reboot:

reboot

Reconnect using SSH after the Raspberry Pi starts again.

🌐 4. Configure the Network

A wired Ethernet connection is recommended for this server.

Check the network interface:

ip addr

Check the current IP address:

hostname -I

For a server, it is important that the Raspberry Pi has a predictable IP address.

Recommended method

Create a DHCP reservation in your router.

For example:

Raspberry Pi
     │
     └── 192.168.1.100

This allows other devices and services to consistently access the server.

🏠 5. Install CasaOS

CasaOS provides a simple web interface for managing applications and services.

Install CasaOS using its installation method:

curl -fsSL https://get.casaos.io | sudo bash

After installation, open the CasaOS dashboard:

http://<RASPBERRY_PI_IP>

Example:

http://192.168.1.100

Complete the initial CasaOS configuration.

Note: This project uses DietPi with CasaOS as the chosen setup. Check the current CasaOS documentation for supported platforms and installation requirements before installing on a new system.

💽 6. Connect the External Storage

Connect the USB SSD/HDD to one of the Raspberry Pi's USB 3 ports.

Check the available drives:

lsblk

Example:

sda
└── sda1

mmcblk0
├── mmcblk0p1
└── mmcblk0p2

Identify the external storage device carefully before formatting or mounting it.

Create the Storage Directory
mkdir -p /mnt/storage

Mount the drive:

mount /dev/sda1 /mnt/storage

Check the mounted storage:

df -h

Create the media directories:

mkdir -p /mnt/storage/media
mkdir -p /mnt/storage/media/movies
mkdir -p /mnt/storage/media/tv
mkdir -p /mnt/storage/media/music

Final structure:

/mnt/storage/
└── media/
    ├── movies/
    ├── tv/
    └── music/

Important: The device name /dev/sda1 is only an example. Always check lsblk before mounting a drive.

🛡️ 7. Install Pi-hole

Pi-hole provides DNS-based network-wide ad and tracker blocking.

Install Pi-hole using its official installation method.

curl -sSL https://install.pi-hole.net | bash

During installation:

Select the correct network interface.
Confirm the Raspberry Pi's IP address.
Select an upstream DNS provider.
Enable the web interface.
Configure the administrator password.
Open Pi-hole

After installation:

http://<RASPBERRY_PI_IP>/admin

Example:

http://192.168.1.100/admin
Configure the Router

To use Pi-hole for the entire home network, configure the router's DNS settings to use the Raspberry Pi as the DNS server.

Example:

Primary DNS:

192.168.1.100

The exact procedure depends on your router.

Important: Make sure Pi-hole is working correctly before changing DNS settings for the entire network.

Check Pi-hole
pihole status
🎬 8. Install Jellyfin

Jellyfin is used as the personal media server.

Open CasaOS:

http://<RASPBERRY_PI_IP>

Open the application store and install Jellyfin.

Configure the media storage so Jellyfin can access:

/mnt/storage/media

Recommended libraries:

Movies
└── /media/movies

TV Shows
└── /media/tv
Open Jellyfin

Jellyfin normally uses port 8096.

http://<RASPBERRY_PI_IP>:8096

Example:

http://192.168.1.100:8096

Complete the Jellyfin setup wizard:

Select language.
Create administrator account.
Add media libraries.
Select the media folders.
Configure playback settings.
Finish setup.
⚠️ Raspberry Pi 4 and Transcoding

The Raspberry Pi 4 is capable of running Jellyfin, but heavy video transcoding can place significant load on the CPU.

Whenever possible, use:

Direct Play

instead of requiring the Raspberry Pi to transcode the media.

For the best experience:

Client Device
      │
      │ Compatible Media
      ▼
   Jellyfin
      │
      ▼
   Direct Play
🎵 9. Install Navidrome

Navidrome is used as the personal music server.

Create the music directory:

mkdir -p /mnt/storage/media/music

Install Navidrome using CasaOS/Docker.

Configure its music library to use:

/mnt/storage/media/music

Navidrome normally uses port 4533.

Open:

http://<RASPBERRY_PI_IP>:4533

Example:

http://192.168.1.100:4533
🎧 10. Add Music

Copy music into:

/mnt/storage/media/music

Example:

music/
├── Artist 1/
│   └── Album 1/
│       ├── 01 - Song.mp3
│       ├── 02 - Song.mp3
│       └── 03 - Song.mp3
│
└── Artist 2/
    └── Album 1/
        └── 01 - Song.flac

Navidrome will scan the music library and organize the collection using the available metadata.

🌐 Service Access

After the setup is complete, the main services can be accessed from devices on the local network.

Service	Port	Example
🏠 CasaOS	80	http://192.168.1.100
🛡️ Pi-hole	80	http://192.168.1.100/admin
🎬 Jellyfin	8096	http://192.168.1.100:8096
🎵 Navidrome	4533	http://192.168.1.100:4533

Ports can differ depending on the installation and configuration.

🐳 Docker

CasaOS uses Docker for many applications.

Check whether Docker is installed:

docker --version

List running containers:

docker ps

List all containers:

docker ps -a

View container logs:

docker logs <container_name>

Restart a container:

docker restart <container_name>

Stop a container:

docker stop <container_name>

Start a container:

docker start <container_name>
🔧 Useful Linux Commands
Check CPU and RAM usage
htop
Check storage
df -h
List disks
lsblk
Check IP address
hostname -I
Check network interfaces
ip addr
Check listening ports
ss -tulpn
Update packages
sudo apt update
sudo apt upgrade -y
Reboot
sudo reboot
Shutdown
sudo shutdown now
🔐 Security

This server is primarily designed for use on a trusted home network.

Recommended security practices:

Use strong passwords.
Keep DietPi updated.
Keep applications updated.
Keep CasaOS updated.
Avoid exposing administration panels directly to the internet.
Use SSH keys where possible.
Keep important data backed up.
Use a firewall where appropriate.
Do not expose Pi-hole administration publicly.
Avoid unnecessary port forwarding.
Remote Access

If remote access is required, use a secure VPN or another properly configured remote-access solution instead of directly exposing administration interfaces to the public internet.

💾 Backup Strategy

The Raspberry Pi itself should not be considered a backup.

Important files should be copied to another storage device.

Recommended structure:

                 Raspberry Pi
                      │
              ┌───────┴───────┐
              │               │
          Main SSD        Backup Drive
              │               │
          Media Files      Backup

Important data to consider backing up:

Movies
TV shows
Music
Jellyfin configuration
Navidrome configuration
Navidrome database
Pi-hole configuration
CasaOS application data
📊 Monitoring

Useful information to monitor:

CPU Usage
RAM Usage
Storage Usage
Temperature
Network Activity
Docker Containers
Service Availability

Useful commands:

htop
df -h
free -h
vcgencmd measure_temp
🧪 Testing the Server

After installation, test each service.

CasaOS
http://<RASPBERRY_PI_IP>
Pi-hole
http://<RASPBERRY_PI_IP>/admin
Jellyfin
http://<RASPBERRY_PI_IP>:8096
Navidrome
http://<RASPBERRY_PI_IP>:4533
📱 Client Devices

The services can be accessed from different devices connected to the home network.

                 Home Network
                      │
        ┌─────────────┼─────────────┐
        │             │             │
      Laptop        Phone         Smart TV
        │             │             │
        └─────────────┼─────────────┘
                      │
               Raspberry Pi 4
                      │
        ┌─────────────┼─────────────┐
        │             │             │
     Jellyfin     Navidrome      Pi-hole
📚 What I Learned

This project provides practical experience with:

🐧 Linux administration
🌐 Networking
🔌 Ethernet and TCP/IP
🛡️ DNS
🖥️ Server administration
🐳 Docker
📦 Container management
💽 Storage management
🎬 Media servers
🎵 Music servers
🔐 Basic server security
🥧 Raspberry Pi administration
☁️ Self-hosting
🚀 Future Improvements

Possible future additions:

 Automated backups
 Uptime Kuma
 Samba file sharing
 Home Assistant
 WireGuard VPN
 Server monitoring dashboard
 Network monitoring
 UPS battery backup
 SSD boot
 Automatic backup system
 More self-hosted applications
📸 Project Gallery

Add project photos here:

![Raspberry Pi Home Server](images/server.jpg)

![CasaOS Dashboard](images/casaos.jpg)

![Jellyfin](images/jellyfin.jpg)

![Navidrome](images/navidrome.jpg)

![Pi-hole](images/pihole.jpg)
📂 Repository Structure
Raspberry-Pi-Home-Server/
│
├── README.md
│
├── images/
│   ├── server.jpg
│   ├── casaos.jpg
│   ├── jellyfin.jpg
│   ├── navidrome.jpg
│   └── pihole.jpg
│
└── documentation/
    └── notes.md
🛠️ Project Status
<p align="center">

🟢 Active Project

</p>

The server is being developed as a personal home-lab project. Services and features may be added or changed as the project evolves.

📌 Project Information
Category	Details
Project Type	Home Server / Homelab
Hardware	Raspberry Pi 4 Model B
Operating System	DietPi
Management	CasaOS
Media Server	Jellyfin
Music Server	Navidrome
DNS Filtering	Pi-hole
Network	Ethernet
Storage	USB SSD/HDD
Status	Active
🔗 Official Documentation
🥧 Raspberry Pi
🐧 DietPi
🏠 CasaOS
🛡️ Pi-hole
🎬 Jellyfin
🎵 Navidrome
👨‍💻 Author

Gavindu Kavishka

Technology enthusiast building and learning through practical projects.

GitHub: @gavindu2006
Portfolio: gavindu2006.pages.dev
