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
 

# HELP! This is incredibly confusing!
Don't worry! I'm working on that. This should be fire and forget, and I intend to make it that way so look out for features such as:
- Install script
- Automatic installation of Docker/Docker-compose
- Guided configuration process


... and more! 

### some info...
This was initially a quick-n-dirty public dump of a compose app i threw together in a few hours based off some lessons learned from running my -arr stack behind a reverse proxy so I apologize for the current state of things. It was never actually designed to be used by anyone but me, and I don't really need a guided install process. However, this is a perfect opportunity to dip my feet into open source and collaborative programming so I've decided to put more work into this project.


# HELP! Things have gone horribly wrong!
Open an issue! I don't have an FAQ or anything to work with in that regard because nobody has had any issues yet ;)
