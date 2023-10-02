---
title: "icesh(1)"
---
## NAME

    icesh - control window properties and the IceWM window manager

## SYNOPSIS

- **icesh** _OPTIONS\|ACTIONS_+

## DESCRIPTION

**icesh** provides two types of commands:

1. Commands to directly interact with icewm:

    These are listed in the section "MANAGER ACTIONS" below.
    They are easy to use, because they don't require to select one
    or more windows. For example, `icesh restart` will restart
    icewm and `icesh clients` lists the applications that
    are managed by icewm.

2. Commands that operate on a selection of windows:

    See the section `WINDOW ACTIONS` below. For example, `icesh close`
    is a request to close a window, but which window? Now icesh
    will turn the mouse pointer into a crosshair. Click on a window
    and a close request will be sent to that application.

    The power of icesh lies in its ability to programmatically
    select one or more windows and operate on that selection.
    This can be used in scripts and in [icewm-keys(5)](icewm-keys)
    to define your own window management hotkeys.  For example, to
    immediately close all xterm windows do `icesh -c xterm close`.

    There are a dozen `SELECT OPTIONS` to select windows.  They start
    with a '-' or a '+'.  The '-' starts a new selection, while the '+'
    adds more windows to an existing selection.

    This selection of windows can be reduced by `FILTER OPTIONS`.
    These remove unwanted windows from the current selection.
    Multiple filter options can be given. For example,
    `icesh -c xterm -W this close` will close only those xterms
    that are shown on the current workspace. The xterms on other
    workspaces are filtered out by the `-W this` filter option.

There is no limit to the number of commands, selections, filters
and actions that you can give to a single icesh command.
They are processed and evaluated one by one from left to right.
This makes icesh a small declarative programming language.
Have a look at some examples near the end of this document.

## OPTIONS

**icesh** recognizes the following options:

## SELECT OPTIONS

Select options specify the window or windows to which subsequent
actions apply. If none is given, but an action does require a window,
then a selection crosshair is shown to select the desired window
interactively. The manager actions do not require window options.

The following options _select_ one or more client windows.
If needed, they can be repeated for successive actions.

- **-a**, **-all**

    Selects all client windows of the window manager.

- **-f**, **-focus**, **+f**, **+focus**

    Selects the application window that is currently focused.
    The option with minus sign replaces the existing selection with
    the focused window. With a plus sign the focused window is added to
    an existing selection.

- **+g**, **+group**

    Extend the current selection with client windows that
    belong to the same application window group.

- **-r**, **-root**, **+r**, **+root**

    Selects the root window.
    The option with minus sign replaces the existing selection with
    the root window. With a plus sign the root window is added to
    an existing selection.

- **-s**, **-shown**

    Selects all client windows that are on the current workspace.

- **-t**, **-top**

    Selects all toplevel windows from the display unconditionally.
    This includes windows that have never been mapped and windows
    with the override redirect bit set to evade management.

- **-w**, **-window**, **+w**, **+window** _WINDOW\_ID_

    Specifies the identifier of the window, _WINDOW\_ID_, for which the
    action applies.  Special identifiers are **root** for the root window
    and **focus** for the currently focused window.
    The option with minus sign replaces the existing selection.
    With a plus sign the window is added to an existing selection.

- **-x**, **-xembed**

    Selects all windows that are embedded using the _XEMBED_ protocol.

- **+c**, **+class** _CLASS_

    Extend the current selection with client windows that have a
    _WM\_CLASS_ property equal to _CLASS_. This is the resource
    instance and class name.  If _CLASS_ contains a period, only
    windows with exactly the same _WM\_CLASS_ property are matched.
    If there is no period, windows of the same class and windows
    of the same instance are selected.

- **+C**, **+Class**

    Extend the current selection with client windows that
    have a _WM\_CLASS_ property _similar_ to the already
    selected set of windows.

- **-D**, **-Dockapps**

    Selects all Dockapp applications that are managed by icewm.

