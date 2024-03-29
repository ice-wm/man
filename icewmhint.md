---
title: "icewmhint(1)"
---
## NAME

icewmhint - set IceWM hints by window class and instance

## SYNOPSIS

**icewmhint** _CLASS_**.**_INSTANCE_ _OPTION_ _VALUE_ ...

## DESCRIPTION

**icewmhint** is a utility for passing IceWM hints to [icewm(1)](icewm).
**icewm** uses these hints for the first _X11 client_ which is
subsequently started. They take precedence over hints from
the [icewm-winoptions(1)](icewm-winoptions) file.

A hint is a triplet consisting of a _class.instance_, an
_IceWM winoption_ and its value. Multiple hints can be given per
invocation of **icewmhint**.

The hints are communicated over the `_ICEWM_WINOPTHINT` property on
the root window.  **icewmhint** appends hints to this property, while
**icewm** removes the property after reading it.

## OPTIONS

**icewmhint** recognizes the following options:

## COMMAND OPTIONS

Only one command option can be specified per invocation.  If no command
option is specified, argument parsing and processing is performed.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## GENERAL OPTIONS

- **-d**, **--display**=_DISPLAY_

    Specifies the X11 DISPLAY. If unspecified, defaults to **$DISPLAY**.

## ARGUMENTS

The following three arguments are required for each hint.

- _CLASS_**.**_INSTANCE_

    Specifies the ICCCM 2.0 **WM\_CLASS** property in terms of resource class
    and resource name separated by a period (`.`).  For example:
    `XTerm.xterm`. Just the resource class or resource name without a dot
    is also acceptable, like `XTerm` or `xterm`.

- _OPTION_

    Specifies the _OPTION_ to affect.

- _VALUE_

    Gives the _VALUE_ for the option.

Multiple hints can be given.

## GENERAL OPTION ARGUMENTS

- **icon** _NAME_

    Specifies the icon name for windows of _CLASS_**.**_INSTANCE_.
    _NAME_ should be the name of the icon.  [icewm(1)](icewm) will use its
    usual method to locate the icon.  The default is the name provided
    by window manager hints.

- **workspace** _WORKSPACE_

    Specifies the workspace on which a window of _CLASS_**.**_INSTANCE_
    will be initially placed.  The default is the current workspace.
    _WORKSPACE_ should be a workspace number counting from 0.

- **geometry** _GEOMETRY_

    Specifies the initial geometry for windows of the given
    _CLASS_**.**_INSTANCE_.  _GEOMETRY_ must be a geometry that can be
    parsed by [XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html).  The default is the geometry provided by
    window manager hints.

- **order** _NUMBER_

    The sorting order of task buttons and tray icons. The default value is
    zero. Increasing positive values go farther right, while decreasing
    negative values go farther left. The order option applies to the task
    pane, the tray pane and the system tray.

- **opacity** _NUMBER_

    Set the \_NET\_WM\_WINDOW\_OPACITY property if _NUMBER_ is a value between
    1 and 100. _NUMBER_ is interpreted as percentage of maximum opaqueness.

- **layer** {_LAYER_\|_NUMBER_}

    This command option specifies the layer to be associated with a
    _CLASS_**.**_INSTANCE_.  The default is the `Normal` layer.  _VALUE_
    is either a layer number or a symbolic layer name.  Symbolic
    layer names are:

        Desktop     (0)  Desktop window.
        Below       (2)  Below the default layer.
        Normal      (4)  Default layer for windows.
        OnTop       (6)  Above the default layer.
        Dock        (8)  Docked windows at edge of screen.
        AboveDock  (10)  Windows above the dock.
        Menu       (12)  The layer for menu's.
        Fullscreen (14)  When fullscreen and focused.
        AboveAll   (15)  Always above anything.

- **tray** {**Ignore**\|**Minimized**\|**Exclusive**\|_NUMBER_}

    Specifies the tray handling to be applied to windows with
    _CLASS_**.**_INSTANCE_.  This option is specific to [icewm(1)](icewm) and
    sets the `_ICEWM_TRAY` property associated with the window.
    The default is `Ignore`.  _VALUE_ can be an option number
    or a symbolic name as follows:

        Ignore     (0)  only in task list.
        Minimized  (1)  icon in tray, task list unminimized.
        Exclusive  (2)  only in tray, not in task list.

- **frame** _label_ (default: none)

    All windows with the same frame label become tabs in a single frame.

## FUNCTION OPTION ARGUMENTS

Specifies which functions are disabled or enabled (0/1) for windows with
_CLASS_**.**_INSTANCE_.  All functions have a default value of enabled
(1) unless overridden by the application.  The Motif-like functions are
as follows:

    fClose     can be closed:        (default: 1).
    fHide      can be hidden:        (default: 1).
    fMaximize  can be maximized:     (default: 1).
    fMinimize  can be minimized:     (default: 1).
    fMove      can be moved:         (default: 1).
    fResize    can be resized:       (default: 1).
    fRollup    can be shaded:        (default: 1).

## DECOR OPTION ARGUMENTS

Specifies which decorations are disabled or enabled (0/1) for windows
with _CLASS_**.**_INSTANCE_.  All decor options have a default value
of enabled (1) unless overridden by the application. The Motif-like
decorations are as follows:

    dBorder    has border:           (default: 1).
    dClose     has close button:     (default: 1).
    dDepth     has depth button:     (default: 1).
    dHide      has hide button:      (default: 1).
    dMaximize  has maximize button:  (default: 1).
    dMinimize  has minimize button:  (default: 1).
    dResize    has resize grips:     (default: 1).
    dRollup    has shade button:     (default: 1).
    dSysMenu   has window menu:      (default: 1).
    dTitleBar  has title bar:        (default: 1).

## FEATURE OPTION ARGUMENTS

Specifies which advanced features to be enabled/disabled (1/0) for
windows with _CLASS_**.**_INSTANCE_.  All advanced features have a
default value of disabled (0) unless overridden by the application.  The
advanced features are as follows:

    allWorkspaces             on all workspaces.
    appTakesFocus             let application take focus.
    doNotCover                limits workspace if sticky.
    doNotFocus                do not focus.
    doNotManage               do not manage.
    forcedClose               no close dialog.
    fullKeys                  provided more keys.
    ignoreNoFocusHint         focus even no-input.
    ignorePagerPreview        do not show in pager preview.
    ignorePositionHint        place automatically.
    ignoreQuickSwitch         not on quick switch.
    ignoreTaskBar             not on task bar.
    ignoreUrgentHint          ignore urgent hints.
    ignoreWinList             not on window list.
    ignoreActivationMessages  only user can focus window.
    ignoreOverrideRedirect    ignore the override redirect flag.
    noFocusOnAppRaise         no focus on raise.
    noFocusOnMap              do not focus when mapped.
    noIgnoreTaskBar           on task bar.
    startClose                close the window immediately.
    startFullscreen           start full screen.
    startMaximized            start maximized.
    startMaximizedHorz        start maximized horizontal.
    startMaximizedVert        start maximized vertical.
    startMinimized            start minimized.

## EXAMPLE

    # Here is how to preload an invisible background process of chromium
    # on the fourth workspace which is only visible on the Window List.

    icewmhint Chromium-browser startMinimized 1 \
              Chromium-browser workspace 3 \
              Chromium-browser ignorePagerPreview 1 \
              Chromium-browser ignorePositionHint 1 \
              Chromium-browser ignoreTaskBar 1 \
              Chromium-browser ignoreQuickSwitch 1 \
              Chromium-browser ignoreUrgentHint 1 \
              Chromium-browser noFocusOnAppRaise 1
    chromium

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
