Mopidy Setup
===============

Build
-----

Build

    podman build --pull -t bartoszeq/mopidy --build-arg BUILD_FROM=docker.io/debian:stable-slim .


Run
---

    pactl load-module module-native-protocol-tcp listen=0.0.0.0 auth-ip-acl=127.0.0.1
    podman-compose up -d

View logs:

    podman-compose logs -f mopidy

Execute any Mopidy command:

    podman exec mopidy mopidy <cmd>
    podman exec mopidy mopidy config
    podman exec mopidy mopidy deps


Mount music from USB
--------------------

    mkdir ~/usb
    mkdir ~/music

Add these lines to `/etc/fstab`.

    /dev/sda1                  /home/jonathan/usb    vfat   defaults         0   0
    /home/jonathan/usb/music   /home/jonathan/music  none   defaults,rbind   0   0
