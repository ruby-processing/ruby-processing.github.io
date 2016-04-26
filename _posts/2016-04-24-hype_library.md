---
layout: post
title:  "Using the Hype Library with JRubyArt"
date:   2016-04-24 13:49:00
categories: jruby_art update
keywords: library, java, framework, hype, processing

---
In this special one off we release we feature [example][] JRubyArt sketches using the [Hype processing framework][] by Joshua Davis. For write ups see these blog entries

1. [A Basic Sketch](http://monkstone.github.io/jruby_art/update/2016/04/18/hype.html)
   Here we are reminded that we cannot use naked web-color strings in JRubyArt (in vanilla processing these get pre-processed anyway). Further vanilla processing (and java) use signed `int` (incompabible with ruby Fixnum) which is why we use `fill(color('#242424'))` for `fill(#242424)` see
   [alternatives][color]
2. [Using Callbacks](http://monkstone.github.io/jruby_art/update/2016/04/20/hype_advanced.html)
   This sketch shows how you can use the magic of JRuby to replace anonymous callbacks with a block.
3. [A GLSL Examples](http://monkstone.github.io/jruby_art/update/2016/04/22/hype_scanlines_glsl.html)
   This sketch shows you a neat method for initialize a pallete of `web-colors`, that Joshua Davis is keen on his `web-colors`, also indtroduces the `HTimer` class (but I'm not sure that it is either required or actually gets used here)
4. [Using nested callbacks](http://monkstone.github.io/nested_callbacks)
5. [3D Orbiter](http://monkstone.github.io/jruby_art/update/2016/04/23/orbiter.html)

[example]:https://github.com/ruby-processing/samples4ruby-processing3/tree/master/external_library/java/hype
[Hype processing framework]:http://www.hypeframework.org/
[color]: {{ site.url }}/alternatives/