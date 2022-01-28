Containarr is a ready-to-configure, easy to deploy docker-compose file for quickly and easily getting up and running with the -arr stack (Radarr, Sonarr, Jackett, bittorrent, etc).

With minimal configuration, you can easily deploy the -arr stack behind a VPN of your choice and connect it to storage.



By default, containarr uses a named docker volume for media, one for downloads, and stores config files on the host filesystem.


You will need to configure storage locations for media and torrents, either by replacing the named volume with a host path, or by setting volume driver_opts to utilize network shares.

To get started:

1. Clone this git repository
2. Configure media and downloads volumes in ./docker-compose.yml
3. (Optional) Create entries for subdomains in your local DNS server for radarr, sonarr, etc .containarr.lan and use the alternative index.html in ./build/nginx
4. Do stuff



Disclaimer: This is for people already somewhat familiar with docker looking to set up -arr apps and a torrent client behind a vpn quickly. Its designed as more of a template to be tweaked.


Tentative plans: trim fat and merge images?
