# 🚧🚧HOLD UP!🚧🚧

This is pre 1.0. It might be unstable, unintuitive in some aspects, or difficult to configure. I'm still working on identifying and correcting issues. If you encounter one, please open an issue on this repo so that I may help resolve it.



# Containarr? What's that?

Containarr is a quick and conveneint way to run -arr apps + a torrent client behind a VPN. This project allows you to get up and running with these tools in minutes and is designed to be easily accessible.

### SPECIAL THANK YOU
to Quentin McGaw for their work on Gluetun.
- https://github.com/qdm12/gluetun

# Getting started

### IMPORTANT
  - Please check GLUETUN above for information on configuring your VPN.
  - Until v0.1.2, you will need to reconfigure the default volume setup. Check issue #8 (https://github.com/ray-rock/containarr/issues/8) for more info.

### Prerequisites:
  - An intermediate understanding of Docker and docker-compose and how to configure a compose file.
  - A working docker installation
  - An open vpn compatible VPN subsription


### Ok, let's go!
  1. Clone this repo or download the latest release.
  2. Inside the docker-compose.yml file, configure the directories for your media and downloads volumes.
  3. Ensure port 8080:8080 is uncommented under service: gluetun (On your first run only)
  4. CD to this folder from a terminal and use ```docker compose up``` to monitor for errors while configuring.
  6. Visit ```http://{SERVER-IP}:8080/``` and configure qbittorrent (Make sure to enable reverse proxy settings under web ui)
  8. Configure your -arr stack - http://localhost:PORT/ (ports documented in compose file comments) allows your containers to communicate.
  9. Assuming all goes well, use ```docker compose down; docker compose up -d``` to get going.


# Configuring storage
Storage configuration can be handled numerous ways. By default, we create two named volumes "media" and "downloads", but don't attach them to anything so your downloads and media libraries will be stored locally by docker. This is fine for testing, but in most cases you'll want to point this at your library. Inside the compose.yaml there are commented out lines for each named volume that can be used to configure a connection to a CIFS/SMB fileshare. you could also mount your media library to the docker volume's folder in /var/lib/docker/volumes. I personally use CIFS.

# HELP! This is incredibly confusing!
Don't worry! I'm working on that. This should be fire and forget, and I intend to make it that way so look out for features such as:
- Install script
- Automatic installation of Docker/Docker-compose
- Guided configuration process


... and more!

### some info...
This was initially a quick-n-dirty public dump of a compose app i threw together in a few hours based off some lessons learned from running my -arr stack behind a reverse proxy so I apologize for the current state of things. It was never actually designed to be used by anyone but me, and I don't really need a guided install process. However, this is a perfect opportunity to dip my feet into open source and collaborative programming so I've decided to put more work into this project.


# HELP! Things have gone horribly wrong!
Please open an issue and I'll get on it!



---



# Getting started 2.0

### IMPORTANT
- Visit ```https://github.com/qdm12/gluetun/wiki``` for information on configuring your VPN with gluetun.
- An understanding of docker, docker compose, and how to configure ```docker-compose.yml``` are helpful but hopefully not *necessary*. If you don't get docker, you should be able to use this with docker desktop. If you find info on using containarr lacking please open a discussion so I can figure out what to add to the wiki.
- This is not intended to be exposed over a public IP. Ensure that containarr is only accessible on your private network.




### Prerequisites:
- A [pihole](https://github.com/pi-hole/pi-hole/#one-step-automated-install) or similar local DNS server are highly recommended. Without one, accessing containarr will require additional configuration which I don't support directly. Its certainly possible to use containarr without a DNS server, but it would probably take more work than simply setting up a pihole and adding the containarr subdomains to your pihole dns entries.
- An openVPN compatible vpn subscription and associated credentials.
- Latest versions of ```docker``` and ```docker compose``` on the machine you'll use to host containarr.
    - For most people, I highly recommend [```docker desktop```](https://www.docker.com/products/docker-desktop/). Simply select your OS and follow the instructions provided.
    - Windows users: [enable WSL2 and the backend for docker](https://docs.docker.com/desktop/windows/wsl/).
    - Users with existing installations: if ```docker-compose``` causes issues, install as ```docker compose``` and try without the hyphen.
        - As root user or with sudo (x86_64 arch):
        ```
            mkdir -p /root/.docker/cli-plugins

            curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64 -o /root/.docker/cli-plugins/docker-compose

            chmod +x /root/.docker/cli-plugins/docker-compose

        ```

## Ok, let's go!

### Part 0: Static IP
Ensure containarr's host has a static IP, and that ports ```80, 443``` are not exposed to the public internet.

### Part 1: DNS entries

#### TL;DR
- By default, containarr requires a static IP and the following DNS/hosts file entries:
    - containarr.lan
    - deemix.containarr.lan
    - qbt.containarr.lan
    - sonarr.containarr.lan
    - radarr.containarr.lan


#### pihole


#### hosts file



### Part 2: Ths fun part

The default configuration should be suitable for most people. Advanced users may customize ```docker-compose.yml``` if they, for example, use SMB shares for storage.

1. ```git clone https://github.com/ray-rock/containarr``` or download the latest release.
2. Rename ```config/gluetun/vpn-config.env.sample``` to ```config/gluetun/vpn-config.env```
3. Configure VPN provider, login credentials, and servers in ```config/gluetun/vpn-config.env```.
    - See [gluetun wiki](https://github.com/qdm12/gluetun/wiki) for more info on configuring your vpn provider.
4.
