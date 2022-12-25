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

Update 12/2022: I've switched to Pop!_OS and its tiling window manager, and have no plans to update this repository/package anymore!
-

So long, and thanks for all the fish :)

If you need this functionality, you can make the necessary files yourself. At
the time of writing this (12/2022), the necessary steps are:

1. Install `gnome-session-flashback` package so you get the necessary
   configuration files for `metacity` (the old gnome window manager)
2. Make copies of all relevant `metacity`-based session configuration files and replace
   `metacity` with `xmonad` in them. This includes at least the following files:

    - `/usr/libexec/gnome-flashback-metacity`
    - `/usr/lib/systemd/user/gnome-session@gnome-flashback-metacity.target.d/session.conf`
    - `/usr/share/gnome-session/sessions/gnome-flashback-metacity.session`
    - `/usr/share/xsessions/gnome-flashback-metacity.desktop`
3. For most Ubuntu releases this has been enough. If the session still doesn't
   work, you might need to update some common configuration file too instead of
   just adding new files. For example,
   [see this commit](https://github.com/Gekkio/gnome-session-xmonad/commit/78354732899955ca213c09f176ca2bf3097186d5)
   for a fix that was necessary for Ubuntu Xenial. I can't predict what
   problems future Ubuntu versions will have, but it might be something
   similar.

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
your configuration, as documented
[on Hackage](https://hackage.haskell.org/package/xmonad-contrib-0.10/docs/XMonad-Config-Gnome.html).

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

+ 18.04 Bionic (LTS)
+ 20.04 Focal (LTS)
+ 21.10 Impish
+ 22.04 Jammy
