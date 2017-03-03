---
layout: page
title: "Propane"
keywords: propane, JRubyArt
---

## Understanding A propane Sketch ##

How you might write a propane sketch, including the `shebang` makes it easier to run the sketch using `script` in the `atom` editor, but assumes you have jruby available at `/usr/bin/jruby` or more likely via symbolic link (yet another reason not to use `rvm` or `rbenv` since they futz with your environment).

### my_sketch.rb ###

```ruby
#!/usr/bin/env jruby
# frozen_string_literal: false
require 'propane'

class MyApp < App::Propane
  # load_library :my_library # propane method
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
    sketch_title 'Regular Propane Sketch' # propane method
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
require 'propane'
module Propane
  # include_package 'org.package' # JRuby method
  class MyApp < App # App is a subclass of processing.core.PApplet

    # load_library :my_library # propane method

    def settings
      size 200, 200 # size 'mode' go here

    end

    def setup
      sketch_title 'Bare Sketch' # propane method
    end

    def draw
      # draw loop
    end    
  end  
end

# NB: If you use this explicit form need to use Propane::MyApp.new to run sketch
```

See more at [propane github pages][github_pages]

[github_pages]:https://ruby-processing.github.io/propane/
[jruby_art]:{{ site.github.url }}/projects/jruby_art/