- **+P**, **+Pid**

    Extend the current selection with client windows that have
    the same process identifier as one of the selected windows.

- **-T**

    Selects the IceWM taskbar.

## FILTER OPTIONS

The following options _filter_ the currently selected set of windows.
If no previous _select_ option was given then a **-all** option is
implicitly assumed to filter all client windows.

- **-c**, **-class** _CLASS_

    Filters the set of windows on their _WM\_CLASS_ property.  This is
    the resource instance and class name. If _CLASS_ contains a period,
    only windows with exactly the same _WM\_CLASS_ property are matched.
    If there is no period, windows of the same class and windows of the
    same instance (aka. _-name_) are selected.

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

- **-u**, **-unmapped**

    Filter clients and keep those that are currently not viewable.
    These are hidden, minimized, rolled-up, or on another workspace.

- **-v**, **-viewable**

    Filter clients and keep only those that are currently viewable.
    These clients are mapped on the current workspace.

- **-G**, **-Gravity** _GRAVITY_

    Filters clients by the window gravity field of the WM\_NORMAL\_HINTS
    property.  Clients with a gravity equal to _GRAVITY_ are selected.
    If _GRAVITY_ starts with an exclamation mark then the filtering is
    inverted.

- **-L**, **-Layer** _LAYER_

    Filters clients by _GNOME window layer_, which can either be a layer
    name or a layer number. See EXPRESSIONS below. If _LAYER_ starts with
    an exclamation mark then the filtering is inverted.

- **-N**, **-Netstate** _STATE_

    Filters clients by _EWMH window state_. Clients that have at
    least an EWMH window state of _STATE_ are selected.  This state
    refers to details like **MINIZED** or **MAXIMIZED**. See EXPRESSIONS
    below. If _STATE_ starts with an exclamation mark then the filtering
    is inverted.  A question mark `?` filters clients with any bit set
    in _STATE_.

- **-P**, **-Property** _PROP\[=value\]_

    Filters clients by property. Clients that have a property _PROP_
    are selected. If the optional _value_ is given, the match succeeds
    only if _PROP_ is a string, window, cardinal, or atom, with a value
    equal to _value_.  The filtering is inverted if _PROP_ starts with
    an exclamation mark.

- **-R**, **-Role** _ROLE_

    Filters clients by WM\_WINDOW\_ROLE. Clients that have a WM\_WINDOW\_ROLE
    property value equal to _ROLE_ are selected.  The filtering is inverted
    if _ROLE_ starts with an exclamation mark.

- **-W**, **-Workspace** _WORKSPACE_

    Filter clients by workspace. Workspace _WORKSPACE_ is either a
    workspace name, or a workspace number counting from zero, or the word
    `this` for the current workspace, or the word `All` for all workspaces.
    If _WORKSPACE_ starts with an exclamation mark then the filtering is
    inverted.

- **-X**, **-Xinerama** _MONITOR_

    Limit clients by _RandR_/_Xinerama_ monitor. Only operate on
    clients that are displayed on _MONITOR_, where _MONITOR_ can
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

- **-q**, **--quiet**

    Don't complain if no matching windows could be found.

## ACTIONS

**icesh** expects one or more action arguments.  There are two kinds of
actions: _window actions_ and _manager actions_. The first operates on
the selected windows. The second directly interacts with the **icewm**
window manager.

## WINDOW ACTIONS

The following actions affect the selected window or windows.

- **activate**

    Activate the window, aka. _to focus_.

- **close**

    Send a close request to the client that created the window.

- **kill**

    Force an immediate close down of the client that created the window.

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

    Hide the window.

- **unhide**

    Reveal the window.

- **skip**

    Don't show the window on the taskbar.

- **unskip**

    Do show the window on the taskbar.

- **sticky**

    Show the window on all workspaces.

- **unsticky**

    Show the window on just one workspace.

- **urgent**

    Set the urgent flag to flash the task button.

