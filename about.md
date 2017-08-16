---
layout: page
title: About
permalink: /about/
---
### The group ###
The ruby-processing group exists to collect together projects that support creating and running processing sketches in ruby. It is also designed to hide the inevitably high [bus factor][bus] of what is an essentially __one man band__, but I am trying hard to make it otherwise (including evolving the code). You could play your part...

There are two main projects [JRubyArt][jruby_art] and [propane][propane], the most evolved and tested of these is [JRubyArt][jruby_art], which is essentially an improved version of ruby-processing, that provides a ruby wrapper around the latest [vanilla processing][processing], it also depends on a vanilla processing install (but can be configured to not require a jruby install). [Propane][propane] is a configuration free, complete version of ruby-processing (_does not require installed vanilla processing_) that depends on an installed jruby (_is slightly more experimental_).

Other projects include the pbox2d gem (a gem wrapper around [jbox2d][jbox2d]), toxiclibs gem (a gem wrapper around [toxiclibs][toxiclibs]) and geomerative gem (a gem wrapper around [geomerative][geomerative]).

Not forgetting the atom editor projects [atom-k9][atom-k9] and [language-jruby-art][language]

#### Martin Prout ####

 First degree was BSc hons Biochemistry from University of Surrey, I went on to specialize in xenobiotic metabolism (at first drugs, then industrial chemicals and pesticides).  I later studied for a computer science degree with the Open University (BSc hons 2:1 but completed insufficient specific modules to be a named degree), course included some smalltalk but mainly java. Subsequently I dabbled a bit with C++, perl python, and even lisp, but got hooked on ruby, particulary ruby-processing. OS experience Windows-98 up to Windows-XP and mainly linux since 2004 (tried gentoo, fedora, even pardus) now using exclusively Archlinux and Mint (Debian). Since November 2012 I have been sole developer/maintainer of [ruby-processing][ruby-processing] (_did update for processing-2.0_), and I have since developed JRubyArt and propane (_for processing-3.0+_) and ensured that jruby-9.0.0.0 (with support from jruby group) continued to work with ruby-processing, and its descendants.

 NB: I'm not in the market for a job, and only get involved with projects that interest me, currently I'm learning javascript just to develop atom packages for JRubyArt / propane (but my heart is not in it, javascript is just horrible).

[jruby_art]: https://ruby-processing.github.io/JRubyArt/
[blog]:http://monkstone.github.io/
[toxiclibs]:http://ruby-processing.github.io/toxicgem/
[geomerative]:http://ruby-processing.github.io/geomerativegem/
[jbox2d]:https://github.com/ruby-processing/jbox2d
[propane]:https://ruby-processing.github.io/propane/
[processing]:https://processing.org/
[atom-k9]:https://atom.io/packages/atom-k9
[language]:https://atom.io/packages/language-jruby-art
[ruby-processing]:https://github.com/jashkenas/ruby-processing
[bus]:https://en.wikipedia.org/wiki/Bus_factor
