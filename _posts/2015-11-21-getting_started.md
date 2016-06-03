---
layout: post
title:  "Getting Started on Linux"
date:   2015-11-21 06:24:13
categories: jruby_art update
permalink: /linux_started/
---

### Getting Started With JRubyArt (stolen from [Ben Lewis][ben]) ###

If you love to code because it is a creative process, then you should give JRubyArt a try because it can be used to [create music][sound], art, animations, [videos][video] and much more. Also since it is based on the latest [Processing][processing] you can access a vast range of libraries to make the difficult things easier.

### What Is Processing? ###

Processing is a simple language, based on Java, that you can use to create digital graphics. It's easy to learn, fun to use, and has an amazing online community comprised of programmers, visual artists, musicians, and interdisciplinary artists of all kinds.

Processing was built by Casey Reas and Benjamin Fry, two protegés of interdisciplinary digital art guru John Maeda at the MIT Media Lab.

Since the project began in 2001, it's been helping teach people to program in a visual art context using a simplified version of Java. It comes packaged as an IDE that can be downloaded and used to create and save digital art “sketches”.

In 2009, Jeremy Ashkenas (aka jashkenas, creator of Backbone.JS, Underscore.JS, and Coffeescript), published the original [ruby-processing gem][gem]. It wraps Processing in a shim that makes it even easier to get started if you know Ruby. It has been since updated to use processing-2.2.1 by Martin Prout (final version using jruby-1.7.24 corresponding to ruby-1.9.3 syntax), NB: no more releases are expected, and ruby-processing is not compatible with processing-3.0+.

In 2015, Martin Prout (aka monkstone) published the [JRubyArt gem][jrubyart], loosely based on the original ruby-processing, but updated to use processing-3.0+ and jruby-9.1.2.0+ (ruby-2.2 syntax)

### Why JRubyArt? ###

Since Processing already comes wrapped in an easy-to-use package, you may ask: "why should I bother with JRubyArt?"

The answer: if you know how to write Ruby, you can use Processing as a visual presentation layer of a much more complex program. Games, interactive art exhibits, innovative music projects, anything you can imagine; it's all at your fingertips.

Additionally, you don't have to declare types, voids, or understand the differences between floats and ints to get started, as you do in pure Processing.

Although there are some drawbacks to using the Ruby version Processing (slower start up time, and sometimes performance), having Ruby's API available to translate your ideas into sketches more than makes up for them.

Why was ruby-processing not updated to use processing3.0+? The [major changes][changes] between processing-2.2.1 and processing-3.0 are not backward compatible. Furthermore since JRubyArt was designed to use jruby-9.0.0.0+ from the outset, it makes use of the more literate ruby-2.2 syntax (although the original ruby-processing will run with jruby-9.1.2.0, the examples and the ruby-processing library are all based on ruby-1.9.3 syntax).

### Pure JRuby Setup Archlinux ###

Install Software as required:- 

{% highlight bash %}
sudo pacman -S jdk8-openjdk # installs openjdk
sudo pacman -S java-openjfx # installs openjfx
sudo pacman -S jruby # installs jruby
sudo pacman -S processing # installs processing-3.1.1  (community)
{% endhighlight %}

Configure in `~/.jruby_art/config.yml`:-
{% highlight bash %}
PROCESSING_ROOT: /usr/share/processing
sketchbook_path: /home/tux/sketchbook
MAX_WATCH: 30
JRUBY: 'true'
{% endhighlight %}

Install JRubyArt 
{% highlight bash %}
jruby -S gem install jruby_art
jruby -S gem install toxiclibs # optional
jruby -S gem install pbox2d # optional
jruby -S gem install geomerative # optional
{% endhighlight %}

Install vanilla processing libraries from processing-3.1.1 ide (recomended audio, video)

### Pure JRuby Setup Debian (Mint, Ubuntu) ###

The simplest way to install oracle java (but with less control over version etc)

{% highlight bash %}
sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java8-installer
{% endhighlight %}

Alternative method (that puts you in control), download and install latest Oracle jdk (in the `/opt` folder makes sense)

Use `update-alternatives` to install and maintain configuration eg for java:-
{% highlight bash %}
sudo update-alternatives --install /usr/bin/java java /opt/jdk1.8.0_92/bin/java 100
sudo update-alternatives --config java # to configure if required
{% endhighlight %}

Download and install latest jruby (in the `/opt` folder makes sense)

Use `update-alternatives` to install and maintain configuration eg for java:-
{% highlight bash %}
sudo update-alternatives --install /usr/bin/jruby jruby /opt/jruby-9.1.2.0/bin/jruby 100
sudo update-alternatives --config jruby # to configure if required
{% endhighlight %}

Configure in `~/.jruby_art/config.yml`:-
{% highlight bash %}
PROCESSING_ROOT: /home/tux/processing-3.1.1 # `substitute` user for `tux`
sketchbook_path: /home/tux/sketchbook
MAX_WATCH: 30
JRUBY: 'true'
{% endhighlight %}

Otherwise you can check to see what platforms are officially supported [here][platforms].

Download Processing-3.1.1 from the [official website][official] and install, prefer to install in say `~/processing-3.1.1`, that way you can keep processing-2.2.1 (or earlier version of processing), which you may find useful.  When you're done, make sure to take note of the directory you installed the app to complete the configuration. 

Complete the install as for Archlinux (make sure `k9` is on your path or use `jruby -S k9`)

### Alternative JRuby-Complete Setup Debian (Mint, Ubuntu) ###

Download and install latest Oracle jdk as above.

Install MRI ruby (must be at least ruby-2.2)

https://www.ruby-lang.org/en/documentation/installation/ (NB: most distros are hopelessly out of data)

Download Processing-3.1.1 from the [official website][official] and install, prefer to install in say `~/processing-3.1.1`.  When you're done, make sure to take note of the directory you installed the app to complete the configuration see below. 

Configure in `~/.jruby_art/config.yml`:-
{% highlight bash %}
PROCESSING_ROOT: /home/tux/processing-3.1.1 # `substitute` user for `tux`
sketchbook_path: /home/tux/sketchbook
MAX_WATCH: 30
JRUBY: 'false'
{% endhighlight %}

If using `rvm` or `rbenv` make sure you are using ruby2.2+
{% highlight bash %}
gem install jruby_art
k9 setup install # installs jruby-complete
{% endhighlight %}

NB: you may find that you are unable to use gems in your sketches unless you have used jruby to install them.

__Finishing up__

Install the samples
 
{% highlight bash %}
k9 setup unpack_samples # downloads and unpacks samples requires wget
{% endhighlight %}

### Running examples

To run a bunch of the samples as a demo:-

{% highlight bash %}
cd ~/k9_samples/contributed # for example
rake # autoruns files in contributed folder
k9 run jwishy.rb # run the JWishy sketch, using an installed jruby
cd ~/k9_samples/processing_app/topics/shaders
rake # autoruns shader sketches
k9 run monjori.rb # run the Monjori sketch with jruby-complete
{% endhighlight %}

### Creating your own sketch

{% highlight bash %}
k9 create fred 200 200 # creates a bare sketch fred.rb (see below)
vim fred.rb # other editors are available
:!k9 run % # from vim runs the sketch 
{% endhighlight %}

You may want to try other [development environments][editor] eg emacs or even netbeans. Needless to say your distro can install these for you, but both need a bit of post install love get the best out of them (vim in the main just works, and is super light weight).

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
[sound]:http://monkstone.github.io/_posts/minim
[video]:http://monkstone.github.io/jruby_art/update/2015/10/13/manipulate_capture.html
