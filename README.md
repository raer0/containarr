# 🚧🚧HOLD UP!🚧🚧
This is pre 1.0 software. It might be unstable, unintuitive in some aspects, or difficult to configure. I'm still working on identifying and correcting issues. If you encounter one, please open an issue on this repo so that I may help resolve it.

# Containarr? What's that?

Containarr is a quick and conveneint way to run -arr apps + a torrent client behind a VPN. This project allows you to get up and running with these tools in minutes and is designed to be easily accessible.

### SPECIAL THANK YOU
to Quentin McGaw for their work on Gluetun. 
- https://github.com/qdm12/gluetun

# Getting started

### IMPORTANT
  - Please check GLUETUN above for information on configuring your VPN.

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
 

# What if I'm a noob and don't know **** about docker?
Don't worry! I'm working on that. Accessibility will be the next main focus on this project. I have a lot of things on my plate, however - so if you have trouble, please open an issue, or even pr. If this gains any traction (i.e. I get emails about it) I will definitely take a look at it and start working on it some more! 
In the meantime, (20th March, 2022) this project isn't 100% noob friendly - so people coming from Reddit or google, beware!


# HELP! Things have gone horribly wrong!
Open an issue! I don't have an FAQ or anything to work with in that regard because nobody has had any issues yet ;)

<!-- Containarr is a ready-to-configure, easy to deploy docker-compose file for quickly and easily getting up and running with the -arr stack (Radarr, Sonarr, Jackett, bittorrent, etc).

With minimal configuration, you can easily deploy the -arr stack behind a VPN of your choice and connect it to storage.



By default, containarr uses a named docker volume for media, one for downloads, and stores config files on the host filesystem.


You will need to configure storage locations for media and torrents, either by replacing the named volume with a host path, or by setting volume driver_opts to utilize network shares.

To get started:

1. Clone this git repository
2. Configure media and downloads volumes in ./docker-compose.yml
3. (Optional) Create entries for subdomains in your local DNS server for radarr, sonarr, etc .containarr.lan and use the alternative index.html in ./build/nginx
4. That's it. Visit http://localhost/ to get started. This app is served over port 80 by default, you can change this in the compose file. Apps are internally routed/proxied.


Note: Prowlarr and Readarr are based off nightly/development builds at this time.


Easily remove modules by commenting/removing them from the docker-compose.yml file i.e. to remove Readarr, simply delete the entire Readarr service from the yml file. 

 -->

<!-- Disclaimer: This is for people already somewhat familiar with docker looking to set up -arr apps and a torrent client behind a vpn quickly. Its designed as more of a template to be tweaked. -->

