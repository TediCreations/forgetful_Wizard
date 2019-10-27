+++
title = "Install and setup wine"
author = ["Kanelis Elias"]
date = 2019-10-27
lastmod = 2019-10-27T17:28:33+02:00
tags = ["wine"]
draft = false
weight = 2001
+++

## Install windows compatibility layer {#install-windows-compatibility-layer}

```bash
sudo apt-get install wine-stable
sudo apt-get install winetricks
```


## Configure it {#configure-it}

Add fonts or windows components

```bash
winetricks
```


## Install your software {#install-your-software}

```bash
wine <program>
```