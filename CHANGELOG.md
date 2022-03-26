# Changelog



## v0.1.2
### What's new?
1. Fixed default storage config (#8)
2. ~~ Changes default vpn routing, adds documentation for whether one should include their indexer or only tunnel qbittorrent. (#9) ~~
3. ~~ Fix an issue where other containers might start before gluetun, leaving them networkless and unable to be used. (#10)~~
4. moved vpn configuration to ```config/gluetun/vpn-config.env```
5. Made changes to reverse proxy to make it functional
    - Added documentation on creating DNS entries for reverse proxy
6. Massive improvements to documentation/readme

<sup>*Stricken entries unfurled into larger issues. (#19)</sup>


### To-Do
- Change exposed ports
- Add SSL termination



## v0.1.1
- Addressed issues brought up in issue #5
  - Removed "UMASK" environment variable
  - Added "DEEMIX_SINGLE_USER=true" environment variable to default deemix configuration.
    - reasoning by @Bockiii - "as that will make the login serverwide (so you only need to login once in one browser and can use the same user in every session)"


## v0.1.0
First release.
