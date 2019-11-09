---
layout: page
title: Installing JRuby for propane
permalink: /jruby/propane/
---

An installed version of JRuby is an absolute pre-requisite for installing propane, but you should [install java][java] first.

### Installing jruby-launcher

It is recommended that you install the jruby-launcher (for optimised performance and suppression of illegal reflective access by jruby warning).

You should set the `JAVA_HOME` environmental variable before installing gem, and use JRuby version you want to use with propane (preferably latest available).

## Debian linux

First set the `JAVA_HOME` environmental variable, you can do this by editing the `~/.profile` file:-

```bash
echo "export JAVA_HOME=/opt/jdk13 >> ~/.profile" # wherever
```
then
```bash
source ~/.profile # to use the edited ~/.profile in current shell
sudo jgem install jruby-launcher # NB: you do need sudo access here
```

## Other linux

First set the `JAVA_HOME` environmental variable, you can do this by editing the `~/.bashrc` file:-

```bash
echo "export JAVA_HOME=/opt/jdk13 >> ~/.bashrc" # wherever
```
then
```bash
source ~/.bashrc # to use the edited ~/.bashrc in current shell
sudo jgem install jruby-launcher # NB: you do need sudo access here
```

[java]:{{ site.github.url }}/java/JRubyArt_propane
