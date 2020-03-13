---
layout: page
title: "PiCrate"
keywords: picrate, JRubyArt
---

## Environment ##

### Java ###

Unlike vanilla processing, we do not distribute a java environment with our projects. It is the expectation that you will use the default openjdk11 suplied with Buster on the RaspberryPI3B+ or RaspberryPI4.

### JRuby ###

With picrate you need to install jruby on your system (you do not need `rvm` or `rbenv` to do this since you call the jruby binary directly).

## Understanding A picrate Sketch ##

How you might write a picrate sketch, including the `shebang` makes it easier to run the sketch using `script` in the `atom` editor, but assumes you have jruby available at `/usr/bin/jruby` or more likely via symbolic link (yet another reason not to use `rvm` or `rbenv` since they futz with your environment).

### my_sketch.rb ###

```ruby
#!/usr/bin/env jruby
# frozen_string_literal: false
require 'picrate'

class MyApp < Processing::App
  # load_library :my_library # picrate method
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
    sketch_title 'Regular PiCrate Sketch' # picrate method
  end

  def draw
    # draw loop
  end
end

MyApp.new
```

### Structure ###

You will see that under the hood the structure is like a [jruby_art][jruby_art] (and ruby-processing) wrapped bare sketch (the only real difference is there's not the option of starting a sketch with MRI ruby).

```ruby
# frozen_string_literal: false
require 'picrate'
module Processing
  # include_package 'org.package' # JRuby method
  class MyApp < App # App is a subclass of processing.core.PApplet

    # load_library :my_library # picrate method

    def settings
      size 200, 200 # size 'mode' go here

    end

    def setup
      sketch_title 'Bare Sketch' # picrate method
    end

    def draw
      # draw loop
    end    
  end  
end

# NB: If you use this explicit form need to use PiCrate::MyApp.new to run sketch
```

See more at [picrate github pages][github_pages]

[github_pages]:https://ruby-processing.github.io/PiCrate/
[jruby_art]:{{ site.github.url }}/projects/jruby_art/
