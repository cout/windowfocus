windowfocus
-----------

Here's a simple script for changing window focus.  Usage:

  windowfocus left
  windowfocus right
  windowfocus up
  windowfocus down

You can configure a custom shortcut (I use vi-like bindings:
Alt+Shift+H, Alt+Shift+J, Alt+Shift+K, and Alt+Shift+L).

TODO:
* Currently implemented as a bash script, so it's a little bit slow
* Need a better algorithm to determine which window is "up", "left",
  etc. (currently just uses the window's X or Y coordinates)

License: MIT License (http://www.opensource.org/licenses/mit-license.html) 

