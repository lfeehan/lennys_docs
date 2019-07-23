# This info is thin, like  butter scraped over too much bread
[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

Blah blah blah

# Docker Related

### Multiarch cross-compilation
Building at 32 bit image on a 64 bit host

 - There is a convenient repository which sets up a 64bit linux environment for cross architecture building which automatically sets up binfmt_misc using qemu and other cross-architecture tools to allow you to build against most architectures. https://github.com/multiarch/qemu-user-static/blob/master/README.md
    ```
    docker run --rm --privileged multiarch/qemu-user-static:register
    ```
 - Now base your docker image off the appropriate image in this repo: https://hub.docker.com/u/multiarch
 - Select your preferred distribution, and under each distribution you can find tags for your required architecture. e.g, in Dockerfile:
    ```
    FROM multiarch/debian-debootstrap:armhf-stretch
    ```
 - Debian stretch for armhf (arm hard float) which will run on the Beaglebone black armv7l 32 bit

