# steamcmd

A docker container for Steam based game servers via [SteamCMD](https://developer.valvesoftware.com/wiki/SteamCMD).

**Currently in development and not suitable for general use.  Feel free to play with it, but do so entirely at your own risk.**

## Overview

Whilst you could probably pull and run this image as-is, you'll likely need to customize it somewhat to add config files, volumes, or whatever.  I've tried to keep things flexible enough to do that, or to (ideally) use this as a base for more specific Steam apps.

## Environment variables

### STEAM_APP_ID

**Required unless `STEAMCMD_ARGS` is specified.**  The ID of the Steam app you wish to install, which you can search for [here](http://steamdb.info).  Has no effect if `STEAMCMD_ARGS` is specified.

### STEAM_APP_CMD

**Required always.**  The command to run the Steam app.  E.g. `/steam/app/some-ded-server --some-option`.  This must be `exec`-able in order to ensure signals propagate (and therefore the container can shut down gracefully).

### STEAM_USERNAME

**Optional.**  The Steam username to authenticate with in order to install Steam apps that require it.

### STEAM_PASSWORD

**Optional.**  The Steam password to authenticate with in order to install Steam apps that require it.

### STEAM_APP_DIR

**Optional.**  The path at which to install the Steam app.  Has no effect if `STEAMCMD_ARGS` is specified.

### STEAMCMD_URL

**Optional.**  The URL from which to fetch SteamCMD.  The default, as documented [here](https://developer.valvesoftware.com/wiki/SteamCMD#Linux) is `https://steamcdn-a.akamaihd.net/client/installer/steamcmd_linux.tar.gz`.

### STEAMCMD_DIR

**Optional.**  The path at which to install SteamCMD.  The default is `/steam/steamcmd`.

### STEAMCMD_ARGS

**Optional.**  The arguments to pass to `steamcmd`.  This will completely override `STEAM_APP_ID` and `STEAM_APP_DIR` and you will need to tell SteamCMD which app you wish to install and where you wish it to be installed, as documented [here](https://developer.valvesoftware.com/wiki/SteamCMD#Downloading_an_app).

## Disclaimer

These containers are designed to be used by Zobees to host game servers for friends and family, and therefore may not suit all use cases.  That said, we are all for flexibility and would welcome pull requests and issues.
