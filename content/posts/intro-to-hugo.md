+++
title = "Intro to Hugo"
author = ["Kanelis Elias"]
date = 2019-10-27
lastmod = 2019-10-27T16:56:18+02:00
tags = ["hugo"]
draft = false
weight = 2001
+++

## Create a new site {#create-a-new-site}

Create a new site with the name "quickstart".

```bash
hugo new site quickstart
cd quickstart
git init
```


## Add an new theme {#add-an-new-theme}

I added the theme.

```bash
git submodule add https://github.com/vaga/hugo-theme-m10c.git themes/m10c
echo 'theme = "m10c"' >> config.toml
```


## Add a post {#add-a-post}

```bash
hugo new posts/my-first-post.md
```