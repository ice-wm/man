---
title: "icesh(1)"
---
# NAME

    icesh - control window properties and the IceWM window manager

# SYNOPSIS

- **icesh** _OPTIONS\|ACTIONS_+

# DESCRIPTION

**icesh** provides 83 commands to change or query a window's state,
and to interact with the [icewm(1)](icewm) window manager. Command arguments
are called actions. Window actions operate on a selection of windows.
**icesh** has several options to select and filter windows.  Options and
actions can be interspersed. They are processed and evaluated one after
another from left to right. Therefore, an option can only affect a
subsequent action, but not a previous one. Because of this, an action
can operate on a different selection of windows than a previous action,
if it is preceded by a new select option. In combination with filter
options, this gives **icesh** its expressive power. Use it in
[icewm-keys(5)](icewm-keys) to define your own window management hotkeys.

# OPTIONS

**icesh** recognizes the following options:

## SELECT OPTIONS

Select options specify the window or windows to which subsequent
actions apply. If none is given, but an action does require a window,
then a selection crossbar is invoked to select the desired window
interactively. The manager actions do not require window options.

The following five options _select_ one or more client windows.
If needed, they can be repeated for successive actions.

- **-w**, **-window** _WINDOW\_ID_

    Specifies the identifier of the window, _WINDOW\_ID_, for which the
    action applies.  Special identifiers are **root** for the root window
    and **focus** for the currently focused window.

- **-r**, **-root**

    Is equivalent to **-window** **root** and selects the root window.

- **-f**, **-focus**

    Is equivalent to **-window** **focus** and selects the focused window.

- **-a**, **-all**

    Selects all clients of the window manager.

- **-s**, **-shown**

    Selects all currently visible clients of the window manager.

- **-t**, **-top**

    Selects all toplevel windows from the display unconditionally.

## FILTER OPTIONS

The following options _filter_ the currently selected set of windows.
If no previous _select_ option was given then a **-all** option is
implicitly assumed to filter all client windows.

- **-c**, **-class** _WM\_CLASS_

    Filters the set of windows on window manager class, _WM\_CLASS_.  If
    _WM\_CLASS_ contains a period, only windows with exactly the same
    _WM\_CLASS_ property are matched.  If there is no period, windows of the
    same class and windows of the same instance (aka. _-name_) are selected.

- **-l**, **-last**

    Filter clients and keep only the most recent client.

- **-m**, **-machine** _HOST_

    Filters clients by host name. Clients with a WM\_CLIENT\_MACHINE property
    equal to _HOST_ are selected.

- **-n**, **-name** _NAME_

    Filters clients by \_NET\_WM\_NAME or WM\_NAME.
    _NAME_ matches any part of the property value.
    To match at the beginning use a `^` prefix.
    To match at the end use a `$` suffix.

- **-p**, **-pid** _PID_

    Filters clients by process ID. Clients with a \_NET\_WM\_PID property equal
    to _PID_ are selected.

- **-G**, **-Gravity** _GRAVITY_

    Filters clients by the window gravity field of the WM\_NORMAL\_HINTS
    property.  Clients with a gravity equal to _GRAVITY_ are selected.
    If _GRAVITY_ starts with an exclamation mark then the filtering is
    inverted.

- **-L**, **-Layer** _LAYER_

    Filters clients by _GNOME window layer_, which can either be a layer
    name (see below) or a layer number.  If _LAYER_ starts with an
    exclamation mark then the filtering is inverted.

- **-S**, **-State** _STATE_

    Filters clients by _GNOME window state_. Clients which have at least
    a state of _STATE_ are selected.  The window state refers to details
    like **minized** or **maximized** and is explained below.  If _STATE_
    starts with an exclamation mark then the filtering is inverted.
    A question mark `?` filters clients with any bit set in _STATE_.

