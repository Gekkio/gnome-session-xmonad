gnome-session-xmonad
====================

This Ubuntu package contains session files for Gnome + XMonad.  The latest
xmonad package in Debian/Ubuntu no longer has such session files, so I'm
maintaining them in this repository. The sessions are simply copies of
metacity-based sessions from gnome-session-flashback/gnome-session-fallback
packages with metacity replaced with xmonad.

Replacing metacity with xmonad seems to keep everything happy, and based on my
testing everything including volume keys works fine.

For ready-to-use binary packages, see my PPA here, or check out the quick
installation guide below:

https://launchpad.net/~gekkio/+archive/ubuntu/xmonad

Quick installation
------------------

    sudo add-apt-repository ppa:gekkio/xmonad
    sudo apt-get update
    sudo apt-get install gnome-session-xmonad

Supported Ubuntu versions
-------------------------

These Ubuntu versions are supported at the moment:

+ 12.04 Precise (LTS)
+ 14.04 Trusty (LTS)
+ 14.10 Utopic
+ 15.04 Vivid
+ 15.10 Wily
