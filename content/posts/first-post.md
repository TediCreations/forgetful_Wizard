+++
title = "First post"
author = ["Kanelis Elias"]
date = 2019-10-22
lastmod = 2019-10-27T16:01:50+02:00
tags = ["hugo"]
categories = ["spell"]
draft = false
weight = 2001
foo = "bar"
baz = "zoo"
alpha = 1
beta = "two words"
gamma = 10
[menu.main]
  identifier = "first-post"
  weight = 2001
+++

## Why? {#why}

There are many spells and this spellbook is responsible for remembering them for me. This makes magic fun and my brain happy.


## When? {#when}

When I learn a new spell...


## How? {#how}

This spellbook is build with Hugo.

```sh
hugo new site "Forgetful_Wizard"
cd "Forgetful_Wizard"
git init
git submodule add https://github.com/vaga/hugo-theme-m10c.git themes/m10c
echo 'theme = "m10c"' >> config.toml
```


## Who? {#who}

You and me!