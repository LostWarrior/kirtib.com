---
author: "Kirti Bhardwaj"
date: 2023-02-06
linktitle: Building Personal Website With Hugo And Netlify
<!-- next: /tutorials/github-pages-blog
prev: /tutorials/automated-deployments -->
title: Building Personal Website With Hugo And Netlify
weight: 10

---

## Introduction

When I decided to build my personal website, there were options abound on how to build, how to deploy etc. I came across hugo and netlify on twitter and everyone raved about how easy it was.
So, I decided to get a basic website up and running first and then go about tweaking and moving it. Found the process to be really smooth, documenting it here for future reference as well as for someone else who might want to use it.

I am using a debian based linux system so steps are based on that:

```
## Check For system architecture
uname -i

## Download Hugo
wget https://github.com/gohugoio/hugo/releases/download/v0.36/hugo_0.36_Linux-64bit.deb

## Install
sudo dpkg -i hugo*.deb

## Version Test
hugo version

## Mandatory Update
sudo apt-get update

## Install Pip and Pygments [ Optional ]
sudo apt-get install python-pip
sudo pip install Pygments

## Enable Autocomplete [ This will generate a bash file]
sudo hugo gen autocomplete
. /etc/bash_completion

## Create a new website
hugo new site example.com
cd example.com

## Run Server
hugo server

## Add theme
cd themes
git clone -b release https://github.com/mismith0227/hugo_theme_pickles
hugo server -t hugo_theme_pickles -w -D

## Copy config to main folder
cp themes/hugo_theme_pickles/exampleSite/config.toml .

## Git
git init
git add .
git commit -m "First Commit"
git push origin branch
```

And you can start editing your website.