- **resize** _WIDTH_ _HEIGHT_

    Resize window to _WIDTH_ by _HEIGHT_ window units.  For text based
    applications like terminals, a window unit is the size of a single
    character cell.

- **sizeto** _WIDTH_ _HEIGHT_

    Resize window to _WIDTH_ by _HEIGHT_ pixels. If _WIDTH_ or _HEIGHT_
    ends with a percent sign `%`, then they refer to a percentage of the
    desktop work area. For instance, `sizeto 50% 100%` resizes to half
    the desktop width and whatever height is available above or below the
    taskbar.

- **sizeby** _WIDTH_ _HEIGHT_

    Resize window by _WIDTH_ by _HEIGHT_ pixels. If _WIDTH_ or _HEIGHT_
    ends with a percent sign `%`, then they refer to a percentage of the
    current window size. For instance, `sizeby 50% 200` increases the width
    by 50% and increases the height by 200 pixels.

- **move** _X_ _Y_

    Move the selected window or windows to the screen position _X_ _Y_.
    To specify _X_ or _Y_ values relative to the right side or bottom side
    precede the value with an extra minus sign, like in `move -+10 --20`.

- **moveby** _X_ _Y_

    Displace window by _X_ _Y_ pixels.

- **center**

    Position the window in the center of the desktop work area.

- **left**

    Position the window against the left side of the desktop work area.

- **right**

    Position the window against the right side of the desktop work area.

- **top**

    Position the window against the top side of the desktop work area.

- **bottom**

    Position the window against the bottom side of the desktop work area.

- **setIconTitle** _TITLE_

    Set the icon title to _TITLE_.

- **getIconTitle**

    Print the icon title.

- **setWindowTitle** _TITLE_

    Set the window title to _TITLE_.

- **getWindowTitle**

    Print the window title.

- **setGeometry** _GEOMETRY_

    Set the window geometry to _GEOMETRY_.  This geometry should be
    specified in a format that can be parsed by [XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html).
    Negative offsets are with respect to the bottom or right side of
    the screen.  Use `+-` for a truly negative position.

- **getGeometry**

    Print the window geometry.

- **setClass** _CLASS_

    Set the resource name and class to _CLASS_, which should be a resource
    name and a resource class connected by a dot. To preserve either the
    existing name or class, use a percentage sign for that part.

- **getClass**

    Print the resource name and class.

- **netState** _\[STATE\]_

    If _STATE_ is omitted then it shows the _EWMH window state_.
    If _STATE_ starts with a `+` then flags in _STATE_ are appended to
    the existing _EWMH window state_.  If _STATE_ starts with a `-`
    then flags in _STATE_ are removed from the existing _EWMH window
    state_.  If _STATE_ starts with a `^` then flags in _STATE_ are
    toggled with respect to the existing _EWMH window state_.
    If _STATE_ starts with a `=` then the _EWMH window state_
    is set to _STATE_. See EXPRESSIONS below. A list of _EWMH flags_
    can be found in the output of `icesh symbols`.

- **setLayer** _LAYER_

    Move the specified window to another _window layer_.
    See EXPRESSIONS below for a list of _LAYER_ symbols.

- **getLayer**

    Print the _window layer_ for the specified window.

- **setWorkspace** _WORKSPACE_

    Move the specified window to another workspace.  Select the root
    window to change the current workspace. If _WORKSPACE_ is `All`
    then the specified window becomes visible on all workspaces.
    Specify `this` for the current workspace, `next` for the subsequent
    workspace or `prev` for the preceding workspace.

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
    is set, other set fields are disabled and cleared fields are enabled.

- **borderless**

    Hide the frame borders and title.

- **bordered**

    Show the frame borders and title.

- **denormal**

    Remove the WM\_NORMAL\_HINTS property, if it exists.  This lifts
    font-size restrictions on resizing, especially for terminals.

- **prop** _PROPERTY_

    Print the value of property _PROPERTY_, if it is present.

- **properties**

    Print all properties and their values.

- **frame**

    Print the identifier of the window frame.

