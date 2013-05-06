---
layout: post
title: "Fix Ruby native gems issue after upgrading to Mountain Lion"
date: 2012-08-15 11:37
comments: true
categories: ruby osx
---

If after upgrading to Mountain Lion you encounter issues such as below

    $ gem install sqlite3
    Building native extensions.  This could take a while...
    ERROR:  Error installing sqlite3:
    ERROR: Failed to build gem native extension.

          /Users/sailavu/.rbenv/versions/1.9.2-p290/bin/ruby extconf.rb
    checking for sqlite3.h... *** extconf.rb failed ***
    Could not create Makefile due to some reason, probably lack of
    necessary libraries and/or headers.  Check the mkmf.log file for more
    details.  You may need configuration options.

    Provided configuration options:
      --with-opt-dir
      --without-opt-dir
      --with-opt-include
      --without-opt-include=${opt-dir}/include
      --with-opt-lib
      --without-opt-lib=${opt-dir}/lib
      --with-make-prog
      --without-make-prog
      --srcdir=.
      --curdir
      --ruby=/Users/sailavu/.rbenv/versions/1.9.2-p290/bin/ruby
      --with-sqlite3-dir
      --without-sqlite3-dir
      --with-sqlite3-include
      --without-sqlite3-include=${sqlite3-dir}/include
      --with-sqlite3-lib
      --without-sqlite3-lib=${sqlite3-dir}/lib
      --enable-local
      --disable-local

Then the try theses steps:

- Install XCode (v4.4.1) from App Store  
- Go to XCode > Preferences > Downloads > Components and install the Command Line Tools  
- Go to Terminal and run `sudo ln -s /usr/bin/llvm-gcc-4.2 /usr/bin/gcc-4.2`

If for some reason you still need gcc-4.2 then install apple-gcc42 via Homebrew dupes.  
You'll then need the following symlink `sudo ln -s /usr/local/bin/gcc-4.2 /usr/bin/gcc-4.2`  

Credit goes to [OSX GCC Install](https://github.com/kennethreitz/osx-gcc-installer), [Gcc 4.2 version missing](http://stackoverflow.com/questions/8007683/gcc-4-2-version-missing)


