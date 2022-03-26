# 🚧🚧HOLD UP!🚧🚧

This is pre 1.0. It might be unstable, unintuitive in some aspects, or difficult to configure. I'm still working on identifying and correcting issues. If you encounter one, please open an issue on this repo so that I may help resolve it.



# Containarr? What's that?

Containarr is a quick and conveneint way to run -arr apps + a torrent client behind a VPN. This project allows you to get up and running with these tools in minutes and is designed to be easily accessible.


# Getting started v0.1.2

## IMPORTANT
- Visit ```https://github.com/qdm12/gluetun/wiki``` for information on configuring your VPN with gluetun.
- An understanding of docker, docker compose, and how to configure ```docker-compose.yml``` are helpful but hopefully not *necessary*. If you don't get docker, you should be able to use this with docker desktop. If you find info on using containarr lacking please open a discussion so I can figure out what to add to the wiki.
- This is not intended to be exposed over a public IP. Ensure that containarr is only accessible on your private network.




## Prerequisites
- A [pihole](https://github.com/pi-hole/pi-hole/#one-step-automated-install) or similar local DNS server are highly recommended. Without one, accessing containarr will require additional configuration which I don't support directly. Its certainly possible to use containarr without a DNS server, but it would probably take more work than simply setting up a pihole and adding the containarr subdomains to your pihole dns entries.
- An openVPN compatible vpn subscription and associated credentials.
- Latest versions of ```docker``` and ```docker compose``` on the machine you'll use to host containarr.
    - For most people, I highly recommend [```docker desktop```](https://www.docker.com/products/docker-desktop/). Simply select your OS and follow the instructions provided.
    - Windows users: [enable WSL2 and the backend for docker](https://docs.docker.com/desktop/windows/wsl/).
    - Users with existing installations on GNU/Linux: if ```docker-compose``` causes issues, install as ```docker compose``` and try without the hyphen.
        - As root user or with sudo (x86_64 architecture):
        ```
            mkdir -p /root/.docker/cli-plugins

            curl -SL https://github.com/docker/compose/releases/latest/download/docker-compose-linux-x86_64 -o /root/.docker/cli-plugins/docker-compose

            chmod +x /root/.docker/cli-plugins/docker-compose

        ```

## Ok, let's go!

### Part 0: Static IP
Ensure containarr's host has a static IP, and that ports ```80, 443``` are not exposed to the public internet.

### Part 1: DNS entries

#### TL;DR:
- Containarr uses these dns entries by default:
    - containarr.lan
    - deemix.containarr.lan
    - qbt.containarr.lan
    - sonarr.containarr.lan
    - radarr.containarr.lan


#### Pihole:
1. Ensure your containarr host and the client accessing it are both configured to use your pihole as a DNS server.
2. Enter your pihole admin panel and make the following entries:
    - CONTAINARR_HOST_IP ➡️ containarr.lan
    - CONTAINARR_HOST_IP ➡️ qbt.containarr.lan
    - CONTAINARR_HOST_IP ➡️ deemix.containarr.lan
    - CONTAINARR_HOST_IP ➡️ radarr.containarr.lan
    - CONTAINARR_HOST_IP ➡️ sonarr.containarr.lan
    - CONTAINARR_HOST_IP ➡️ prowlarr.containarr.lan

#### Hosts file:

##### GNU/Linux | MacOS:
1. Open a terminal.
2. ```sudo nano /etc/hosts```
3. Add the following entries to your hosts file:
    - CONTAINARR_HOST_IP    containarr.lan
    - CONTAINARR_HOST_IP    qbt.containarr.lan
    - CONTAINARR_HOST_IP    deemix.containarr.lan
    - CONTAINARR_HOST_IP    radarr.containarr.lan
    - CONTAINARR_HOST_IP    sonarr.containarr.lan
    - CONTAINARR_HOST_IP    prowlarr.containarr.lan

##### Windows:
1. Open a Windows command line with admin privileges.
2. ```notepad C:\windows\system32\drivers\etc\hosts```
3. Add the following entries to your hosts file:
    - CONTAINARR_HOST_IP    containarr.lan
    - CONTAINARR_HOST_IP    qbt.containarr.lan
    - CONTAINARR_HOST_IP    deemix.containarr.lan
    - CONTAINARR_HOST_IP    radarr.containarr.lan
    - CONTAINARR_HOST_IP    sonarr.containarr.lan
    - CONTAINARR_HOST_IP    prowlarr.containarr.lan




### Part 2: The fun part

The default configuration should be suitable for most people. Advanced users may customize ```docker-compose.yml``` if they so choose - I don't care, I'm not a cop.

1. ```git clone https://github.com/ray-rock/containarr``` or download the latest release.
2. ```chown -R 2500:2500 containarr/data/```
3. Rename ```config/gluetun/vpn-config.env.sample``` to ```config/gluetun/vpn-config.env```
4. Configure a VPN provider, login credentials, and servers in ```config/gluetun/vpn-config.env```.
    - See [gluetun wiki](https://github.com/qdm12/gluetun/wiki) for more info on configuring your vpn provider.
5. Open a terminal and navigate to your containarr folder.
6. ```docker compose up```
7. Once the command prompt settles, visit ```http://containarr.lan``` in your browser.
8. If you see a menu, great! Now visit ```http://containarr.lan:8080``` and use ```usernamne: admin, password: adminadmin``` to log in to qbittorrent.
9. Go to ```qbittorrent settings ➡️ web ui ➡️ security``` and **ensure that CSRF and CLICKJACKING PROTECTION are turned OFF**
10. In your terminal window: ```Ctrl + C``` then ```docker compose down```
11. Comment out ```services: gluetun: ports: - 8080:8080``` in docker-compose.yml, you no longer need to expose it.
12. ```docker compose up -d``` and you should be good to go!

### Part 3: Now what?

#### Note:
use ```localhost``` for any configurations which ask for an IP address.

- Connect radarr/sonarr to qbittorrent
- Connect prowlarr to radarr/sonarr
- Configure your data folders on each app.


# HELP! Things have gone horribly wrong!
Please open an issue and I'll get on it!


# Credits

### gluetun
Thank you to [@qdm12](https://github.com/qdm12) for their work on [gluetun](https://github.com/qdm12/gluetun).

### linuxserver
Thank you to [linuxserver.io](https://github.com/linuxserver) for their work on the docker containers used in this project.
- [linuxserver/docker-qbittorrent](https://github.com/linuxserver/docker-qbittorrent)
- [linuxserver/docker-sonarr](https://github.com/linuxserver/docker-sonarr)
- [linuxserver/docker-radarr](https://github.com/linuxserver/docker-radarr)
- [linuxserver/docker-prowlarr](https://github.com/linuxserver/docker-prowlarr)



### Radarr Sonarr, and Prowlarr
Thank you to all who contribute to [radarr](https://github.com/Radarr/Radarr), [sonarr](https://github.com/Sonarr/Sonarr), and [prowlarr](https://github.com/Prowlarr/Prowlarr).
