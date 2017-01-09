---
layout: page
title:  "Building hype library"
---

```bash
mkdir hype_processing
cd hype_processing
wget https://github.com/hype/HYPE_Processing/blob/master/distribution/HYPE.zip
unzip HYPE.zip

cd ../../
mkdir .mvn
touch .mvn/extensions.xml # see below
touch pom.rb # see below
```

### extensions.xml ###
This file tells maven to do a polyglot-ruby build

```xml
<?xml version="1.0" encoding="UTF-8"?>
<extensions>
  <extension>
    <groupId>io.takari.polyglot</groupId>
    <artifactId>polyglot-ruby</artifactId>
    <version>0.1.19</version>
  </extension>
</extensions>
```

### pom.rb ###

This is the ruby polyglot version of `pom.xml`

```ruby
project 'hype' do

  model_version '4.0.0'
  id 'hypeframework:hype:2.0.2'
  packaging 'jar'

  description 'A collection of classes that performs the heavy lifting for you by writing a minimal amount of code.'

  organization 'hypeframework', 'http://www.hypeframework.org/'

  [ 'Joshua Davis', 'James Cruz', 'Benjamin Fox', 'Christopher Tino'].each do |name|
    developer name do
      name name
      roles 'developer'
    end
  end

  license 'BSD 3', 'https://opensource.org/licenses/BSD-3-Clause'

  properties( 'maven.compiler.source' => '1.8',
  'project.build.sourceEncoding' => 'UTF-8',
  'maven.compiler.target' => '1.8',
  'polyglot.dump.pom' => 'pom.xml' )

  jar 'processing.org:core:3.2.3' # latest available from maven central
end
```
Ideally you need apache-maven-3.3.9 installed (at least 3.3.1), to compile with

```bash
mvn package # outputs into target folder
```

For JRubyArt wrap `hype.jar` in `library` folder, put `library` folder in a `hype` folder (and put that alondside regular processing libraries in `sketchbook/libraries` linux etc).  For propane put nested hype library in `~/.propane/libraries folder` see how to install [contributed][contributed] libraries for propane.

[contributed]:https://ruby-processing.github.io/propane/contributed/
