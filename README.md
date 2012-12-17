wiimote-mupen64
===============

After spending agonizing hours trying to get it to work, I finally have a
functional setup for using a Wiimote in Mupen64plus under Linux.

Overview
--------

This contraption works by using
[`wminput`](http://abstrakraft.org/cwiid/wiki/wminput) to get input data from
the Wiimotes. `wminput` is not installed in Ubuntu by default and is available
in the repos.

Steps to get it working
=======================

1. Cut a hole in a box.

2. Install `wminput` with

        sudo apt-get install wminput

3. Copy `52-wiimote.rules` to `/etc/udev/rules.d/`. You'll have to restart
   `udev` for it to take effect, but I had to restart the whole computer.

4. Copy `wmconfig` to `.cwiid/wminput/`

5. Copy the contents of `mupen64plus.cfg` to the `[Input-SDL-Control1]` section
   of `~/.config/mupen64plus/mupen64plus.cfg`, replacing the existing contents
   of that section

6. Launch `wminput` with

        wminput -c wmconfig -r -w

7. Put the Wiimote in discoverable mode by pressing `1` and `2` simultaneously.
   After a few seconds, `wminput` should print `Ready.` to the console.

8. Launch `mupen64plus` with your game of choice.

9. ???

10. Profit!

About Bindings
==============

I was setting things up in order to play the wonderful _Jet Force Gemini_, which
influenced my choice of bindings. Other mappings are certainly viable; customize
to your liking.

The format will be

* N64( **Z** ) :: Wii( **B** ) = SDL(`5`)

That is, the `Z` button of the N64 (the trigger under the joystick) will be
bound to the `B` button of the Wii (the trigger on the Wiimote), which
corresponds to the SDL keycode `7`. It is the SDL keycode which goes into the
`mupen64plus.cfg` file.

Bindings
--------

* N64( **L** ) :: Wii( **1** ) = SDL(`7`)
* N64( **R** ) :: Wii( **Z** ) = SDL(`9`)
* N64( **Z** ) :: Wii( **B** ) = SDL(`5`)
* N64( **A** ) :: Wii( **A** ) = SDL(`4`)
* N64( **B** ) :: Wii( **C** ) = SDL(`6`)
* N64( **Start** ) :: Wii( **Home** ) = SDL(`10`)
* N64( **C↑** ) :: Wii( **D-pad↑** ) = SDL(`0`)
* N64( **C↓** ) :: Wii( **D-pad↓** ) = SDL(`1`)
* N64( **C←** ) :: Wii( **D-pad←** ) = SDL(`2`)
* N64( **C→** ) :: Wii( **D-pad→** ) = SDL(`3`)
* N64( **Joystick X** ) :: Wii( **Joystick X** ) = SDL(`axis0`)
* N64( **Joystick Y** ) :: Wii( **Joystick Y** ) = SDL(`axis1`)

Multiple controllers
====================

To run multiple controllers, you'll need a separate `wminput` process for each
controller; each `wminput` process can handle only one Wiimote at a time.

Wishes for the future
=====================

It would be nice to be able to use
[`XWiimote`](https://github.com/dvdhrm/xwiimote) instead of `wminput` since it
comes with Ubuntu (it's a kernel module) and can be paired using the Bluetooth
applet instead of running a daemon on the command line. SDL recognizes the
Wiimote, but it creates a separate device for the main Wiimote and the nunchuck.
So far as I can tell, Mupen64plus does not let you bind half of the buttons to
one device and the other half to a different one.

This shouldn't be a problem if you are using a classic controller, since all of
the buttons and joysticks needed are on it, but I don't have a classic, so I'm
stuck for now. If anyone can figure out a way to make this work, I'd be most
appreciative.
