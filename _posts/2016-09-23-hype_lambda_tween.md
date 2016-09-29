---
layout: post
title: "Using lambda for callbacks hype Library"
date: 2016-09-23 00:50:00
categories: jruby_art update
keywords: library, hype, JRubyArt, lambda callbacks
permalink: "/lambda_callbacks"
---

Here we explore using ruby lambda syntax to implement callbacks with the hype library by Joshua Davis.  See how we can easily deal with nested callbacks in JRubyArt, much simpler than creating all those instances of `HCallback` however we do not really need these lambdas, see [previous post][], and it is probably inefficient to have them. This is just an exercise to show how we can do it we wanted to, if for examples we were prototyping a java version?
However it is not quite as straight-forward as it might seem, note the inclusion of the required but unused obj parameter for the stabby lambda, and its omission from the long form (so the timer callback expects a lambda of with an arity of zero, whereas the HTween callback expects an arity of one, _go figure_).

### tween_lambda_example.rb ###

{% highlight ruby %}
# encoding: utf-8
load_library :hype
include_package 'hype'
# namespace for imported classes
module Hype
  java_import 'hype.extended.behavior.HRandomTrigger'
  java_import 'hype.extended.behavior.HTimer'
  java_import 'hype.extended.behavior.HTween'
  java_import 'hype.extended.colorist.HColorPool'
end

attr_reader :canvas
PALETTE = %w(#FFFFFF #F7F7F7 #ECECEC #333333 #0095a8 #00616f #FF3300 #FF6600).freeze

def settings
  size(640, 640)
end

def setup
  sketch_title('Tween Example')
  H.init(self)
  H.background(color('#000000'))
  colors = Hype::HColorPool.new(web_to_color_array(PALETTE))
  H.add(@canvas = HCanvas.new).autoClear(false).fade(1)
  tween_trigger = Hype::HRandomTrigger.new(1.0 / 6)
  tween_trigger.callback do
    r = canvas.add(HRect.new(25 + (rand(0..5) * 25)).rounding(10))
              .stroke_weight(1)
              .stroke(colors.getColor)
              .fill(color('#000000'), 25)
              .loc(rand(0..width), rand(0..height))
              .anchor_at(H::CENTER)
    tween1 = Hype::HTween.new
                         .target(r).property(H::SCALE)
                         .start(0).end(1).ease(0.03).spring(0.95)
    tween2 = Hype::HTween.new
                         .target(r).property(H::ROTATION)
                         .start(-90).end(90).ease(0.01).spring(0.7)
    tween3 = Hype::HTween.new
                         .target(r).property(H::ALPHA)
                         .start(0).end(255).ease(0.1).spring(0.95)
    r.scale(0).rotation(-90).alpha(0)
    timer = Hype::HTimer.new.interval(250).unregister
    on_appear = -> (_obj) { timer.register }
    on_disappear = -> (_obj) { canvas.remove(r) }
    on_pause = lambda do
      tween3.callback(&on_appear)
      timer.unregister
      tween1.start(1).end(2).ease(0.01).spring(0.99).register
      tween2.start(90).end(-90).ease(0.01).spring(0.7).register
      tween3.start(255).end(0).ease(0.01).spring(0.95).register.callback(&on_disappear)
    end
    timer.callback(&on_pause)
  end
end

def draw
  H.draw_stage
end

{% endhighlight %}


<img src="/assets/hype_tween.png" />

[previous post]: {{ site.url }}/nested_callbacks
[jruby_art]:https://ruby-processing.github.io/index.html
[hype_library]:https://github.com/hype/HYPE_Processing
[hype_framework]:http://www.hypeframework.org/
