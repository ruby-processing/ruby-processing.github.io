---
layout: page
title: "JRubyArt"
keywords: propane, JRubyArt
---

## Understanding A JRubyArt Sketch ##

What you can/should write (like a vanilla processing sketch) avoids boilerplate
### bare.rb ###
```ruby
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
```

When you run/watch this sketch using:-
```bash
k9 -r bare.rb
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
An explicitly wrapped sketch can actually be run directly with jruby

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

[github_pages]:https://ruby-processing.github.io/JRubyArt/
