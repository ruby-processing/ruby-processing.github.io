---
layout: page
title: JRubyArt
keywords: 'propane, JRubyArt'
---

## Environment

### Java

Unlike vanilla processing, we do not distribute a java environment with our projects. It is quite possible that Oracle jdk8 will work best with JRubyArt 1.7.0 and below, and Oracle jdk12 will work best with JRubyArt-2.2.0+ but they have not been tested. It seem that not all OpenJDK distributions are equal, if you are lucky the one installed on your system will work for you (jdk8 for JRubyArt-1.7.0 and jdk11+ for JRubyArt-2.2.0). If you have linker problems with opengl sketches we strongly recommend you use [AdoptOpenJDK][adopt] binaries.

### JRuby

With JRubyArt, there is the possibility of installing jruby-complete (using k9 --install), rather than install jruby on your system, you will need a vanilla ruby install and to configure `~/.jruby_art/config.yml` to run sketches. Otherwise install jruby (you do not need rvm or rbenv to this as jruby binary gets called directly).


## Understanding A JRubyArt Sketch

JRubyArt has taken advantage of ruby language features to create a `DSL` like experience when coding processing in ruby, to the extent that

```ruby
background 0
```

is a valid sketch (ie you can write `static` sketches in ruby). Like vanilla processing we wrap this code before it is run but unlike vanilla processing we don't use a preprocessor.

What you can/should write (like a vanilla processing sketch) avoids much boilerplate.

### bare.rb

```ruby
# load_library :my_library # jruby_art method
# include_package 'org.package' # JRuby method
def settings
  size 200, 200 # size 'mode' or fullscreen 'mode' goes here
  # pixel_density(2) # only for HiDpi screens
  # see https://processing.org/reference/pixelDensity_.html
  # smooth # useless unless you enter a figure 2, 3, 4 or 8
  # for default renderer default is 3 for P2D and P3D it is 2
  # see https://processing.org/reference/smooth_.html
end

def setup
  sketch_title 'Bare Sketch' # jruby_art method
end

def draw
  # draw loop
end
```

When you run/watch this sketch using:-

```bash
k9 -r bare.rb # run
# or
k9 -w bare.rb # watch
```

It gets wrapped for you see below:-

```ruby
# frozen_string_literal: false
require 'jruby_art'
module Processing
  class Sketch < App # App is a subclass of processing.core.PApplet

    # begin bare sketch ###########################################
    # load_library :my_library # jruby_art method
    # include_package 'org.package' # JRuby method
    def settings
      size 200, 200 # since processing-3.0 size 'mode' go here
    end

    def setup
      sketch_title 'Bare Sketch' # jruby_art method
    end

    def draw
      # draw loop
    end    
    # end bare sketch ###########################################
  end
  Sketch.new
end
```

### class_sketch.rb

An explicitly class wrapped sketch can actually be run directly with `jruby`, but you should prefer [propane][propane] for that. Another reason to favour [propane][propane] is if the `glsl` sketch worked before processing-3.3.7 and hasn't worked since (PGraphicsOpenGL.java and PShapeOpenGL.java were reverted to earlier versions of in propane).

```ruby
# frozen_string_literal: false
require 'jruby_art'

class MySketch < Processing::App
  # load_library :my_library # jruby_art method
  # include_package 'org.package' # JRuby method
  def settings
    size 200, 200 # since processing-3.0 size 'mode' go here
  end

  def setup
    sketch_title 'Explicit JRubyArt Sketch' # jruby_art method
  end

  def draw
    # draw loop
  end
end

MySketch.new
```

See more at [JRubyArt github pages][github_pages]

[propane]:{{ site.github.url }}/projects/propane/

[github_pages]: https://ruby-processing.github.io/JRubyArt/

[adopt]: https://adoptopenjdk.net/
