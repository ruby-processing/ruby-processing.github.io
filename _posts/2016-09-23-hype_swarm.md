---
layout: post
title: "Using HLocatable and HSwarm from the hype Library"
date: 2016-09-23 11:40:00
categories: jruby_art update
keywords: library, hype, JRubyArt, java8, proc
permalink: "/hype_swarm"
---

Here is an example sketch by Joshua Davis, from the [hype framework][hype_framework] that has been changed to make use of ruby syntax.
The declared aim of the [hype][hype_library] library is to provide:-
__A collection of classes that performs the heavy lifting so that you can create sketches with the minimum amount of code__. When using the [hype][hype_library] library to create [JRubyArt][jruby_art] sketches it is suggested that you not simply ape the [hype framework][hype_framework] examples, but tailor your sketches to take advantage of the ruby language to create even more elegant code (Code as Art), not that it is relevant here.

Unzip the library in the processing libraries folder, rename the folder `hype`, rename `distribution` folder to `library`, rename the `HYPE.jar` to `hype.jar`. Check that you can see the library from the processing-3.2.1 ide. Note that we can use snake case in place of camel case, for constants use `::` and not `.` to call. The important thing to learn from this sketch is how to implement the `HCallback` interface. This can be implemented as a closure (block), note we do not/should not try and use the vanilla processing method.

In this case we use the `web_to_color_array` convenience method (since JRubyArt-1.0.7) to convert the web string array to color int in the `HColorPool` constructor.  Note that we create the `on_anim` callback as a proc (if we had used lambda we would need a dummy `_obj` argument to implement the callback interface, because we are using `obj` from the original callback). I'm not entirely sure we are getting same behaviour with the targets as the original (need investigation).

### hype_swarm.rb ###

{% highlight ruby %}
# encoding: utf-8
load_library :hype
include_package 'hype'
# Access through Hype namespace
module Hype
  java_import 'hype.extended.behavior.HSwarm'
  java_import 'hype.extended.behavior.HTimer'
  java_import 'hype.extended.behavior.HTween'
  java_import 'hype.extended.colorist.HColorPool'
  java_import 'hype.interfaces.HLocatable'
end

PALETTE = %w(#FFFFFF #F7F7F7 #ECECEC #333333 #0095a8 #00616f #FF3300 #FF6600).freeze
PALETTE2 = %w(#242424 #111111 #ECECEC).freeze
include Hype

attr_reader :swarm, :canvas, :colors, :pool, :tween, :count

def settings
  size(640, 640)
end

def setup
  sketch_title 'Hype Swarm'
  H.init(self)
  @count = 0
  @colors = HColorPool.new(web_to_color_array(PALETTE))
  colors2 = web_to_color_array(PALETTE2)
  H.background(colors2[0])
  H.add(@canvas = HCanvas.new.auto_clear(false).fade(40))
  @swarm = HSwarm.new
                 .speed(4)
                 .turn_ease(0.1)
                 .twitch(15)
                 .idle_goal(width / 2, height / 2)
  @pool = HDrawablePool.new(10)
  pool.auto_add_to_stage
      .add(HRect.new(10).rounding(5))
      .on_create do |obj|
    obj.stroke_weight(2)
       .stroke(colors2[1])
       .fill(colors2[2])
       .loc(rand(100..540), rand(100..540))
       .anchor_at(H::CENTER)
       .rotation(45)
    @tween = HTween.new
                   .target(obj).property(H::LOCATION)
                   .start(obj.x, obj.y)
                   .end(rand(0..width), rand(0..height))
                   .ease(0.01)
                   .spring(0.9)
    on_anim = proc do
      tween.start(obj.x, obj.y)
           .end(rand(100..540), rand(100..540))
           .ease(0.01)
           .spring(0.9)
           .register
    end
    HTimer.new.interval(2_000).callback(&on_anim)
  end
      .request_all
end

def draw
  if count < 100
    swarm.add_target(
      canvas.add(
        HRect.new(8, 2)
             .rounding(4)
             .anchor_at(H::CENTER)
             .no_stroke
             .fill(colors.get_color)
      )
    )
    @count += 1
  end
  H.draw_stage
  it = swarm.goals.iterator
  while it.has_next
    it.remove
    it.next
  end

  pool.each do |d|
    swarm.add_goal(d.x, d.y)
  end
end


{% endhighlight %}


<img src="/assets/swarm.png" />

[jruby_art]:https://ruby-processing.github.io/index.html
[hype_library]:https://github.com/hype/HYPE_Processing
[hype_framework]:http://www.hypeframework.org/
