windowfocus
-----------

Here's a simple script for changing window focus.  Usage:

    windowfocus left
    windowfocus right
    windowfocus up
    windowfocus down

You can configure a custom shortcut (I use vi-like bindings:
Alt+Shift+H, Alt+Shift+J, Alt+Shift+K, and Alt+Shift+L).

Requirements:
* xdotool

TODO:
* Currently implemented as a ruby script that calls out to xdotool, so
  it's a little bit slow

License: MIT License (http://www.opensource.org/licenses/mit-license.html) 

