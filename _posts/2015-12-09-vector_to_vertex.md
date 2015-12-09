---
layout: post
title:  "AppRender and ShapeRender"
date:   2015-12-09 20:57:00
categories: jruby_art update
keywords: to_vertex, Vec3D, Vec2D, AppRender, ShapeRender
permalink: /app_render/
---
Vec2D and Vec3D classes can be efficiently rendered as both PApplet vertices, and PShape vertices using AppRender and ShapeRender utility classes. To use either renderer you should create a single instance in the processing setup see below AppRender as example:-

{% highlight ruby %}
attr_reader :renderer
...
def setup
  @renderer = AppRender.new(self)
end
...
{% endhighlight %}

Note the use of `attr_reader` so we can access the `renderer` outside of `setup`. Here is a snippet of code for a 2D sketch, where we draw a polygon outline directly using the processing vertex (nested within `begin_shape` and `end_shape(CLOSE)`). All we need to do is supply our renderer as an argument to the Vec2D `:to_vertex` instance method.

{% highlight ruby %}
...
begin_shape # Vec2D example
  no_fill
  stroke(255)
  morph.each do |v|
    v.to_vertex(renderer)
  end
end_shape(CLOSE)
...
{% endhighlight %}

If you chose not use the renderer, this is how the code would look, requires more ruby to java conversions:-

{% highlight ruby %}
...
begin_shape # Vec2D example
  no_fill
  stroke(255)
  morph.each do |v|
    vertex(v.x, v.y)
  end
end_shape(CLOSE)
...
{% endhighlight %}

For an advanced use of the ShapeRenderer see the [trefoil sketch][trefoil]

[trefoil]:https://github.com/ruby-processing/samples4ruby-processing3/blob/master/processing_app/demos/graphics/trefoil.rb