---
layout: page
title: "Vec2D"
permalink: /classes/vec2d/
---

The Vec2D class is a direct replacement for processings PVector class (when used for 2D work, see Vec3D for 3D version).

### Methods:-
{% highlight ruby %}
a * b # where a is instance of Vec2D and b is a scalar
a + b # where both a and b are both instances of Vec2D
a - b # where both a and b are both instances of Vec2D
a / b # where a is instance of Vec2D and b is a scalar
a == b # where both a and b are both instances of Vec2D
a.angle_between(b) # where both a and b are both instances of Vec2D
a.copy # where a is instance of Vec2D returns a deep copy
a.cross(b) # where both a and b are both instances of Vec2D
a.dist(b) # where both a and b are both instances of Vec2D
a.dot(b) # where both a and b are both instances of Vec2D
a.heading # where a is instance of Vec2D
a.lerp(b) # where both a and b are both instances of Vec2D
a.lerp!(b) # where both a and b are both instances of Vec2D
a.mag # where a is instance of Vec2D
a.normalize # where a is instance of Vec2D
a.normalize! # where a is instance of Vec2D
a.normalize!(b) # where both a and b are both instances of Vec2D
a.rotate(b) # where both a is an instance of Vec2D and b is scalar radians
a.rotate!(b) # where both a is an instance of Vec2D and b is scalar radians
a.set_mag(b) # where both a is instance of Vec2D and b is scalar
a.set_mag(b) &block # a conditional variantwhere &block evaluates to a boolean
a.to_a # returns an array [x, y] where a is instance of Vec2D
a.to_s # returns a string where a is instance of Vec2D
a.to_vertex(b) # where b is a instance of Render sends vector a to PApplet.vertex
a.x returns x as a float # where a is instance of Vec2D
a.x=b # sets the x value of Vec2D a to the float b
a.y # returns y as a float # where a is instance of Vec2D
a.y=b # sets the y value of Vec2D a to the float b
{% endhighlight %}
### Constructors:-
{% highlight ruby %}
Vec2D.from_angle(a) # returns a new Vec2D object # where a is a float radians
Vec2D.new(a, b) # where a and b are both floats 
{% endhighlight %}

Example Usages: [Examples][Vec2D]

[Vec2D]: https://github.com/ruby-processing/JRubyArt-examples/blob/master/processing_app/library/vecmath/vec2d/