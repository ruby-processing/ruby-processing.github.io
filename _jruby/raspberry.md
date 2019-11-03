---
layout: page
title: Installing/Updating JRuby on Raspbian Distro
permalink: /jruby/raspberry
---

# Recommended Setup For PiCrate

## Download

Download the latest JRuby release [here][download]. You could use `wget` (substituting latest version for for `9.2.9.0`):-

`wget https://repo1.maven.org/maven2/org/jruby/jruby-dist/9.2.9.0/jruby-dist-9.2.9.0-bin.tar.gz`

## Install

```bash
cd /opt
sudo tar xzvf ~/jruby-dist-9.2.9.0-bin.tar.gz # or ~/Downloads/...
sudo update-alternatives --install /usr/bin/jruby jruby /opt/jruby-9.2.9.0/bin/jruby 100
sudo update-alternatives --install /usr/bin/jgem jgem /opt/jruby-9.2.9.0/bin/jgem 100
sudo update-alternatives --install /usr/bin/jirb jirb /opt/jruby-9.2.9.0/bin/jirb 100
```

## Update

```bash
sudo update-alternatives --config jruby
sudo update-alternatives --config jgem
sudo update-alternatives --config jirb
```

## Set a local gem environment

It is preferable to store gems in your local environment, if you have not installed ruby before we recommend you do the following:-

1. Create local folders

  ```bash
  mkdir -p ~/.gem/ruby/2.5.0
  ```

2. Set gem home/path in ~/.profile

  ```bash
  echo "export GEM_HOME=\"\$HOME/.gem/ruby/2.5.0\"" >> ~/.profile
  echo "export GEM_PATH=\"\$HOME/.gem/ruby/2.5.0\"" >> ~/.profile
  ```

  This will set were gems get installed (unless you use rvm, which would be stupid to use on raspberrypi).

## Add the ${GEM_PATH}/bin to PATH

```bash
echo "export PATH=\"\${PATH}:\${GEM_PATH}/bin\"" >> ~/.profile
```

You need to do this to use gem executables.

## Installing/Updating jruby-launcher gem

First set the `JAVA_HOME` environmental variable, you can do this by editing the `~/.profile` file:-

```bash
source ~/.profile # to use the edited ~/.profile in current shell
echo "export JAVA_HOME=/usr/lib/jvm/java-8-openjdk >> ~/.profile"
```

Above assumes you are using `java-8-openjdk` on Buster, adjust for your setup. We do not currently recommend using `java-11-openjdk`, but if you are there is even more reason to install the `jruby-launcher` gem as it suppresses illegal-reflective access warning from `JRuby` (but not from the jogl jars)

[download]: https://www.jruby.org/download
