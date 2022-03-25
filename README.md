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


