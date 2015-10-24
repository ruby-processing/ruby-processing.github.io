---
layout: post
title:  "Comparison with ruby-processing"
date:   2015-09-28 06:24:13
categories: jruby_art update
---

|feature    |  ruby-processing  |  JRubyArt       |
|---------- |:-------------:    |------:          |
|binary     |rp5                |k9               |
|java       |jdk-7              |jdk-8            |
|version    |processing-2.2.1   |processing-3.0.1+|
|ruby       |1.9.3              |2.2              |
|ArcBall    |library            |built-in         |
|Vec2D      |library            |built-in         |
|Vec3D      |library            |built-in         |
|DegLut     |library            |built-in         |
|FX2D       |No                 |Yes              |
|App Export |Yes                |No               |
|Live mode  |Yes                |Yes              |
|Watch mode |Yes                |Yes              |
|settings   |no                 |see below        |

-----
Introduced for processing-3.0 is the `settings` method, but this is hidden for users of the processing ide. This is where `size` belongs or `full_screen`, also you should set `smooth` and `pixel_density` here. Retina users can make use of their hi-dpi display by setting `pixel_density(2)`, NB: size should be first line of `settings`, and if used `pixel_density(2)` should be next.
