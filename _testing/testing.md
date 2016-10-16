---
layout: page
title:  "Testing"
---

### Continous Integration ###

[travis ci][travis], we are all set up to go and this would actually work if only the current version of processing was available from maven central

### Platform Testing ###

* Currently only linux64 bit gets proper testing (Archlinux and Debian/Mint)
* Must be working on macOS (volunteers required), I know there are users and no-one complains
* Windows I can only guess (no-one complains)

### Testing code ###

In a sense every example sketch is a test, if the sketch runs (and they all have run at least once) then the tests are passing. In general sketches are not formally tested, but it would be no bad thing to create tests before [re-factoring][99]. There are _in the main_ tests written into ruby-processing projects, and we favor [minitest][minitest] over [rspec][rspec]. Note that if you are going to use rspec you should probably use `jruby -S rspec` to run your tests and include `require 'java'` in your specs. Static tests such as rubocop can also be useful, but you should be wary of some of the suggested changes to `working code`, there's some funky stuff hidden in JRubyArt code.

[99]:http://www.sandimetz.com/99bottles/
[minitest]:https://github.com/seattlerb/minitest/
[rspec]:http://rspec.info/documentation/
[travis]:https://travis-ci.org/
