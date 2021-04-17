---
layout: page
title:  "Testing"
---

### Continous Integration ###

[travis ci][travis]

### Platform Testing ###

* Currently only linuxAMD64 bit gets proper testing (Archlinux and Debian/Mint) for JRubyArt art and propane
* RaspberryPI OS and Manjaro ARM also get full testing
* Volunteers are required for Windows and MacOS, thought he probably work (_at least no-one complains_)

### Testing code ###

In a sense every example sketch is a test, if the sketch runs (and they all have run at least once) then the tests are passing. In general sketches are not formally tested, but it would be no bad thing to create tests before [re-factoring][99]. There are _in the main_ tests written into ruby-processing projects, and we favor [minitest][minitest] over [rspec][rspec]. Note that if you are going to use rspec you should probably use `jruby -S rspec` to run your tests and include `require 'java'` in your specs. Static tests such as rubocop can also be useful, but you should be wary of following all the suggested changes to `working code`, there's some funky stuff hidden in JRubyArt code.

[99]:http://www.sandimetz.com/99bottles/
[minitest]:https://github.com/seattlerb/minitest/
[rspec]:http://rspec.info/documentation/
[travis]:https://travis-ci.org/