- **-W**, **-Workspace** _WORKSPACE_

    Filter clients by workspace. Workspace _WORKSPACE_ is either a
    workspace name or a workspace number counting from zero.
    If _WORKSPACE_ starts with an exclamation mark then the filtering is
    inverted.

- **-X**, **-Xinerama** _MONITOR_

    Limit clients by _RandR_/_Xinerama_ monitor. Only operate on
    clients which are displayed on _MONITOR_, where _MONITOR_ can
    be `All` for all monitors, `this` for the monitor where the
    active window is displayed, or a monitor number starting from zero.
    See the output of `randr` or `xinerama` below.

## GENERAL OPTIONS

The following options are identical for every IceWM command.

- **-d**, **-display** _DISPLAY_

    Specifies the X11 DISPLAY.  If unspecified, defaults to **$DISPLAY**.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# ACTIONS

**icesh** expects one or more action arguments.  There are two kinds of
actions: _window actions_ and _manager actions_. The first operates on
the selected windows. The second directly interacts with the **icewm**
window manager.

## WINDOW ACTIONS

The following actions affect the selected window or windows.

- **activate**

    Activate the window, aka. _to focus_.

- **close**

    Close the window.

- **kill**

    Terminate the window.

- **id**

    Print window identifiers for the selected windows.

- **pid**

    Print process identifiers for the selected windows.

- **list**

    Show window details, like geometry and names.

- **lower**

    Lower the window.

- **raise**

    Raise the window.

- **above**

    Stack the window above others.

- **below**

    Stack the window below others.

- **rollup**

    Rollup the specified window.

- **fullscreen**

    Set the window to fullscreen.

- **maximize**

    Maximize the window.

- **horizontal**

    Maximize the window only horizontally.

- **vertical**

    Maximize the window only vertically.

- **minimize**

    Minimize the window.

- **restore**

    Restore the window to normal.

- **hide**

    Make window hidden.

- **unhide**

    Undo window hidden.

- **skip**

    Don't show window on taskbar.

- **unskip**

    Do show window on taskbar.

- **resize** _WIDTH_ _HEIGHT_

    Resize window to _WIDTH_ by _HEIGHT_ window units.

- **sizeto** _WIDTH_ _HEIGHT_

    Resize window to _WIDTH_ by _HEIGHT_ pixels. If _WIDTH_ or _HEIGHT_
    ends with a percent sign `%`, then they refer to a percentage of the
    desktop work area. For instance, `sizeto 50% 100%`a resizes to half
    the desktop width and whatever height is available above or below the
    taskbar.

- **move** _X_ _Y_

    Move the selected window or windows to the screen position _X_ _Y_.
    To specify _X_ or _Y_ values relative to the right side or bottom side
    precede the value with an extra minus sign, like in `move -+10 --20`.

- **moveby** _X_ _Y_

    Displace window by _X_ _Y_ pixels.

- **center**

    Position window in the center of the desktop work area.

- **left**

    Position window against the left side of the desktop work area.

- **right**

    Position window against the right side of the desktop work area.

- **top**

    Position window against the top side of the desktop work area.

- **bottom**

    Position window against the bottom side of the desktop work area.

- **setIconTitle** _TITLE_

    Set the icon title to _TITLE_.

- **getIconTitle**

    Print the icon title.

- **setWindowTitle** _TITLE_

    Set the window title to _TITLE_.

- **getWindowTitle**

    Print the window title.

- **setGeometry** _GEOMETRY_

    Set the window geometry to _GEOMETRY_.

- **getGeometry**

    Print the window geometry.

- **setState** _MASK_ _STATE_

    Set the _GNOME window state_ to _STATE_.  Only bits selected by
    _MASK_ are affected.  See below for _STATE_ and _MASK_ symbols.

- **toggleState** _STATE_

    Toggle the _GNOME window state_ bits specified by the _STATE_
    expression.  See below for _STATE_ symbols.

- **getState**

    Print the _GNOME window state_ for the specified window.

