---
layout: post
title:  "Ruby alternative methods"
date:   2015-10-25 17:21:00
categories: jruby_art update
permalink: /alternatives/
---

|function       |  processing          |  JRubyArt         |
|----------     |:-------------:       |------:            |
|color string   |`color(#cc6600)`      |`color('#cc6600')` |
|date/time      |                      |t = Time.now       |
|               |day                   |t.day              |
|               |hour                  |t.hour             |
|               |minute                |t.minute           |
|               |second                |t.second           |
|               |year                  |t.year             |
|               |map(x, b0, eo, b1, b1)|map1d(x, (b0..e0), (b1..e1))|
|               |map(x, b0, eo, b1, b1)|p5map(x, b0, e0, b1, e1)|
|conversion     |degrees(theta)        |theta.degrees    |
|conversion     |radians(theta)        |theta.radians    |
|conversion     |hex(string)           |string.hex       |
|conversion     |unhex(string)         |string.to_i(base=16)|
|conversion     |binary(c)             |c.to_s(2)        |
|conversion     |unbinary(string)      |string.to_i(base=2)|
|math           |abs(x)                |x.abs            |
|math           |round(x)              |x.round          |
|math           |ceil(x)               |x.ceil           |
|math           |random(x)             |rand(x)          |
|math           |random(a, b)          |rand(a..b)       |
|math power     |pow(a, b)             |a**b             |
|square         |sq(x)                 |x * x            |
|print          |println(x)            |puts x           |
|format         |trim(string)          |string.strip     |
|format         |`nf(float_value, 0, 2)` |`format('%.2f', float_value)`|
|format         |`nf(num, digit)`        |`num.to_s.rjust(digit, '0')`|
|format         |nf(nf(num, left, right)|`see below`     |

`num.to_s.rjust(left, '0').ljust(left + right, '0')`