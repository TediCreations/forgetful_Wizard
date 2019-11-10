+++
title = "Setup DLNA server on Raspberry Pi"
author = ["Kanelis Elias"]
date = 2019-11-10
lastmod = 2019-11-10T15:33:00+02:00
tags = ["dlna", "raspberrypi"]
draft = false
weight = 2001
+++

## Setup DLNA server on RAspberry Pi {#setup-dlna-server-on-raspberry-pi}


### Installation {#installation}

```bash
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install minidlna
```


### Mount hard drive {#mount-hard-drive}

Connect an external hard drive.

```bash
sudo nano /etc/fstab
```

Add this line. Change only the /dev of your hard drive. It is assumed that the hdd is fat32 formatted.

```text
/dev/sda1    /media/HDD   vfat    defaults     0        2
```


### Configuration {#configuration}

Open the file /etc/minidlna.conf

```bash
sudo nano /etc/minidlna.conf
```

and change this

```text
#friendly_name=
# * "A" for audio (eg. media_dir=A,/var/lib/minidlna/music)
# * "P" for pictures (eg. media_dir=P,/var/lib/minidlna/pictures)
# * "V" for video (eg. media_dir=V,/var/lib/minidlna/videos)
```

into this:

```text
friendly_name="MINIDLNA"
media_dir=A,/media/HDD/Music
media_dir=P,/media/HDD/Pictures
media_dir=V,/media/HDD/Movies
```


### Restart server {#restart-server}

```bash
sudo service minidlna restart
sudo service minidlna force-reload
```