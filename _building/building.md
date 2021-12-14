---
layout: page
title: Developing / Building ruby-processing projects
---

All projects can be built on 64 bit linux, including PiCrate for RaspberryPI. Failing that use Windows, Apple is close to useless for open source development, I would be glad if you could prove wrong...

I use [Netbeans][netbeans] when developing java components and [Atom][atom] for:-
1. Developing ruby components (and creating and running sketches)
2. Automating github
3. Creating markdown (and previewing) documentation

Any experienced developer might prefer other tools but the above work well for me, from time to time I might use vim combined with commandline tools (eg rubocop) instead of atom.

# Tools of the Trade

You will need to install jdk11+, maven (apache-maven-3.8.3+), jruby-9.3.2.0+, and have access to processing jogl jars. Note we prefer a local install of [minitest][minitest] for testing.

# How to build ruby-processing projects

You will need to get the latest version of JOGL (currently JOGL-2.4 as a release candidate)

```bash
git clone repo
cd repo
rake
```

It really is as simple as that...

We are using a [polyglot maven build][polyglot] and the pom.xml is only produced for reference, if modifications are required modify `pom.rb`, `Rakefile` and `*.gemspec` please don't alter the `Gemfile` (_which is only included for bundler fans_), preferably don't use `bundler` you probably don't need it, and it can't control jruby version, java version, jar version (or much else that is important to JRubyArt/propane). If your crutch is broken why use it?

[netbeans]: https://netbeans.apache.org/
[atom]: https://atom.io/
[local]: https://maven.apache.org/guides/mini/guide-3rd-party-jars-local.html
[minitest]: https://github.com/seattlerb/minitest
[polyglot]: https://github.com/takari/polyglot-maven
