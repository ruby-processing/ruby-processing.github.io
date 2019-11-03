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

As of writing java does not come pre-installed with Buster, we strongly recommend that you install stock OpenJDK8 distribution.

```bash
sudo apt-get install openjdk-8-jdk
```

You should avoid installing the default openjdk-11-jdk, since it probably wont perform as well, and lead to complications (lots of warning messages etc). If you still want to use openjdk11, it is recommended that you install the [jruby-launcher][jruby] gem.

[jruby]:{{ site.github.url }}/jruby/raspberry
