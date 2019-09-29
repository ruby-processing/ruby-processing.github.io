---
layout: page
title: Building ruby-processing projects
---

# Tools of the Trade

You will need to install jdk12, maven (apache-maven-3.5+), jruby-9.2.8.0+, and have access to processing jogl jars. Note we prefer a local install of [minitest][minitest] for testing.

# How to build ruby-processing projects

Install the processing so you can access the processing hacked jogl jars, unfortunately you will need to do this until the processing guys (mainly Ben Fry) see the light and convert vanilla processing to use a maven build. Do this for any other jars you require that are not available from maven central.

```bash
git clone repo
cd repo
rake
```

It really is as simple as that...

We are using a [polyglot maven build][polyglot] and the pom.xml is only produced for reference, if modifications are required modify `pom.rb`, `Rakefile` and `*.gemspec` please don't alter the `Gemfile` (_which is only included for bundler fans_), preferably don't use `bundler` you probably don't need it, and it can't control jruby version, java version, jar version (or much else that is important to JRubyArt/propane). If your crutch is broken why use it?

[local]: https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html
[minitest]: https://github.com/seattlerb/minitest
[polyglot]: https://github.com/takari/polyglot-maven
