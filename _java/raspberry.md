---
layout: page
title: Choice of JDK on Raspbian Distro
---

# Recommended Setup For PiCrate

## Raspbian Stretch Release

The installed Oracle JDK8 probably works best, you can use the stock OpenJDK8 from Debian distribution.

```bash
sudo apt-get install openjdk-8-jdk
```

## Raspbian Buster Release

The latest version of PiCrate works well with stock java install (jdk11) on Raspbian Buster.


You will need to define JAVA_HOME for jdk11+ to avoid reflective access warnings with JRuby.
