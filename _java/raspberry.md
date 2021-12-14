---
layout: page
title: Choice of JDK on Raspbian Distro
---

# Recommended Setup For PiCrate

## RaspberryPI OS Release (32 bit)

The [RaspberryPI OS][raspbian] installed OpenJDK probably just works best.

```bash
sudo apt install openjdk-11-jdk # installs latest jdk11
```

## ManjaroARM (64 bit)

The latest version of PiCrate works well with stock java install jdk17.

```bash
sudo pacman -S jre-openjdk
```

[raspbian]:https://www.raspberrypi.com/software/
