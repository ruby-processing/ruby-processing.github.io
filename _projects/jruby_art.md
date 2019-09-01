---
layout: page
title: JRubyArt
keywords: 'propane, JRubyArt'
---

# Understanding A JRubyArt Sketch

Ruby-processing and now JRubyArt have both taken advantage of ruby language features to create a `DSL` like experience when coding processing in ruby, to the extent that

```ruby
background 0
```

is a valid sketch (ie you can write `static` sketches in ruby). Like vanilla processing we wrap this code before it is run but unlike vanilla processing we don't use a preprocessor.

What you can/should write (like a vanilla processing sketch) avoids much boilerplate.

## bare.rb

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

## class_sketch.rb

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