- **setHints** _HINTS_

    Set the _GNOME window hints_ to _HINTS_. See below for symbols.

- **getHints**

    Print the _GNOME window hints_ for the specified window.

- **setLayer** _LAYER_

    Move the specified window to another _GNOME window layer_.
    See below for _LAYER_ symbols.

- **getLayer**

    Print the _GNOME window layer_ for the specified window.

- **setWorkspace** _WORKSPACE_

    Move the specified window to another workspace.  Select the root
    window to change the current workspace. If _WORKSPACE_ is `All`
    then the specified window becomes visible on all workspaces.
    Specify `this` for the current workspace.

- **getWorkspace**

    Print the workspace for the specified window.

- **opacity** \[_OPACITY_\]

    Print the window opacity if _OPACITY_ is not given,
    otherwise set the window opacity to _OPACITY_.

- **setTrayOption** _TRAYOPTION_

    Set the _IceWM tray option_ for the specified window to _TRAYOPTION_.
    See _IceWM tray options_, below, for _TRAYOPTION_ symbols.

- **getTrayOption**

    Print the _IceWM tray option_ for the specified window.

- **setNormalGravity** _GRAVITY_

    Set the window gravity field in the WM\_NORMAL\_HINTS property for the
    specified window to _GRAVITY_.  See below for _GRAVITY_ symbols.

- **getNormalGravity**

    Print the window gravity from the WM\_NORMAL\_HINTS property for the
    specified window.

- **setWindowGravity** _GRAVITY_

    Set the window gravity for the specified window to _GRAVITY_.
    See below for _GRAVITY_ symbols.

- **getWindowGravity**

    Print the window gravity for the specified window.

- **setBitGravity** _GRAVITY_

    Set the bit gravity> for the specified window to _GRAVITY_.
    See below for _GRAVITY_ symbols.

- **getBitGravity**

    Print the bit gravity for the specified window.

- **motif** \[**funcs** _FUNCTIONS_ \| **decor** _DECORATIONS_ \| **remove**\]

    Query, set or modify the `_MOTIF_WM_HINTS` property for the specified
    window.  Without arguments **motif** will show the current value, but
    only if the window has such a property. The property can be removed or
    reset with the **remove** argument. With **funcs** and **decor** individual
    fields of this property can be enabled or disabled. If _FUNCTIONS_ or
    _DECORATIONS_ starts with a minus or plus sign then the existing value
    is modified, otherwise it is set to the new value. Note that if `All`
    is set, then other set fields will be disabled and cleared fields will
    be enabled.

## MANAGER ACTIONS

The following actions control the IceWM window manager and therefore
do not require a window _select_ or _filter_ option:

- **listWorkspaces**

    List the names of all workspaces.

- **goto** _WORKSPACE_

    Change the current workspace to _WORKSPACE_.

- **workspaces** \[_COUNT_\]

    Print the number of workspaces if _COUNT_ is not given,
    otherwise set the number of workspaces to _COUNT_.

- **setWorkspaceName** _INDEX_ _NAME_

    Change the name of the workspace _INDEX_ to _NAME_, where _INDEX_ is
    a workspace number starting from zero.

- **setWorkspaceNames** _NAME_ \[_NAME_\]\*

    Change the workspace names to the list of _NAME_s.

- **desktop** \[_SHOWING_\]

    If _SHOWING_ is `1` then set `showing the desktop` mode.
    If _SHOWING_ is `0` then turn off `showing the desktop`.
    Print the current mode if _SHOWING_ is not given.

- **randr**

    Summarize the _RandR_ configuration.

- **xinerama**

    Summarize the _Xinerama_ configuration.

- **check**

    Print information about the current window manager, like name,
    version, class, locale, command, host name and pid.

- **clients**

    List all managed client windows, their titles and geometries.

- **shown**

    List all mapped client windows for the current desktop,
    their titles and geometries.

- **windows**

    List all toplevel windows, their titles and geometries.

