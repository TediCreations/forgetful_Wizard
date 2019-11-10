+++
title = "Fresh Raspbian Installation"
author = ["Kanelis Elias"]
date = 2019-11-10
lastmod = 2019-11-10T14:13:07+02:00
tags = ["raspberrypi", "raspbian"]
draft = false
weight = 2001
+++

## Fresh Raspbian Image {#fresh-raspbian-image}


### Burn the image in an SD Card {#burn-the-image-in-an-sd-card}

You can use my script: <https://raw.githubusercontent.com/TediCreations/.dotfiles/master/files/bin/utils/writeSDCard>

```bash
writeSDCard ~/rasbian.img
```


### Enable headless ssh {#enable-headless-ssh}

1.  Add a file named "ssh" inside the /boot directory.
2.  Add a file named "wpa\_supplicant.conf" inside the /boot directory with the following contents.

<!--listend-->

```text
ctrl_interface=DIR=/var/run/wpa_supplicant GROUP=netdev
update_config=1
country=us

network={
        ssid="<Name of your WiFi>"
        psk="<Password for your WiFi>"
        scan_ssid=1
}
```


### Make it secure {#make-it-secure}

Change the default password of user pi

```bash
passwd
```


### Make a new user and lock pi user {#make-a-new-user-and-lock-pi-user}

```bash
sudo adduser tedi
sudo usermod -a -G adm,dialout,cdrom,sudo,audio,video,plugdev,games,users,input,netdev,gpio,i2c,spi tedi
sudo su - tedi
sudo pkill -u pi
sudo passwd --lock pi
```

pi user is locked and not deleted because Raspbian seems to have a lot of service dependencies on it.
Beware that logins to pi using password is not possible anymore, but possible via ssh with a key.