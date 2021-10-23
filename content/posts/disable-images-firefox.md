+++
title = "Disable images at Firefox"
author = ["Kanelis Elias"]
date = 2019-10-27
lastmod = 2019-12-01T21:43:09+02:00
tags = ["firefox"]
draft = false
weight = 2001
+++

## Disable image rendering in Firefox {#disable-image-rendering-in-firefox}

Sometime ago I did not have an ADSL internet connection at home. I managed to make my smartphone a hotspot and accessing its internet connection via my laptop.
Disabling the image rendering proved to save some change. You only need to adjust the settings via about:config.

1.  Open Firefox
2.  Type **about: config** in the address bar.
3.  Search for **permissions.default.image** and adjust the value to **2**. The default value is **1** by default.

    | Value | Description                             |
    |-------|-----------------------------------------|
    | 1     | Allow all images to load                |
    | 2     | Block all images from loading           |
    | 3     | Prevent third-party images from loading |
    |       |                                         |