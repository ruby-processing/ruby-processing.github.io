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

## Oracle jdk8 for Arm

Is still available for personal use, but it is a bit of hassle to install:-

1. [download]
2. Untar to say `/opt` folder

  ```bash
  cd /opt
  sudo tar xzvf ~/Downloads/*.tar.gz
  ```

3. Install and configure using `update-alternatives`

  ```bash
  sudo update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_231/jre/bin/jar 100
  sudo update-alternatives --install /usr/bin/javac javac /opt/jdk1.8.0_231/bin/javac 100
  sudo update-alternatives --install /usr/bin/jar jar /opt/jdk1.8.0_231/bin/jar 100
  ```

  configure

  ```bash
  sudo update-alternatives --config java
  sudo update-alternatives --config javac
  sudo update-alternatives --config jar
  ```

  edit `~/.profile`

  ```bash
  export JAVA_HOME=/opt/jdk1.8.0_231
  ```

  install jruby-launcher gem

  ```bash
  sudo jgem install jruby-launcher
  ```

  `Building native extensions. This could take a while... Successfully installed jruby-launcher-1.1.10-java 1 gem installed`

[jruby]:{{ site.github.url }}/jruby/raspberry

[download]: https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
