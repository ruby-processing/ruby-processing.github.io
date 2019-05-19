---
layout: page
title: About
permalink: /about/
---

# The group

The ruby-processing group exists to collect together projects that support creating and running processing sketches in ruby. It is also designed to hide the inevitably high [bus factor][bus] of what is an essentially **one man band**, but I am trying hard to make it otherwise (including evolving the code). You could play your part...

There are three main projects [JRubyArt][jruby_art], [PiCrate] and [propane], [JRubyArt][jruby_art] is the closest to the original ruby-processing and provides a ruby implementation that approximates to the latest [vanilla processing][processing] (but can be configured to not require a jruby install).

[Propane] is a configuration free, complete version of ruby-processing (_does not require installed vanilla processing_) that depends on an installed jruby (_is slightly more experimental however since a modified PApplet is required with jdk9+ propane may take over in future_). Since propane-3.2.0, propane is compiled with jdk11, and thus jdk11 is a requirement.

[PiCrate] is a standalone version designed for the [RaspberryPI][rpi], but can be developed and run 64 bit linux.

Other projects include the pbox2d gem (a gem wrapper around [jbox2d]), toxiclibs gem (a gem wrapper around [toxiclibs]) and geomerative gem (a gem wrapper around [geomerative]).

Not forgetting the atom editor projects [atom-k9] and [language-jruby-art][language]

## Martin Prout

First degree was BSc hons Biochemistry from University of Surrey, I went on to specialize in xenobiotic metabolism (at first drugs, then industrial chemicals and pesticides). I later studied for a computer science degree with the Open University (BSc hons 2:1 but completed insufficient specific modules to be a named degree), course included some smalltalk but mainly java. Subsequently I dabbled a bit with C++, perl python, and even lisp, but got hooked on ruby, particulary ruby-processing. OS experience Windows-98 up to Windows-XP and mainly linux since 2004 (tried gentoo, fedora, even pardus) now using exclusively Archlinux and Mint (Debian). Since November 2012 I have been sole developer/maintainer of [ruby-processing] (_did update for processing-2.0_), and I have since developed JRubyArt and propane (_for processing-3.0+_) and ensured that jruby-9.2.0.0+ (with support from jruby group) continues to work with ruby-processing, and its descendants.

Personally I can't understand why processing group spawned p5*js (javascript is just horrible), but I learned sufficient to develop atom packages [atom-k9] and [language-jruby-art][language] for JRubyArt / propane.

[atom-k9]: https://atom.io/packages/atom-k9
[blog]: http://monkstone.github.io/
[bus]: https://en.wikipedia.org/wiki/Bus_factor
[geomerative]: http://ruby-processing.github.io/geomerativegem/
[jbox2d]: https://github.com/ruby-processing/jbox2d
[jruby_art]: https://ruby-processing.github.io/JRubyArt/
[language]: https://atom.io/packages/language-jruby-art
[picrate]: https://ruby-processing.github.io/PiCrate/
[processing]: https://processing.org/
[propane]: https://ruby-processing.github.io/propane/
[rpi]: https://www.raspberrypi.org/
[ruby-processing]: https://github.com/jashkenas/ruby-processing
[toxiclibs]: http://ruby-processing.github.io/toxicgem/
