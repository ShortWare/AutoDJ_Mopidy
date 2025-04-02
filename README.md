My Mopidy Setup
===============

Build
-----

Build

    docker build --pull -t bartoszeq/mopidy --build-arg BUILD_FROM=debian:stable-slim .


Run
---

    docker compose up -d

View logs:

    docker logs -f mopidy

Execute any Mopidy command:

    docker exec mopidy mopidy <cmd>
    docker exec mopidy mopidy config
    docker exec mopidy mopidy deps


Mount music from USB
--------------------

    mkdir ~/usb
    mkdir ~/music

Add these lines to `/etc/fstab`.

    /dev/sda1                  /home/jonathan/usb    vfat   defaults         0   0
    /home/jonathan/usb/music   /home/jonathan/music  none   defaults,rbind   0   0
