Shish's Hacked Versions of Various Test Roms
============================================

- blargg's test roms are great but hard to automate
- mooneye's test roms use `LD B,B` (opcode 0x40) to signal completion, but
  that's a valid instruction, which blargg's roms test, so that isn't ideal
  either

So I basically want to use those test suites, except tweaked to use an
invalid opcode to indicate status. Specifically, I'm defining two new
non-standard opcodes:

- 0xFC - exit with success
- 0xFD - exit with failure

and then hacking other people's test suites to use those.

This repo is primarily designed to be used for testing RosettaBoy (A collection
of gameboy emulators written in a variety of languages) - but if anybody else
thinks that this is a good idea you're welcome to use it. Also if anyone has
any better ideas for how to do fully-automated test suites, I'm open to
suggestions :)

Layout is `<test suite name>/<test name>.gb`
