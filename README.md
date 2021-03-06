kids
====

[![Build Status]][Travis CI]

Kids is a log aggregation system.

It aggregates messages like [Scribe](https://github.com/facebookarchive/scribe) and its pub/sub pattern is ported from [Redis](http://redis.io/).


Features
--------

* Real-time subscription
* Distributed collection
* Message persistence
* Multithreading
* Redis protocol
* No third-party dependencies


Installation
------------

You need a complier with C++11 support like GCC 4.7 (or later) or [Clang](http://clang.llvm.org).

Download a [release](https://github.com/zhihu/kids/releases). Untar the tarball, then:

    ./configure
    make
    make test  # optional
    make install

By default, it will be installed to `/usr/local/bin/kids`.
You can use the `--prefix` option to specify the installation location.
Run `./configure --help` for more config options.


Quickstart
----------

Kids comes with some sample config files in `samples/`, after building, simply run:

    kids -c samples/dev.conf

Because kids uses redis protocol, so you can use `redis-cli` to play with it, open another terminal:
    
    $ redis-cli -p 3888
    $ 127.0.0.1:3388> PSUBSCRIBE *

In yet another terminal:
    
    $ redis-cli -p 3388
    $ 127.0.0.1:3388> PUBLISH test message

`redis-cli` needs `redis` to be installed, in MAC, you can run `brew install redis` to install it.

Full explanation of config file, see [here](doc/config.md).

Run `kids --help` for more running options.


License
-------

Kids is BSD-licensed, see LICENSE for more details.


FAQ
---

Q: What is the meaning of "kids"?  
A: "kids" is the recursive acronym of "Kids Is Data Stream".


Architecture
------------

![image](doc/image/arch.jpg)

You can view the Chinese version README [here](README.zh_CN.md)


[Build Status]: https://img.shields.io/travis/zhihu/kids/master.svg?style=flat
[Travis CI]:    https://travis-ci.org/zhihu/kids