- **extents**

    Print the window identifier and the frame border sizes: left, right,
    top and bottom.

- **focusmodel**

    Print the ICCCM focus model as advertised by the client window.
    This is either Locally, Passive, Globally or NoInput.

- **override** \[_0\|1_\]

    Print the override redirect status for the window, or if either 0 or 1
    is given, then disable or enable the override redirect status.

- **tabto** _label_

    Move the windows as tabs to a frame that has `frame` label _label_.
    Such a frame is created if needed.

- **untab**

    Move each window to its own frame, if it is currently tabbed.

- **loadicon** `image.pam`

    Load an icon from file, which must be in the PAM image format,
    with dimensions at most 256, a depth of 4, and type _RGB\_ALPHA_.

- **saveicon** `file000.pam`

    Save an icon to a new file in the PAM image format. Digits are
    increased to generate a unique new filename for each window.

- **click** _window-x_ _window-y_ _button_

    Send a button press and release event at position (_window-x_,
    _window-y_). A negative position is relative to the bottom right
    corner. The mouse pointer is warped to the position before sending
    the events. The button number should be between 1 and 5 inclusive.

- **monitors** _top_ _bottom_ _left_ _right_

    This sets the monitors to use for fullscreen.
    Top, bottom, left, and right are indices of the _icesh xinerama_ command.

- **spy**

    Observe the selected windows and report any changes. This includes
    focus, visibility, position, size and all window properties.
    To monitor all of the protocol request messages that client applications
    may send to icewm, also spy on the root window.

- **stacking**

    Sort the list of windows from topmost to bottom-most.

- **reverse**

    Reverse the order of the list of windows.

## MANAGER ACTIONS

The following actions control the IceWM window manager and therefore
do not require a window _select_ or _filter_ option:

- **listWorkspaces**

    List the names of all workspaces.

- **current**

    Show the number and name of the current workspace.

- **goto** _WORKSPACE_

    Change the current workspace to _WORKSPACE_. Specify `next` for the
    subsequent workspace or `prev` for the preceding workspace.

- **workspaces** \[_COUNT_\]

    Print the number of workspaces if _COUNT_ is not given,
    otherwise set the number of workspaces to _COUNT_.

- **setWorkspaceName** _INDEX_ _NAME_

    Change the name of the workspace _INDEX_ to _NAME_, where _INDEX_ is
    a workspace number starting from zero.

- **setWorkspaceNames** _NAME_ \[_NAME_\]\*

    Change the workspace names to the list of _NAME_s.

- **addWorkspace** _NAME_

    Create a new workspace with name _NAME_.

- **desktop** \[_SHOWING_\]

    If _SHOWING_ is `1` then set `showing the desktop` mode.
    If _SHOWING_ is `0` then turn off `showing the desktop`.
    Print the current mode if _SHOWING_ is not given.

- **workarea**

    Print the dimensions of the work area for the current workspace.
    This is the desktop, but minus space occupied by dock and panel windows.

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

    List applications that are managed by the IceWM system tray.

- **xembed**

    List application windows that are embedded using the _XEMBED_ protocol.
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

- **hibernate**

    Let icewm execute the `HibernateCommand`.

- **winoptions**

    Let icewm reload the `winoptions`.

- **keys**

    Let icewm reload the `keys` file.

- **refresh**

    Let icewm refresh the desktop background.

- **guievents**

    Monitor the **ICEWM\_GUI\_EVENT** property and report all changes.
    Hit `Ctrl+C` to abort this and continue with the next command.

- **delay** \[_time_\]

    Stop execution for _time_ or 0.1 seconds.

- **runonce** _program_ \[_arguments..._\]

    This action is meant to be used together with the **-class** option.
    Only if no window is matched by _WM\_CLASS_ then
    _program_ \[_arguments..._\] is executed.

- **loop** \[_count_\]

    Loop back to the beginning of the command and repeat. The optional
    _count_ limits the number of repetitions.

