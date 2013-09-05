#!/bin/bash

cmd=$1
verbose=1

debug() {
  if [ "${verbose}" = "1" ]; then
    echo "$*"
  fi
}

# Get information for the active window
active=$(xdotool getwindowfocus)
eval $(xdotool getwindowgeometry --shell ${active})
active_x=${X}
active_y=${Y}
active_width=${WIDTH}
active_height=${HEIGHT}
active_screen=${SCREEN}

# Get information about the current desktop
desktop=$(xdotool get_desktop)

# Get a list of visible windows
windows=$(xdotool search --onlyvisible --maxdepth 2 --screen ${active_screen} --desktop ${desktop} --name '.*')
debug "${windows}"

smallest=999999
target=

for window in ${windows}; do
  # If the window is hidden (minimized/iconified), then ignore it
  hidden=$(xwininfo -all -id ${window} | fgrep -i hidden)
  if [ -n "${hidden}" ]; then
    continue
  fi

  # Get information about the window
  eval $(xdotool getwindowgeometry --shell ${window}) # WINDOW X Y WIDTH HEIGHT SCREEN
  
  # Determine how close the window is in the specified direction
  case ${cmd} in
    left)  diff=$(( ${active_x} - ${X} )) ;;
    right) diff=$(( ${X} - ${active_x} )) ;;
    up)    diff=$(( ${active_y} - ${Y} )) ;;
    down)  diff=$(( ${Y} - ${active_y} )) ;;
  esac

  # Is this the next closest window in the specified direction?  If so
  # then keep it.
  if [ "${diff}" -gt 0 -a "${diff}" -lt "${smallest}" ]; then
    smallest=${diff}
    target=${window}
  fi

  debug "${window} ${active_x} ${X} ${active_y} ${Y} ${diff} ${smallest} ${target}"
done

# Switch to the closest window that we found
if [ -n "${target}" ]; then
  xdotool windowfocus "${target}"
fi

