---
layout: page
title: JRubyArt and propane
---

# Recommended Setup For JRubyArt and propane

Prior to jdk9 there were no specific recommendations, linux user probably used vanilla OpenJDK8 that was installed by there distribution, and Mac and Windows users probably installed Oracle jdk8\. The ruby-processing project wants to move forward, and it is a requirement that you install at least jdk11\. Oracle jdk is no longer an option for regular users, but unfortunately neither is a stock linux distribution of OpenJDK11+.

## Stock OpenJDK on linux

Require at least OpenJDK-11, prefer OpenJDK-17

## OpenJDK (Recommended version 17+)

The development version of vanilla processing is using this version and I think it is a good choice, however to confuse matters it comes in several flavours. Vanilla processing is using the variant with a `hotspot` jvm, which is a good starting point. The ruby-processing group will be pleased to hear about anyone experimenting with the `OpenJ9` jvm.

### Debian and RPM linux release matrix

[Matrix](https://github.com/AdoptOpenJDK/openjdk-installer/blob/master/linux/README.md#support-matrix)

### Brew Install MacOS

[Brew](https://github.com/AdoptOpenJDK/homebrew-openjdk)

### Windows

[Windows 64](https://adoptopenjdk.net/installation.html#x64_win-jdk)

### OpenJ9 jdk17+

Is a possible alternative.

Use the latest versions of PiCrate, propane and JRubyArt to avoid reflective access warnings (you may need to define JAVA_HOME to get rid off the JRuby warnings).
