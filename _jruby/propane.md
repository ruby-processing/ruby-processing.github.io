---
layout: page
title: Installing JRuby for propane
permalink: /jruby/propane/
---

An installed version of JRuby is an absolute pre-requisite for installing propane, but you should install java first.

## Installing/Updating jruby-launcher gem debian linux

First set the `JAVA_HOME` environmental variable, you can do this by editing the `~/.profile` file:-

```bash
echo "export JAVA_HOME=/opt/jdk13 >> ~/.profile" # wherever
```
then
```bash
source ~/.profile # to use the edited ~/.profile in current shell
sudo jgem install jruby-launcher # NB: you do need sudo access here
```