- **systray**

    List applications which are managed by the IceWM system tray.

- **xembed**

    List application windows which are embedded using the _XEMBED_ protocol.
    This is another way to discover system tray applications.

- **logout**

    Let icewm execute the `LogoutCommand`.

- **reboot**

    Let icewm execute the `RebootCommand`.

- **shutdown**

    Let icewm execute the `ShutdownCommand`.

- **cancel**

    Let icewm cancel the logout/reboot/shutdown.

- **about**

    Let icewm show the about window.

- **windowlist**

    Let icewm show the window list window.

- **restart**

    Let icewm restart itself.

- **suspend**

    Let icewm execute the `SuspendCommand`.

- **winoptions**

    Let icewm reload the `winoptions`.

- **guievents**

    Monitor the **ICEWM\_GUI\_EVENT** property and report all changes.

- **colormaps**

    Monitor which colormap is installed.

- **runonce** _program_ \[_arguments..._\]

    This action is meant to be used together with the **-class** option.
    Only if no window is matched by _WM\_CLASS_ then
    _program_ \[_arguments..._\] is executed.

- **sync**

    Synchronize with the IceWM window manager. That is, wait for icewm to
    process all previous actions.

- **symbols**

    List all named symbols.

## EXPRESSIONS

Some of the window actions require one or two _EXPRESSION_ arguments.

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
        Rollup                (32)
        All                 (1023)

    These symbols are used with the _MASK_ and _STATE_ arguments to the
    `setState` and `toggleState` actions. Some additional states include:
    Above, Below, Urgent and Fullscreen.

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

- _Gravity symbols_

    Named symbols for window and bit gravity (numeric range: 0-10):

        ForgetGravity         (0)
        NorthWestGravity      (1)
        NorthGravity          (2)
        NorthEastGravity      (3)
        WestGravity           (4)
        CenterGravity         (5)
        EastGravity           (6)
        SouthWestGravity      (7)
        SouthGravity          (8)
        SouthEastGravity      (9)
        StaticGravity         (10)

- _Motif functions_

        All                  (1)
        Resize               (2)
        Move                 (4)
        Minimize             (8)
        Maximize             (16)
        Close                (32)

- _Motif decorations_

        All                  (1)
        Border               (2)
        Resize               (4)
        Title                (8)
        Menu                 (16)
        Minimize             (32)
        Maximize             (64)

# EXAMPLES

List all workspace names:

    icesh listWorkspaces

Example output:

    workspace #0: `main'
    workspace #1: `web'
    workspace #2: `doc'
    workspace #3: `dev'

Close terminal work and activate terminal fun.

    icesh -c work.XTerm close -a -c fun.XTerm activate

Print opacity for all xterms.

    icesh -c XTerm opacity

Change opacity for all xterms.

    icesh -c XTerm opacity 84

Move all windows on workspace "Top" to the current workspace.

    icesh -W "Top" setWorkspace "this"

Restore all hidden clients, minimize all clients on the current
workspace and activate Firefox.

    icesh -S hidden restore -a -W "this" minimize -a -c Firefox activate

Resize the focused window to occupy the right half of the desktop area.

    icesh -f sizeto 49% 100% sync top sync right sync raise activate

# ENVIRONMENT

The following environment variables are examined by **icesh**:

- **DISPLAY**

    The display to use if the **-display** option is unspecified.

# COMPLIANCE

While **icesh** is largely compliant with the GNOME WinWM/WMH
specification, it only minimally supports NetWM/EWMH.
Some commands, like tray options and manager actions, are specific
to IceWM.

# SEE ALSO

[icewm(1)](icewm), [wmctrl(1)](https://manned.org/wmctrl.1), [xdotool(1)](https://manned.org/xdotool.1), [xprop(1)](https://manned.org/xprop.1), [xwininfo(1)](https://manned.org/xwininfo.1).

# BUGS

**icesh** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
