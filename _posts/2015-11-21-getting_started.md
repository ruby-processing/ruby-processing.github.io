---
layout: post
title:  "Getting Started on Linux"
date:   2015-11-21 06:24:13
categories: jruby_art update
permalink: /linux_started/
---

### Getting Started With JRubyArt (stolen from [Ben Lewis][ben])

If you love to code because it is a creative process, then you should give JRubyArt a try because it can be used to [create music][sound], art, animations, [videos][video] and much more. Also since it is based on the latest [Processing][processing] you can access a vast range of libraries to make the difficult things easier.

### What Is Processing?

Processing is a simple language, based on Java, that you can use to create digital graphics. It's easy to learn, fun to use, and has an amazing online community comprised of programmers, visual artists, musicians, and interdisciplinary artists of all kinds.

Processing was built by Casey Reas and Benjamin Fry, two protegés of interdisciplinary digital art guru John Maeda at the MIT Media Lab.

Since the project began in 2001, it's been helping teach people to program in a visual art context using a simplified version of Java. It comes packaged as an IDE that can be downloaded and used to create and save digital art “sketches”.

In 2009, Jeremy Ashkenas (aka jashkenas, creator of Backbone.JS, Underscore.JS, and Coffeescript), published the original [ruby-processing gem][gem]. It wraps Processing in a shim that makes it even easier to get started if you know Ruby. It has been since updated to use processing-2.2.1 by Martin Prout (final version using jruby-1.7.24 corresponding to ruby-1.9.3 syntax), NB: no more releases are expected, and ruby-processing is not compatible with processing-3.0+.

In 2015, Martin Prout (aka monkstone) published the [JRubyArt gem][jrubyart], loosely based on the original ruby-processing, but updated to use processing-3.0+ and jruby-9.0.5.0+ (ruby-2.2 syntax)

### Why JRubyArt?

Since Processing already comes wrapped in an easy-to-use package, you may ask: "why should I bother with JRubyArt?"

The answer: if you know how to write Ruby, you can use Processing as a visual presentation layer of a much more complex program. Games, interactive art exhibits, innovative music projects, anything you can imagine; it's all at your fingertips.

Additionally, you don't have to declare types, voids, or understand the differences between floats and ints to get started, as you do in pure Processing.

Although there are some drawbacks to using the Ruby version Processing (slower start up time, and sometimes performance), having Ruby's API available to translate your ideas into sketches more than makes up for them.

Why was ruby-processing not updated to use processing3.0+? The [major changes][changes] between processing-2.2.1 and processing-3.0 are not backward compatible. Furthermore since JRubyArt was designed to use jruby-9.0.0.0 from the outset, it makes use of the more literate ruby-2.2 syntax (although the original ruby-processing will run with jruby-9.0.5.0, the examples and the ruby-processing library are all based on ruby-1.9.3 syntax).

### Setup

Setting JRubyArt for the first time, can seem a bit involved (especially if you are addicted to rvm or rbenv). The JRubyArt gem relies on JRuby-9.0.5.0+, Processing-3.0.1, and a handful of other dependencies. Here's how to get them all installed and working on linux.

You will likely have wget installed, install latest 0racle jdk-8, and some version of ruby-2.2+ preferably jruby-9.0.5.0. If your distro does not offer a sufficiently up to date version of java install Oracle version in `/opt` as suggested for jruby and create appropriate links (use `update-alternatives` for a debian based distro).

### Processing

If you are on ArchLinux 
{% highlight bash %}
sudo pacman -S processing # installs processing-3.0.1
{% endhighlight %}

Otherwise you can check to see what platforms are officially supported [here][platforms].

Download Processing-3.0.2+ from the [official website][official] and install, prefer to install in say `~/processing-3.0.2`, that way you can keep processing-2.2.1 (or earlier version of processing), which you may find useful.  When you're done, make sure to take note of the directory you installed the app to complete the configuration. 

__Finishing up__

Fire up processing, and use the processing ide to install the sound and video libraries as these are no longer included in the download (but you will surely want them):-

`Sketch/Import Library/Add Library/Video` _ide menu_

### JRuby

For ArchLinux only:-

{% highlight bash %}
sudo pacman -S jruby # installs jruby-9.0.5.0
sudo pacman -S ruby # installs up to date MRI ruby
{% endhighlight %}

