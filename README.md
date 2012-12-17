wiimote-mupen64
===============

After spending agonizing hours trying to get it to work, I finally have a
functional setup for using a Wiimote in Mupen64plus under Linux.

Overview

This contraption works by using
[`wminput`](http://abstrakraft.org/cwiid/wiki/wminput) to get input data from
the Wiimotes.

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
