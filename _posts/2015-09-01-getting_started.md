---
layout: post
title:  "Getting Started"
date:   2015-10-01 06:24:13
categories: jruby_art update
---
### Install

Install [processing-3.0][processing] if you are on Windows, prefer to install in say `C:/Java/Processing` ie folders without special characters or spaces. You need to let JRubyArt know where you've installed processing using config.yml see Configuration. 

Install processings [video library][video] and [audio library][audio] from the processing-3.0 ide (separate install since processing-3.0).

Install `jdk1.8.0_60+` can be openjdk with OpenJFX _a separate download works on ArchLinux_ probably safer to go with the [Oracle version][jdk], currently FX2D is still experimental but may eventually replace JAVA2D

Install JRubyArt gem:-

{% highlight bash %}
gem install jruby_art
k9 setup install # downloads and installs jruby-9.0.3.0 complete requires wget
k9 setup unpack_samples # downloads and unpacks samples requires wget
{% endhighlight %}

### Configuration

Config file is `config.yml` in the `~/.jruby_art folder` so can co-exist with a ruby-processing install (~/.rp5rc)

{% highlight yaml %}
# Example YAML configuration file for jruby_art on linux
PROCESSING_ROOT: /home/tux/processing-3.0
# important sketch_book path may be different for processing-3.0
sketchbook_path: /home/tux/sketchbook 
{% endhighlight %}

{% highlight yaml %}
# Example YAML configuration file for jruby_art on macosx
PROCESSING_ROOT: /Applications/Processing.app/Contents/Java
# important sketch_book path may be different for processing-3.0
sketchbook_path: # user defined needed to pick up libraries
{% endhighlight %}

{% highlight yaml %}
# Example YAML configuration file for jruby_art on Windows
# K9_ROOT: "C:/Ruby22-x64/lib/ruby/gems/2.2.0/gems/jruby_art-1.0.0" # should not be necessary
PROCESSING_ROOT: "C:/Java/Processing" # just a suggestion
sketchbook: "C:/Users/USER/Documents/Processing" # adjust to suit your install
# JRUBY: false # uncomment to use jruby-complete by default especially if you haven't installed jruby
{% endhighlight %}

You could even try our [RubyArt configuration sketch][config] in the processing ide.

### Running examples

{% highlight bash %}
cd ~/k9_samples/contributed # for example
rake # autoruns files in contributed folder
k9 run jwishy.rb # run the JWishy sketch, using an installed jruby
cd ~/k9_samples/processing_app/topics/shaders
rake # autoruns shader sketches
k9 --nojruby run monjori.rb # run the Monjori sketch with jruby-complete
{% endhighlight %}

### Create your own sketches

{% highlight bash %}
k9 create fred 200 200 # creates a bare sketch fred.rb (see below)
vim fred.rb # other editors are available
:!k9 run % # from vim runs the sketch 
{% endhighlight %}

{% highlight ruby %}
def setup
  sketch_title 'Fred'
end

def draw

end

def settings
  size 200, 200, FX2D
  # smooth # here
end
{% endhighlight %}

[processing]:https://www.processing.org/tutorials/gettingstarted/
[video]:https://www.processing.org/reference/libraries/video/
[audio]:https://processing.org/reference/libraries/sound/
[jdk]:http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html
[config]:https://github.com/ruby-processing/Example-Sketches/blob/master/samples/JRubyArt/JRubyArt.pde
