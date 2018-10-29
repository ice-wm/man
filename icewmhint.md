---
title: "icewmhint(1)"
---
# NAME

    icewmhint - set IceWM hints by window class and instance

# SYNOPSIS

**icewmhint** \[_CLASS_**.**_INSTANCE_\] _OPTION_ _VALUE_

# DESCRIPTION

**icewmhint** is a simple utility for passing IceWM hints to [icewm(1)](icewm.md)
by window class and instance.  Unlike tools that use WMH or EWMH, such
as [icesh(1)](icesh.md), [wmctrl(1)](https://manned.org/wmctrl.1) and [xdotool(1)](https://manned.org/xdotool.1), **icewmhint** uses a
special property, `_ICEWM_WINOPHINT`, on the root window to pass
special hints to [icewm(1)](icewm.md).

# OPTIONS

**icesh** recognizes the following options:

## COMMAND OPTIONS

Command options are mutually exclusive.  Only one command option can be
specified per invocation.  If no command option is specified, argument
parsing and processing is performed.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## GENERAL OPTIONS

**icewmhint** has not general options: all information is passed using
non-option arguments.

# ARGUMENTS

The following arguments are required:

- \[_CLASS_**.**_INSTANCE_\]

    Specifies the ICCCM 2.0 **WM\_CLASS** property in terms of resource name
    and resource class separated by a period (`.`).  For example:
    `XTerm.xterm`.  This argument must be specified for all commands
    affecting client windows.

- _OPTION_ _VALUE_

    Specifies the _OPTION_ to affect and the _VALUE_ that goes with the
    option.  Options and their arguments are as follows:

## GENERAL OPTION ARGUMENTS

General option arguments are normally associated with GNOME WinWM/WMH
hints (except for the tray option argument).

- **icon** _NAME_

    Specifies the icon name for windows of _CLASS_**.**_INSTANCE_.
    _NAME_ should be the name of the icon.  [icewm(1)](icewm.md) will use is
    usual method to find the icon.  The default is the name provided by
    window manager hints.

- **workspace** _WORKSPACE_

    Specifies the workspace on which a window of _CLASS_**.**_INSTANCE_
    will be initially placed.  The default is to place the window on the
    current workspace.  _WORKSPACE_ should be a numeric workspace
    number (counting from 0).

- **geometry** _GEOMETRY_

    Specifies the initial geometry for windows of the given
    _CLASS_**.**_INSTANCE_.  _GEOMETRY_ must be a geometry that can be
    parsed by [XParseGeometry(3)](https://manned.org/XParseGeometry.3).  The default is the geometry provided by
    window manager hints.

- **layer** {**Desktop**\|**Below**\|**Normal**\|**OnTop**\|**Dock**\|**AboveDock**\|**Menu**\|_NUMBER_}

    The layer is a similar concept to the layer specified by GNOME/WMH and
    implied by NetWM/EWMH.  It is in this case however specific to
    [icewm(1)](icewm.md).

    The command option specifies the layer to be associated with an
    _CLASS_**.**_INSTANCE_.  The default is the `Normal` layer.  _VALUE_
    is either a numeric layer _NUMBER_ or a symbolic layer name.  Symbolic
    layer names are one of the following:

        Desktop    (0)  desktop window layer.
        Below      (2)  below normal windows.
        Normal     (4)  default window layer.
        OnTop      (6)  above normal windows.
        Dock       (8)  docks (panels and edge displays).
        AboveDock (10)  above docks.
        Menu      (12)  above everything else.

- **tray** {**Ignore**\|**Minimized**\|**Exclusive**\|_NUMBER_}

    Specifies the tray handling to be applied to windows with
    _CLASS_**.**_INSTANCE_.  This option is specific to [icewm(1)](icewm.md) and
    sets the `_ICEWM_TRAY` property associated with the window.
    The default is `Ignore`.  _VALUE_ can be a numerical option _NUMBER_
    or a symbolic name as follows:

        Ignore     (0)  only in task list.
        Minimized  (1)  icon in tray, task list unminimized.
        Exclusive  (2)  only in tray, not in task list.

## FUNCTION OPTION ARGUMENTS

Specifies which functions are disabled/enabled (0/1) for windows with
_CLASS_**.**_INSTANCE_.  All function options have a default value of
enabled (1) unless overridden by the application.  The Motif-like
functions are as follows:

    fClose     can be closed:        (default: 1).
    fHide      can be hidden:        (default: 1).
    fMaximize  can be maximized:     (default: 1).
    fMinimize  can be minimized:     (default: 1).
    fMove      can be moved:         (default: 1).
    fResize    can be resized:       (default: 1).
    fRollup    can be shaded:        (default: 1).

## DECOR OPTION ARGUMENTS

Specifies which decorations are disabled/enabled (0/1) for windows with
_CLASS_**.**_INSTANCE_.  All decor options have a default value of
enabled (1) unless overridden by the application. The Motif-like
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
    forcedClose               no close dialog.
    fullKeys                  provided more keys.
    ignoreNoFocusHint         focus even no-input.
    ignorePositionHint        place automatically.
    ignoreQuickSwitch         not on quick switch.
    ignoreTaskBar             not on task bar.
    ignoreUrgentHint          ignore urgent hints.
    ignoreWinList             not on window list.
    noFocusOnAppRaise         no focus on raise.
    noFocusOnMap              do not focus when mapped.
    noIgnoreTaskBar           on task bar.
    nonICCCMconfigureRequest  more configure requests.
    startFullscreen           start full screen.
    startMaximized            start maximized.
    startMaximizedHorz        start maximized horizontal.
    startMaximizedVert        start maximized vertical.
    startMinimized            start minimized.

# BUGS

**icewmhint** had no known bugs at the time of release.  Please report bugs
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
