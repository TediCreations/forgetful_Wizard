+++
title = "Mount to a remote filesystem with sshfs"
author = ["Kanelis Elias"]
date = 2021-10-23
lastmod = 2021-10-23T19:43:14+03:00
tags = ["sshfs", "mount"]
draft = false
weight = 2001
+++

## Mount to remote filesystem over SSH with sshfs {#mount-to-remote-filesystem-over-ssh-with-sshfs}


### Introduction {#introduction}

In many cases it can become cumbersome to transfer files to and from a droplet. Imagine a development usage scenario where you are coding apps remotely and find yourself uploading a script repeatedly to your virtual server to test. This can become quite a hassle in a very short period of time. Luckily there is a way to mount your VPS file system to your local computer so you can make changes on the fly and treat your droplet as local storage. In this article, we will show you how to do exactly that.


#### Installing SSHFS {#installing-sshfs}

On debian based distro.

```bash
sudo apt-get install sshfs
```


#### Mounting the Remote File System {#mounting-the-remote-file-system}

Create a local directory in which to mount the remote file system.

```bash
sudo mkdir /mnt/name
```


#### Temporarily solution {#temporarily-solution}

<!--list-separator-->

-  Temporarily with password login

    ```bash
    sudo sshfs -o allow_other,default_permissions user@ip_address:/ /mnt/name
    ```

<!--list-separator-->

-  Temporarily with ssh key authentication

    ```bash
    sudo sshfs -o allow_other,default_permissions,IdentityFile=~/.ssh/id_rsa user@ip_address:/ /mnt/name
    ```

    It is important to note that this process provides only a temporary mount point to your droplet. If the virtual server or local machine is powered off or restarted, you will need to use the same process to mount it again.

<!--list-separator-->

-  Unmount

    When you no longer need the mount point you can simply unmount it with the command

    ```bash
    sudo umount /mnt/name
    sudo rmdir /mnt/name
    ```


#### Permanent solution {#permanent-solution}

We will need to edit the /etc/fstab file on the local machine to automatically mount the file system each time the system is booted.

First we need to edit the /etc/fstab file with a text editor.

```bash
sudo nano /etc/fstab
```

Add the following entry to the bottom of the file.

```text
sshfs#root@xxx.xxx.xxx.xxx:/ /mnt/droplet
```

Save the changes and reboot.

<!--list-separator-->

-  Warning

    It should be noted that permanently mounting your VPS file system locally is a potential security risk. If your local machine is compromised it allows for a direct route to your droplet. Therefore it is not recommended to setup permanent mounts on production servers.
