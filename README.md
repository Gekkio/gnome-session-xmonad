gnome-session-xmonad
====================

This Ubuntu package contains session files for Gnome + XMonad.  The latest
xmonad package in Debian/Ubuntu no longer has working session files, so I'm
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

This installs the **GNOME + XMonad** session, which can be selected from the
login screen. Make sure you select the right one, because the list probably has
other xmonad sessions as well.

These xmonad sessions are unrelated to this package, and are not guaranteed
to work:

* GNOME Flashback (Xmonad)
* XMonad

Your xmonad configuration must have the necessary gnome hooks in place.
In practice things work perfectly if you are using `gnomeConfig` properly in
your configuration.

Minimal installation (doesn't install GHC)
------------------------------------------

Like the [Quick Installation](#quick-installation) above, except we avoid
bringing in Ubuntu's GHC ecosystem:

    sudo add-apt-repository ppa:gekkio/xmonad
    sudo apt-get update
    sudo apt-get install --no-install-recommends gnome-session-xmonad

To be able to compile your `~/.xmonad/xmonad.hs`, you'll probably also want
to install the X11 packages specified in the 
[Xmonad README](https://github.com/xmonad/xmonad/blob/master/README.md#building):

    sudo apt-get install libx11-dev libxinerama-dev libxext-dev libxft-dev libxrandr-dev libxss-dev

This minimal installation assumes you already have GHC installed by some
non-Apt means, e.g. via Stack or a http://haskell.org/ghc tarball.

Supported Ubuntu versions
-------------------------

These Ubuntu versions are supported at the moment:

+ 14.04 Trusty (LTS)
+ 16.04 Xenial (LTS)
+ 18.04 Bionic (LTS)
+ 18.10 Cosmic
+ 19.04 Disco
