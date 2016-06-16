---
layout: post
title:  "Ruby alternative methods"
date:   2015-10-25 17:21:00
categories: jruby_art update
permalink: /alternatives/
---
<style>
table{
    border-collapse: collapse;
    border-spacing: 0;
    border:2px solid #0000FF;
}

th{
    border:2px solid #0000FF;
}
</style>
Here is a list of ruby alternatives to some 'processing' convenience methods; which with the exception of `color`, `map1d`, `p5map`, `degrees` and `radians` are just regular ruby methods.

|function       |processing            |JRubyArt           |
|----------     |-------------       |------               |
|camera         |`camera(args)`      |`kamera(hash_args)`  |
|color string   |`color(#cc6600)`      |`color('#cc6600')` |
|date/time      |                      |`t = Time.now`       |
|               |`day`                   |`t.day`              |
|               |`hour`                  |`t.hour`             |
|               |`minute`                |`t.minute`           |
|               |`second`                |`t.second`           |
|               |`year`                  |`t.year`             |
|               |`map(x, b0, eo, b1, e1)`|`map1d(x, (b0..e0), (b1..e1))`|
|               |`map(x, b0, eo, b1, e1)`|`p5map(x, b0, e0, b1, e1)`|
|conversion     |`degrees(theta)`        |`theta.degrees`    |
|conversion     |`radians(theta)`        |`theta.radians`    |
|conversion     |`hex(string)`           |`string.hex`       |
|conversion     |`unhex(string)`         |`string.to_i(base=16)`|
|conversion     |`binary(c)`             |`c.to_s(2)`        |
|conversion     |`unbinary(string)`      |`string.to_i(base=2)`|
|math           |`abs(x)`                |`x.abs`            |
|math           |`round(x)`              |`x.round`          |
|math           |`ceil(x)`               |`x.ceil`           |
|math           |`random(x)`             |`rand(x)`          |
|math           |`random(a, b)`          |`rand(a..b)`       |
|math power     |`pow(a, b)`             |`a**b`             |
|square         |`sq(x)`                 |`x * x`            |
|print          |`println(x)`            |`puts x`           |
|format         |`trim(string)`          |`string.strip`     |
|format         |`nf(float_value, 0, 2)` |`format('%.2f', float_value)`|
|format         |`nf(num, digit)`        |`num.to_s.rjust(digit, '0')`|
|format         |`nf(nf(num, left, right)`|`see below`     |

`num.to_s.rjust(left, '0').ljust(left + right, '0')`

For examples of using time in sketches see [learning JRubyArt blog][time], [timestamp][timestamp] and this [clock sketch][clock].

For example of `kamera` usage see my [blog][blog]. To use `selectInput` see link to `File Chooser` in page header.

[time]:https://monkstone.github.io/_posts/time
[timestamp]:https://monkstone.github.io/_posts/timestamp
[clock]:https://github.com/ruby-processing/samples4ruby-processing3/blob/master/processing_app/library/fastmath/clock.rb
[blog]:http://monkstone.github.io/_posts/kamera/