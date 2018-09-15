---
title: "icesh(1)"
---
# NAME

    icesh - control properties of windows

# SYNOPSIS

- **icesh** \[_OPTIONS_\] _ACTIONS_
- **icesh** {**-h**\|**--help**} \[_OPTIONS_\] \[_ACTIONS_\]
- **icesh** {**-V**\|**--version**}
- **icesh** {**-C**\|**--copying**}

# DESCRIPTION

**icesh** provides commands for use by shell scripts that affect a
window's state similar to [wmctrl(1)](https://manned.org/wmctrl.1) or [xdotool(1)](https://manned.org/xdotool.1), except more
limited, specifically for **icewm(1)**, and limited to affecting GNOME
WinWM/WMH properties.

# OPTIONS

**icesh** recognizes the following options:

## COMMAND OPTIONS

Command options are mutually exclusive.  Only one command option can be
specified per invocation.  If no command option is specified, action
argument parsing and processing is performed.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## GENERAL OPTIONS

- **-display** _DISPLAY_

    Specifies the X11 _DISPLAY_ to use.  When unspecified, defaults to the
    $DISPLAY environment variable.

- **-window** _WINDOW\_ID_

    Specifies the identifier of the window, _WINDOW\_ID_, for which the
    action applies.
    When no _WINDOW\_ID_ or _WM\_CLASS_ is specified, a selection crossbar
    is invoked to select the desired window.

- **-class** _WM\_CLASS_

    Specifies the window manager class, _WM\_CLASS_, for which the action
    applies.
    When no _WINDOW\_ID_ or _WM\_CLASS_ is specified, a selection crossbar
    is invoked to select the desired window.

# ARGUMENTS

**icesh** accepts the following arguments:

- **ACTIONS** ::= _ACTION_\[ _ACTION_\]\*

    Actions can be one of:

    - **setIconTitle** _TITLE_

        Set the icon title for the specified window to _TITLE_.

    - **setWindowTitle** _TITLE_

        Set the window title for the specified window to _TITLE_

    - **setGeometry** _GEOMETRY_

        Set the window geometry for the specified window to _GEOMETRY_.

    - **setState** _MASK_ _STATE_

        Set the GNOME window state for the specified window to _STATE_.  Only
        the bits selected by _MASK_ are affected.  _STATE_ and _MASK_ are
        expressions of the domain _GNOME window state_.  See ["GNOME window
        state"](#gnome-window-state), below, for _STATE_ and _MASK_ symbols.

    - **toggleState** _STATE_

        Toggle the GNOME window state bits specified by the _STATE_ expression
        for the specified window.  See ["GNOME window state"](#gnome-window-state), below, for
            _STATE_ symbols.

    - **setHints** _HINTS_

        Set the _GNOME window hints_ for the specified window to _HINTS_.  See
        ["GNOME window hints"](#gnome-window-hints), below, for _HINTS_ symbols.

    - **setLayer** _LAYER_

        Moves the specified window to another _GNOME window layer_.  See
        ["GNOME window layer"](#gnome-window-layer), below, for _LAYER_ symbols.

    - **setWorkspace** _WORKSPACE_

        Moves the specified window to another workspace.  Select the root
        window to change the current workspace.

    - **listWorkspaces**

        Lists the names of all workspaces.

    - **setTrayOption** _TRAYOPTION_

        Set the _IceWM tray option_ hint for the specified window to
        _TRAYOPTION_.  See ["IceWM tray options"](#icewm-tray-options), below, for _TRAYOPTION_
        symbols.

- **EXPRESSION** ::= _SYMBOL_ \| _EXPRESSION_ { `+` \| `\|` }
_SYMBOL_

    Each _SYMBOL_ may be from one of the following applicable domains:

    - _GNOME window state_

        Named symbols of the domain _GNOME window state_ (numeric range:
        0-1023):

            AllWorkspaces          (1)
            Sticky                 (1)
            Minimized              (2)
            Maximized             (12)
            MaximizedVert          (4)
            MaximizedVertical      (4)
            MaximizedHoriz         (8)
            MaximizedHorizontal    (8)
            Hidden                (16)
            All                 (1023)

        These symbols are used with the _MASK_ and _STATE_ arguments to the
        `setState` and `toggleState` actions.

    - _GNOME window hint_

        Named symbols of the domain _GNOME window hint_ (numeric range: 0-63):

            SkipFocus              (1)
            SkipWindowMenu         (2)
            SkipTaskBar            (4)
            FocusOnClick          (16)
            DoNotCover            (32)
            All                   (63)

        These symbols are used with the _HINTS_ argument to the `setHints`
        action.

    - _GNOME window layer_

        Named symbols of the domain _GNOME window layer_ (numeric range: 0-15):

            Desktop                (0)
            Below                  (2)
            Normal                 (4)
            OnTop                  (6)
            Dock                   (8)
            AboveDock             (10)
            Menu                  (12)

        These symbols are used with the _LAYER_ argument to the `setLayer`
        action.

    - _IceWM tray option_

        Named symbols of the domain _IceWM tray option_ (numeric range: 0-2):

            Ignore                 (0)
            Minimized              (1)
            Exclusive              (2)

        These symbols are used with the _TRAYOPTION_ argument to the
        `setTrayOption` action.

# USAGE

The purpose of **icesh** is to provide commands that can be used from a
shell script (see [sh(1)](https://manned.org/sh.1)) to affect the state, geometry and hints
associated with a window, or to list and parse information about
existing windows.

It should be noted that **icesh** works on any window manager that is
compliant with the GNOME WinWM/WMH specification.  The `setTrayOption`
action; however, is IceWM specific.

# EXAMPLES

The following command will list all the workspaces associated with the
root window after a window (any window) is selected:

    icesh listWorkspaces

Example output:

    workspace #0: `main'
    workspace #1: `web'
    workspace #2: `doc'
    workspace #3: `dev'
    workspace #4: `scr'
    workspace #5: `gfx'
    workspace #6: `misc'
    workspace #7: `'

# ENVIRONMENT

The following environment variables are set or examined by **icesh**:

- **DISPLAY**

    When the **-display** option is not specified, the `DISPLAY` environment
    variable is consulted to determine the display.

# COMPLIANCE

While **icesh** is largely compliant with the GNOME WinWM/WMH
specification, it does not support NetWM/EWMH.

# BUGS

**icesh** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# HISTORY

**icesh** is historical and deprecated.  The command originally (and
still) only supported the GNOME WinWM/WMH specification.  Unlike
[wmctrl(1)](https://manned.org/wmctrl.1) and [xdotool(1)](https://manned.org/xdotool.1), NetWM/EWMH support was never included.
Except for the `setTrayOption` command, [wmctrl(1)](https://manned.org/wmctrl.1) and [xdotool(1)](https://manned.org/xdotool.1)
are quite capable of performing the necessary functions and more.

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

[Index](/man) | [IceWM](/)
