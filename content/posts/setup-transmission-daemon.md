+++
title = "Setup transmission daemon on Raspberry Pi"
author = ["Kanelis Elias"]
date = 2019-10-27
lastmod = 2019-12-04T00:00:42+02:00
tags = ["raspberrypi", "transmission"]
categories = ["Home Server"]
draft = false
weight = 2001
+++

## Intro {#intro}

Hardware used: Raspberry Pi 3B+
[Source](https://pimylifeup.com/raspberry-pi-transmission/)


## Setup {#setup}

Update

```bash
sudo apt update
sudo apt upgrade
```

Install transmission

```bash
sudo apt install transmission-daemon
```

We need to stop the daemon because it is automatically started.

```bash
sudo systemctl stop transmission-daemon
```

Create torrent directories

```bash
sudo mkdir -p /media/HDD/torrent-inprogress
sudo mkdir -p /media/HDD/torrent-complete
```

Give user pi access over these directories
**SOS! This had no effect**

```bash
sudo chown -R pi:pi /media/HDD/torrent-inprogress
sudo chown -R pi:pi /media/HDD/torrent-complete
```


## Configure transmission {#configure-transmission}

Edit configuration file

```bash
sudo nano /etc/transmission-daemon/settings.json
```

Modify these configurations options with below changes

```text
"incomplete-dir": "/media/HDD/torrent-inprogress",
"download-dir":   "/media/HDD/torrent_complete",
"incomplete-dir-enabled": true,
"rpc-password":  "Your_Password",
"rpc-username":  "Your_Username",
"rpc-whitelist": "192.168.*.*",
```


## User permissions {#user-permissions}

Old way is to add user pi into the debian-transmission group

```bash
sudo usermod -a -G debian-transmission pi
```

Newer way is to add user debian-transmission into the pi group

```bash
sudo usermod -a -G pi debian-transmission
```


## Restart {#restart}

Now we need to tell the service manager to reload all service configuration files by running the following command. Otherwise, systemctl will try to use the older version of the service file.

```bash
sudo systemctl daemon-reload
```

Start back up the Transmission daemon service

```bash
sudo systemctl start transmission-daemon
```