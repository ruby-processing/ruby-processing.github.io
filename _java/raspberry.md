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

You should avoid installing the default openjdk-11-jdk, since it probably wont perform as well, and lead to complications (lots of warning messages etc). If you still want to use openjdk11, it is recommended that you install the jruby-launcher gem.

### Installing jruby-launcher

#### May help with openjdk-8, highly recommended with openjdk11+

You should set the `JAVA_HOME` environmental variable before installing gem, and use JRuby version you want to use with PiCrate (preferably latest available).

```bash
sudo jgem install jruby-launcher
```

You will now have an optimised `jruby launcher` that also suppresses some illegal reflective access warnings by jruby (warnings re-jogl remain).