For debian (ubuntu/mint etc) distro installers are hopelessly out of date (even for MRI ruby), my preference is to download and install jruby (and MRI ruby) to the `/opt` folder and make use of the excellent update-alternatives tool to create symbolic links to the relevant binaries (this is much more robust than rvm or rbenv). Use rvm or better rbenv if you must, but be aware they can be particulary troublesome on linux (and are completely incompatible, and difficult to get rid of especially rvm).

### JRubyArt

Configuration:-

JRubyArt needs to know where you've installed processing, where your processing sketchbook lives (for the video and audio libraries etc), and whether you've done a system/user install of jruby.

Config file is `config.yml` in the `~/.jruby_art folder` so it can co-exist with a ruby-processing install (~/.rp5rc), it is advisable to have separate folders for processing-3.0 and processing-2.2.1 sketchbooks.

{% highlight yaml %}
# Example YAML configuration file for jruby_art on linux (debian etc)
PROCESSING_ROOT: /home/tux/processing-3.0.2
# important sketch_book path may be different for processing-3.0
sketchbook_path: /home/tux/sketchbook 
{% endhighlight %}

Alternative but probably only for ArchLinux 

{% highlight yaml %}
# Example YAML configuration file for jruby_art on ArchLinux 
PROCESSING_ROOT: /usr/share/linux
# important sketch_book path may be different for processing-3.0
sketchbook_path: /home/tux/sketchbook 
{% endhighlight %}

If you can/are using rvm or rbenv switch to using jruby-9.0.5.0+ then

{% highlight bash %}
gem install jruby_art
{% endhighlight %}

if you are brave (or sensible) and have done an independent jruby install

{% highlight bash %}
jruby -S gem install jruby_art # then install other gems eg toxiclibs the same way
{% endhighlight %}

but you might find regular MRI gem install works (also tends to be quicker)

{% highlight bash %}
gem install jruby_art
{% endhighlight %}

After installing the the gem you need to download and install jruby-complete,
this is not included in the gem, because it would make it too big, however providing you've got wget installed all you need to do is:-

{% highlight bash %}
k9 setup install # downloads and installs jruby-complete requires wget
{% endhighlight %}

While you are at it you should install the samples
 
{% highlight bash %}
k9 setup unpack_samples # downloads and unpacks samples requires wget
{% endhighlight %}

### Running examples

To run a bunch of the samples as a demo:-

{% highlight bash %}
cd ~/k9_samples
rake # autoruns demo sketches sequentially (random order per folder)
{% endhighlight %}

More selectively run per folder or individual sketches:-

{% highlight bash %}
cd ~/k9_samples/contributed # for example
rake # autoruns files in contributed folder
k9 run jwishy.rb # run the JWishy sketch, using an installed jruby
cd ~/k9_samples/processing_app/topics/shaders
rake # autoruns shader sketches
k9 --nojruby run monjori.rb # run the Monjori sketch with jruby-complete
{% endhighlight %}

### Creating your own sketch

{% highlight bash %}
k9 create fred 200 200 # creates a bare sketch fred.rb (see below)
vim fred.rb # other editors are available
:!k9 run % # from vim runs the sketch 
{% endhighlight %}

You may want to try other [development environments][editor] eg emacs or even netbeans. Needless to say ArchLinux can install these for you, but both need a bit of post install love get the best out of them (vim in the main just works, and is super light weight).

{% highlight ruby %}
def setup
  sketch_title 'Fred'
end

def draw

end

def settings
  size 200, 200
  # smooth # here
end
{% endhighlight %}

Read more about using the [processing api here][api]

[api]: {{ site.url }}/api/
[ben]:https://blog.engineyard.com/2015/getting-started-with-ruby-processing
[processing]:https://processing.org/
[gem]:https://rubygems.org/gems/ruby-processing
[jrubyart]:https://rubygems.org/gems/jruby_art
[changes]:https://github.com/processing/processing/wiki/Changes-in-3.0
[official]:https://processing.org/download/?processing
[platforms]:https://github.com/processing/processing/wiki/Supported-Platforms
[editor]:{{ site.url }}/editors/
[sound]:http://monkstone.github.io/_posts/sound/
[video]:http://monkstone.github.io/_posts/
