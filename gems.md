---
layout: page
title:  "Gems"
---
#### About gems ####
RubyGems is a package manager for the Ruby programming language that provides a standard format for distributing Ruby programs and libraries (in a self-contained format called a "gem"), a tool designed to easily manage the installation of gems, and a server for distributing them. In the main you can use most of these gems in ruby-processing projects, though some built with native extensions may not be usable with jruby, there are usually good and sometimes better java alternatives (including [gems built for jruby][jgem]). But there's more there are [gems][gems] that have been build exclusively for use with jruby-projects, that make it even easier to use processing libraries in JRubyArt and propane. There are gems to help with maven builds, publish web-pages (_jekyll and its github flavors_) that are used to bring you this content etc.

#### Building a gem for use with JRubyArt / Propane ####
The [arcball.gem][arcball] for propane, is a reasonable template for producing your own standalone processing library, that can be installed as a gem. You may also found my [guide to creating jruby-extensions][extensions] useful if you wish to stick to the 'jruby-extension convention' (my extensions and those created by jruby guys are sublety different we use `implements Library`, whereas proposed convention is to use `implements BasicLibraryService`). You could also look at other [gems built for jruby][jgem], which include more advanced features, there is no requirement to stick to convention, since both forms are likely to continue to be supported.

[extensions]:https://github.com/jruby/jruby-examples
[arcball]:https://github.com/ruby-processing/ArcBall
[jgem]:https://github.com/jruby/jruby/wiki/C-Extension-Alternatives
[gems]:http://ruby-processing.github.io/JRubyArt/gems/
