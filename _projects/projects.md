---
layout: page
title: "Ruby Processing Projects"
keywords: projects, propane, JRubyArt, toxicgem, atom-k9, language-jruby-art, pbox2d
---

### JRubyArt ###

The natural successor to ruby-processing, for processing-3.3.1 and jruby-9.1.8.0, requires vanilla processing install. Executable `k9`. Can work without jruby install (using jruby-complete.jar).  Features a --watch (-w) mode, where sketch will reload on saved changes.  Supports `bare` sketches (like vanilla processing)

### propane ###

An alternative ruby-processing implementation, for processing-3.3.1 and jruby-9.1.8.0, does not require vanilla processing install, does require jruby install. Executable `jruby`.  Should be be easier to convert into an exportable app, no reliance on vanilla processing install. Only supports class wrapped sketches.

### pbox2d ###

Gem wrapper around [jbox2d][pbox2d] for JRubyArt and propane

### toxiclibs ###

Gem wrapper around [toxiclibs libraries][toxiclibs] for JRubyArt and propane

### geomerative ###

Gem wrapper around [geomerative library][geomerative] for JRubyArt and propane

### ruby_wordcram ###

Gem wrapper around [WordCram library][wordcram] for JRubyArt and propane, create word clouds in ruby.

### joonsrenderer ###

Gem wrapper around [joonsrenderer library][joonsrenderer] for JRubyArt and propane, enables sunflow raytracing of sketches

### filters4jruby_art

A set of GLSL filters for use with JRubyArt (propane), as [example sketches][examples]

### atom-k9 ###

The [atom-k9][atom-k9] package allows you run JRubyArt sketches from atom editor

### language-jruby-art ###

The [language-jruby-art][language-jruby-art] provides syntax highlighting and snippets for JRubyArt and propane

[pbox2d]:https://github.com/ruby-processing/jbox2d
[toxiclibs]:https://github.com/ruby-processing/toxicgem
[geomerative]:https://github.com/ruby-processing/geomerativegem
[language-jruby-art]:https://github.com/ruby-processing/language-jruby-art
[atom-k9]:https://github.com/ruby-processing/atom-k9
[joonsrenderer]:https://github.com/ruby-processing/joonsrenderer
[examples]:https://github.com/ruby-processing/filters4jruby_art/blob/master/README.md
[wordcram]:http://wordcram.org/
