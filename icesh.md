---
title: "icesh(1)"
---
# NAME

    icesh - control properties of windows

# SYNOPSIS

- **icesh** \[_OPTIONS_\] _ACTIONS_

# DESCRIPTION

**icesh** provides commands for use by shell scripts that affect a
window's state, similar to [wmctrl(1)](https://manned.org/wmctrl.1) or [xdotool(1)](https://manned.org/xdotool.1), except
mostly limited to GNOME WinWM/WMH properties
and **icewm(1)** specific commands.

# OPTIONS

**icesh** recognizes the following options:

## COMMAND OPTIONS

A command option specifies the window or windows to which subsequent
arguments apply. If no command option is given, but an argument
does require a window then a selection crossbar is invoked to select
the desired window interactively. Some arguments do not require this.

- **-w**, **-window** _WINDOW\_ID_

    Specifies the identifier of the window, _WINDOW\_ID_, for which the
    action applies.  Special identifiers are **root** for the root window
    and **focus** for the currently focused window.

- **-c**, **-class** _WM\_CLASS_

    Specifies the window manager class, _WM\_CLASS_, for which the action
    applies.  If _WM\_CLASS_ contains a period, only windows with exactly
    the same _WM\_CLASS_ property are matched.  If there is no period,
    windows of the same class and windows of the same instance (aka. _-name_)
    are selected.

- **-r**, **-root**

    Is equivalent to **-window** **root**.

- **-f**, **-focus**

    Is equivalent to **-window** **focus**.

## GENERAL OPTIONS

- **-d**, **-display** _DISPLAY_

    Specifies the X11 DISPLAY.  If unspecified, defaults to **$DISPLAY**.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# ARGUMENTS

**icesh** accepts the following arguments:

- **ACTIONS** ::= _ACTION_ \[_ACTION_\]\*

    Actions can be one of:

    - **setIconTitle** _TITLE_

        Set the icon title for the specified window to _TITLE_.

    - **getIconTitle**

        Prints the icon title for the specified window.

    - **setWindowTitle** _TITLE_

        Set the window title for the specified window to _TITLE_

    - **getWindowTitle**

        Prints the window title for the specified window.

    - **setGeometry** _GEOMETRY_

        Set the window geometry for the specified window to _GEOMETRY_.

    - **getGeometry**

        Prints the window geometry for the specified window.

    - **setState** _MASK_ _STATE_

        Set the GNOME window state for the specified window to _STATE_.  Only
        the bits selected by _MASK_ are affected.  _STATE_ and _MASK_ are
        expressions of the domain GNOME window state.  See ["GNOME window
        state"](#gnome-window-state), below, for _STATE_ and _MASK_ symbols.

    - **toggleState** _STATE_

        Toggle the GNOME window state bits specified by the _STATE_ expression
        for the specified window.  See ["GNOME window state"](#gnome-window-state), below, for
        _STATE_ symbols.

    - **getState**

        Prints the GNOME window state for the specified window.

    - **setHints** _HINTS_

        Set the GNOME window hints for the specified window to _HINTS_.  See
        ["GNOME window hints"](#gnome-window-hints), below, for _HINTS_ symbols.

    - **getHints**

        Prints the GNOME window hints for the specified window.

    - **setLayer** _LAYER_

        Moves the specified window to another GNOME window layer.  See
        ["GNOME window layer"](#gnome-window-layer), below, for _LAYER_ symbols.

    - **getLayer**

        Prints the GNOME window layer for the specified window.

    - **setWorkspace** _WORKSPACE_

        Moves the specified window to another workspace.  Select the root
        window to change the current workspace. If _WORKSPACE_ is `All`
        then the specified window becomes visible on all workspaces.

    - **getWorkspace**

        Prints the workspace for the specified window.

    - **listWorkspaces**

        Lists the names of all workspaces.

    - **setTrayOption** _TRAYOPTION_

        Set the _IceWM tray option_ hint for the specified window to
        _TRAYOPTION_.  See ["IceWM tray options"](#icewm-tray-options), below, for _TRAYOPTION_
        symbols.

    - **getTrayOption**

        Prints the IceWM tray option for the specified window.

    The following actions do not require a window or class command option:

    - **check**

        Prints information about the current window manager, like name,
        version, class, locale, command, host name and pid.

    - **clients**

        Lists all managed client windows, their titles and geometries.

    - **shown**

        Lists all managed client windows for the current desktop,
        their titles and geometries.

    - **windows**

        Lists all toplevel windows, their titles and geometries.

    - **logout**

        Ask IceWM to execute the `LogoutCommand`.

    - **reboot**

        Ask IceWM to execute the `RebootCommand`.

    - **shutdown**

        Ask IceWM to execute the `ShutdownCommand`.

    - **cancel**

        Ask IceWM to cancel the logout/reboot/shutdown.

    - **about**

        Ask IceWM to show the about window.

    - **windowlist**

        Ask IceWM to show the window list window.

    - **restart**

        Ask IceWM to restart.

    - **suspend**

        Ask IceWM to execute the `SuspendCommand`.

    - **guievents**

        Monitor the **ICEWM\_GUI\_EVENT** property and report all changes.

    - **colormaps**

        Monitor which colormap is installed.

    - **runonce** _program_ \[_arguments..._\]

        This action is meant to be used together with the **-class** option.
        Only if no window is matched by _WM\_CLASS_ then
        _program_ \[_arguments..._\] is executed.

    Some actions require one or two _EXPRESSION_ arguments.

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
compliant with the GNOME WinWM/WMH specification.  Some commands, like
`setTrayOption` and the actions, however, are IceWM specific.

# EXAMPLES

The following command lists all workspace names:

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

The following environment variables are examined by **icesh**:

- **DISPLAY**

    The display to use if the **-display** option is unspecified.

# COMPLIANCE

While **icesh** is largely compliant with the GNOME WinWM/WMH
specification, it does not support NetWM/EWMH.

# BUGS

**icesh** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# HISTORY

**icesh** is historical and deprecated.  The command only supports
the GNOME WinWM/WMH specification and IceWM specific commands.  Unlike
[wmctrl(1)](https://manned.org/wmctrl.1) and [xdotool(1)](https://manned.org/xdotool.1), support for NetWM/EWMH was never included.
For most of the supported commands, [wmctrl(1)](https://manned.org/wmctrl.1) and [xdotool(1)](https://manned.org/xdotool.1)
are quite capable of performing the necessary functions and more.

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