- **pick**

    Choose a window by a mouse button click.

- **sync**

    Synchronize with the IceWM window manager. That is, wait for icewm to
    process all previous actions.

- **symbols**

    List all named symbols.

## CONDITIONALS

Icesh supports `if-then-else` expressions. The full syntax is:

    if selection
    then
        actions
    elif selection
    then
        actions
    else
        actions
    end

Where `selection` is a sequence of selection and filtering options,
which evaluates to **true** when it is non-empty. That is, if one or more
windows fulfilled the condition. If it is empty, then its `actions`
clause is ignored and the subsequent `elif` or `else` clause is tried
or taken. Each clause is optional.

Whenever a selection condition evaluates to **false**, the window selection
that existed before the `if` clause is immediately restored.  This also
happens after an `end` clause.

## EXPRESSIONS

Some of the window actions require one or two _EXPRESSION_ arguments.

- **EXPRESSION** ::= _SYMBOL_ \| _EXPRESSION_ { `+` \| `\|` }
_SYMBOL_

Each _SYMBOL_ may be from one of the following applicable domains:

- _Window layer_

    Named symbols of the domain _Window layer_ (numeric range: 0-15):

        Desktop                (0)
        Below                  (2)
        Normal                 (4)
        OnTop                  (6)
        Dock                   (8)
        AboveDock             (10)
        Menu                  (12)
        Fullscreen            (14)
        AboveAll              (15)

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

- _EWMH window state symbols_

    Named symbols of the domain _EWMH state_ (numeric range:
    0-8191):

        ABOVE                 (1)
        BELOW                 (2)
        DEMANDS_ATTENTION     (4)
        FOCUSED               (8)
        FULLSCREEN            (16)
        HIDDEN                (32)
        MAXIMIZED_HORZ        (64)
        MAXIMIZED_VERT        (128)
        MODAL                 (256)
        SHADED                (512)
        SKIP_PAGER            (1024)
        SKIP_TASKBAR          (2048)
        STICKY                (4096)

## EXAMPLES

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

    icesh -N HIDDEN restore -a -W "this" minimize -a -c Firefox activate

Resize the focused window to occupy the right half of the desktop area.

    icesh -f sizeto 49% 100% top right raise

Toggle the frame border of the focused window.

    if icesh -f motif | grep -q 'decor:$'; then \
        icesh -f motif decor All; else icesh -f motif decor ""; fi

Here is a different solution using conditionals.

    icesh -f if -P _NET_FRAME_EXTENTS=0 then bordered else borderless

Here is a conditional to either toggle the visibility of a roxterm
that has a WM\_ROLE value of `special` or start it with **runonce**.

    icesh if -c roxterm.Roxterm -R special then \
        if -v then hide \
        elif -u then setWorkspace this activate end \
        else runonce roxterm --role=special

Collect all urxvt terminals from the fourth workspace in a single frame
on the current workspace.

    icesh -W 3 -c urxvt tabto myfunnyname

Use the loop construct conditionally to wait for a certain window to
appear.

    icesh -t if -n Tooltip then list else delay 0.05 loop end

## ENVIRONMENT

- **DISPLAY**

    The default display.

## EXIT STATUS

- **0**

    The last action completed successfully.

- **1**

    The last action completed unsuccessfully, or no window met the condition.

- **2**

    A conditional has invalid syntax.

- **3**

    The display could not be opened.

- **4**

    The X server reports an error while processing a request.

## COMPLIANCE

**icesh** is largely compliant with the EWMH and ICCCM specifications.
Some commands, like manager actions, are specific to IceWM.

## SEE ALSO

[icewm(1)](icewm), [wmctrl(1)](https://manned.org/wmctrl.1), [xdotool(1)](https://manned.org/xdotool.1), [xprop(1)](https://manned.org/xprop.1),
[xwininfo(1)](https://manned.org/xwininfo.1), [XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html).

## BUGS

Please report bugs at [Github](https://github.com/bbidulock/icewm/issues).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
