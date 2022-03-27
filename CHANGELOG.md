# ❗ Changelog ❗


## Contributors
- @Bockiii  ➡️  v0.1.1, #5
- @stevietv  ➡️  v0.2.3, #8
- @ray-rock  ➡️  project creator.


## What's new?
### v0.2.3
- Addressed [this](https://github.com/ray-rock/containarr/pull/21#pullrequestreview-922297868) review, which was missed by @ray-rock before merging pr #21.

### v0.2.2
- Added screenshot to readme

### v0.2.1
- Fixed lacking documentation.

### v0.2.0
- Implemented self-signed SSL in the reverse proxy.
- Changed to MIT license.



### v0.1.2

- ✅Fixed default storage config (#8)
- ~~Changes default vpn routing, adds documentation for whether one should include their indexer or only tunnel qbittorrent. (#9)~~
- ~~Fix an issue where other containers might start before gluetun, leaving them networkless and unable to be used. (#10)~~
- Moved vpn configuration to ```config/gluetun/vpn-config.env```
- ✅Made changes to reverse proxy to make it functional (#19)
    - Added documentation on creating DNS entries for reverse proxy
- Massive improvements to documentation/readme

<sup>*Stricken entries unfurled into larger issues.</sup>


#### To-Do
- Change exposed ports
- ✅~~Add SSL termination~~



### v0.1.1
- ✅Addressed issues brought up in issue #5
  - Removed "UMASK" environment variable
  - Added "DEEMIX_SINGLE_USER=true" environment variable to default deemix configuration.
    - reasoning by @Bockiii - "as that will make the login serverwide (so you only need to login once in one browser and can use the same user in every session)"


### v0.1.0
First release.
