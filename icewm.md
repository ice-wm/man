---
title: "icewm(1)"
---
# NAME

    icewm - lightweight X11 window manager

# SYNOPSIS

**icewm** \[_OPTIONS_\]

# DESCRIPTION

**icewm** is a lightweight window manager for the X11 window system.  It
aims to be small, fast and familiar to new users.  **icewm** is called a
re-parenting window manager, because it draws small frames around
application windows.  Windows are manipulated via the mouse by dragging
or resizing this frame.  It is also called a stacking window manager,
because windows can overlap.  Many windows may exist, some hidden behind
others, while interaction takes place with the currently visible ones.
**icewm** supports a configurable number of virtual desktops.  It
provides a task bar for monitoring applications and a pager to switch
between desktops.  **icewm** is largely compliant with the ICCCM 2.0,
WinWM/WMH and NetWM/EWMH window manager specifications.

**icewm** was originally designed to emulate the look of Motif, OS/2 Warp
4, OS/2 Warp 3 and Windows 95.  Since it has a theme engine other styles
are possible.  The installation comes with several configured themes.  A
menu allows to choose between themes.

Generally, it tries to make all functions available by both keyboard and
mouse.  Configuration is very good through various preferences files.
However, configuring is not required: it works fine out of the box.

## PROGRAMS

The **icewm** package includes several programs:

- [icewm(1)](icewm)

    The actual window manager. It positions application windows on screen
    and decorates them with borders. It gives input focus to the current
    active application. **icewm** supports different focus modes, which are
    explained below. It draws a small task bar at the bottom of the screen,
    which gives easy access to programs, to virtual desktops, to active
    applications, and to a small set of monitoring applets.

- [icewmbg(1)](icewmbg)

    The background setting application. It can assign plain background color
    or images in different formats to the X background.  Each work space can
    have its own background.  It supports semi-transparency. Semitransparent
    background image and colour can be configured. When the background image
    has changed then [icewmbg(1)](icewmbg) can be notified to update the background.
    Multi-head monitor setups are fully supported.  This program should be
    started before **icewm**.  See the [icewmbg(1)](icewmbg) man page for details.

- [icewm-session(1)](icewm-session)

    [icewm-session(1)](icewm-session) is the preferred program to start the IceWM system.
    It first loads additional environment variables from the optional
    `env` file. Then it starts [icewmbg(1)](icewmbg) and **icewm**. It also runs
    the `startup` script and implements basic session management.
    On termination the `shutdown` script will be run first, then
    [icewm-session(1)](icewm-session) will terminate **icewm** and [icewmbg(1)](icewmbg).
    [icewm-session(1)](icewm-session) will also start the optional [icesound(1)](icesound)
    if you give it the **--sound** option.  See [icewm-session(1)](icewm-session).

- [icesh(1)](icesh)

    A powerful tool to control window properties and to interact with the
    window manager. It is typically used in shell scripts. See [icesh(1)](icesh).

- [icehelp(1)](icehelp)

    A small document browser, which is used by **icewm** to display the
    'IceWM manual' and some man pages.

- [icewmhint(1)](icewmhint)

    A utility for passing IceWM-specific window options to **icewm**.
    The options are used to configure the first application which is started
    subsequently.  See [icewmhint(1)](icewmhint).

- [icesound(1)](icesound)

    Plays audio files on GUI events which are raised by **icewm**.
    It supports ALSA, AO and OSS.  See the [icesound(1)](icesound) man page.

- [icewm-menu-fdo(1)](icewm-menu-fdo)

    Generate an **icewm** menu with executable desktop applications
    according to XDG specifications. See the [icewm-menu-fdo(1)](icewm-menu-fdo) man page.

- [icewm-set-gnomewm(1)](icewm-set-gnomewm)

    Configures GNOME to start IceWM instead of its own WM.

# OPTIONS

## COMMON OPTIONS

Each of the IceWM executables supports the following options:

- **-c**, **--config**=_FILE_

    Use _FILE_ as the source of configuration options.  By default **icewm**
    looks for a file named `preferences`.  Typically this file is stored as
    one of `$ICEWM_PRIVCFG/preferences`,
    `$XDG_CONFIG_HOME/icewm/preferences`, or `$HOME/.icewm/preferences`,
    or in one of the configuration directories explained below. It contains
    a long list of options which allow the user to tweak the behaviour of
    **icewm** to ones taste.  A default `preferences` file contains comments
    about the purpose of each option, the range of useful values and the
    current or default value. A `preferences` file is a readable text file
    which can be modified with the help of a text editor.  If this option is
    given to [icewm-session(1)](icewm-session) then it is passed on to **icewm**. If
    **icewm** is started independently then this option can be given to
    **icewm** directly.  However, usually one will want to use a
    `preferences` file from a default location.

- **-t**, **--theme**=_NAME_

    Use _NAME_ as the name of the **icewm** theme to use.  A theme defines
    the look and feel of **icewm**, like colours, fonts, buttons and button
    behaviour.  Originally a theme defined options to emulate the appearance
    of other desktop environments, like Motif, OS/2 Warp, or Windows.  Over
    the years many new original themes have been designed with beautiful
    icons and backgrounds, which advance the state of the art in desktop
    look and feel.  Many of them can be downloaded from the website
    [https://www.box-look.org/](https://www.box-look.org/browse/cat/142/ord/latest/) and stored in one of the directories
    `$ICEWM_PRIVCFG/icewm/themes/`, `$XDG_CONFIG_HOME/icewm/themes/` or in
    `$HOME/.icewm/themes/`.  You can then activate such a theme via the
    menu in the lower left corner of the display.  A default theme is
    specified in one of `$ICEWM_PRIVCFG/icewm/theme`,
    `$XDG_CONFIG_HOME/icewm/theme`, or in `$HOME/.icewm/theme`.  When a
    new theme is selected then this value is overwritten, so that the next
    time **icewm** is started this choice is reused.

- **--display**=_DISPLAY_

    _DISPLAY_ specifies the connection to the X11 server.  If this option
    is missing, as is usually the case, then _DISPLAY_ is read from the
    environment variable `DISPLAY`.

- **--sync**

    This option is sometimes used in software development of **icewm**.  It
    specifies to use a slower synchronous communication mode with the X11
    server.  This is irrelevant for normal use of **icewm**.

- **-h**, **--help**

    Gives a complete list of all the available command line options with
    some very brief explanation.

- **-V**, **--version**

    Shows the software release version for this program.

## ICEWM OPTIONS

The **icewm** program supports some additional options:

- **--replace**

    Instructs **icewm** to replace an existing window manager.  Provided that
    the window manager being replaced is ICCCM 2.0 compliant, once it
    notices that it is to be replaced it will cease operations and typically
    stop execution.  This allows **icewm** to establish itself as the only
    active window manager.

- **-r**, **--restart**

    Tell **icewm** to restart itself. This reloads the configuration from file.

- **--configured**

    Shows a list of configuration options which were enabled when **icewm**
    was compiled from source code.  This can be helpful if one suspects some
    functionality may be missing.

- **--directories**

    Gives a list of directories where **icewm** will look for configuration
    data.  This list is printed in the actual order in which **icewm** uses
    it to search for configuration files.

- **-l**, **--list-themes**

    **icewm** will search all the configuration directories for theme files
    and print a list of all found themes.

- **--postpreferences**

    This gives a long list of all the internal **icewm** options with their
    actual values after **icewm** has processed all of the configuration and
    theme files. In some advanced scenarios this can be helpful to inspect
    which configuration was chosen or whether option formatting was correct.

# USAGE

## TASKBAR

On startup **icewm** launches the task bar at the bottom of the screen.
The task bar consists from left to right  of the following components:

The _Menu_ button in the lower left corner gives access to the **icewm**
root menu. This menu has sub-menus to start applications, to control
**icewm** settings, and the **icewm** _Logout_ menu.

The _Show Desktop_ button unmaps all application windows to fully
uncover the desktop.

The _Window List Menu_ button gives access to a menu with a list of
active windows for the current work space and a list of work spaces
with sub-menus for their active application windows.

The _Toolbar_ is a list of icons for applications which are defined in
the toolbar configuration file.

The _Workspace List_ shows one button for each work space.  The current
work space is indicated by a pressed button.  Pressing another work space
button switches to that work space.  The work spaces are defined in the
`preferences` file.  When `PagerShowPreview` is turned on a small
graphical summary for each workspace is shown.

The _Task Pane_ consists of a list of wide buttons for each application
which is running on the current work space.  Each task button shows the
application icon and the application title.  The active application is
indicated by a pressed button.  This is the application which has input
focus.  Pressing another button activates that application: it is
brought to the foreground and receives input focus.  Other mouse
controlled activities on the window buttons are dragging window buttons to
(temporarily) rearrange the order (with left mouse button) or closing
the application window (with middle button while pressing and holding `Alt`).

If there are not many application buttons then a stretch of plain task
bar is visible.  Clicking on it with the right mouse button gives the
task bar menu.  Even with a full task pane, this menu can be usually
accessed by right-clicking the bottom right corner of the taskbar.

The _Tray Applet_ shows system tray objects.

The _APM Applet_ shows battery power status.

The _Net Applet_ shows network activity.  Network devices to monitor
are given by the `NetworkStatusDevice` option.

The _Memory Applet_ monitors memory usage.

The _CPU Applet_ monitors processor utilization.

The _Mailbox Applet_ monitors mailbox status changes.  The location of
the mailbox is given by the `MailBoxPath` preferences option or else by
the `MAILPATH` or `MAIL` environment variables.  It can be the path of
a local mail spool file or the specification of a remote POP3 or IMAP
location.  For example:

    MailBoxPath="pop3://myname:password@host.com/"

The _Clock Applet_ shows the current time and date.  It is configured
by the `TimeFormat` option.

The _Task Bar Collapse_ button collapses the task bar and hides it.

Not all **icewm** applets may show up on the task bar.  They must have
been enabled during configuration of the **icewm** software.  Their
appearance is also controlled by options in the `preferences` file.

## INPUT FOCUS

Of all visible windows only one can be the active window.  This is the
window which has input focus.  It is the primary receiver of keyboard
and mouse events and hence one can interact with the application which
created that window.  A primary task of a window manager is to allow the
user to switch input focus between different windows.  The primary means
to do this is the mouse pointer.  By moving the mouse pointer over the
screen to another window, and perhaps also by clicking on a window,
input focus can be directed.

The `FocusMode` option controls the way **icewm** gives input focus to
applications.  It is initialized by the `focus_mode` configuration
file.  The focus mode is set via the _Focus_ menu.  **icewm** supports
six focus models:

- **1. Click-to-focus**

    The default focus mode.  In this mode changing input focus requires to
    click a window with the left mouse button. The window is raised if
    needed.  When an application requests focus its task pane button
    flashes.  This gives the option to honor this request or to ignore it.
    When a new application window appears it automatically receives focus.
    Also when a hidden application raises to the front it receives focus.

- **2. Sloppy-mouse-focus**

    Sets input focus merely by moving the mouse pointer over a window.  It
    is called sloppy, because if the mouse then leaves the window and moves
    to the desktop background the input focus remains with the last active
    window.  When a window receives focus it is raised.  When an application
    requests focus its task pane button flashes.  A new application or an
    application which raises to the front automatically receives focus.

- **3. Explicit-focus**

    Focus is even more user-controlled than **Click-to-focus**.  When a
    window receives focus it is not raised by default, unless the frame
    border is clicked.  No flashing occurs when an application requests
    focus.  When a new application window appears it does not receive focus.
    Only by explicit clicking on a window is focus directed.

- **4. Strict-mouse-focus**

    Like **Sloppy** but focus remains with the last window. New applications
    don't receive focus and are mapped behind other windows.  When an
    application raises to the front it still does not get focus.

- **5. Quiet-sloppy-focus**

    Like **Sloppy** but no disturbing flashing occurs on the task bar when an
    application requests focus.

- **6. Custom-mode**

    A focus mode which is defined in detail by ten options in the
    `preferences` file.
    These are:
    `ClickToFocus`,
    `FocusOnAppRaise`,
    `RequestFocusOnAppRaise`,
    `RaiseOnFocus`,
    `RaiseOnClickClient`,
    `FocusChangesWorkspace`,
    `FocusOnMap`,
    `FocusOnMapTransient`,
    `FocusOnMapTransientActive`,
    `MapInactiveOnTop`.

    All non-Custom focus modes override these ten options.

Apart from the mouse, **icewm** supports changing input focus in two
other ways. Both involve the keyboard.  The first uses the
`QuickSwitch` window.  It is activated by pressing `Alt+Tab` or
`Alt+Shift+Tab`.  A window pops up in the centre of the screen with a
narrow band over the next or previous window which will receive input
focus when the `Alt` key is released.  By repeatedly pressing
`Alt+Tab` or `Alt+Shift+Tab` one can cycle through all windows.

The second keyboard method involves pressing `Alt+Esc` or
`Alt+Shift+Esc`.  Input focus is immediately changed to the next or
previous window, which will be raised to make it fully visible.

And finally, there is another way which is a hybrid of keyboard and
mouse control. It involves the `QuickSwitch` popup explained before,
after pressing `Alt+Tab` and while still holding `Alt` a left click
on one of the list items causes the activation of the related window.

## WINDOW PLACEMENT

A second important task of a window manager is to place new windows on
the screen.  By default **icewm** chooses a placement with minimal
overlap, but this is determined by the `SmartPlacement` option in the
`preferences` file.  If `SmartPlacement` is turned off then windows
are placed in sequence from left to right and top to bottom.  One can
also turn on `ManualPlacement`.  Then new windows appear initially in
the top left corner and the mouse cursor changes into a fist.  By moving
the fist cursor to a suitable location and clicking the new window will
appear at the mouse click location.

## WINDOW LAYERS

Windows can overlap.  Which window appears on top is determined by three
features.  Newer windows appear over older windows.  By clicking on a
window it is raised to the top.  But both are overruled by the window
layer.  Windows can be placed in different layers via the _Layers_
menu.  Click with the right mouse button on the window frame and select
_Layer_.  From there choose one of seven window layers.  These are
ordered from higher to lower.  Windows in higher layers appear over
windows in lower layers.

## WORKSPACES

**icewm** supports multiple virtual desktops called work spaces.  A work
space is like a screen where a subset of all application windows are
mapped.  Thanks to multiple work spaces we can more easily manage a
large number of applications.  The number of work spaces and their names
are configurable in the `preferences` file through the
`WorkspaceNames` option.  By default four workspaces are created
with the names 1, 2, 3 and 4 thus:

    WorkspaceNames=" 1 ", " 2 ", " 3 ", " 4 "

This syntax is typical for **icewm** options which receive multiple
values.  It is a list of comma separated values each of which can be
quoted.

The work spaces are visible on the toolbar.  One can switch to a
different work space by pressing the work space button in the toolbar,
but after becoming familiar with the 'keyboard shortcuts' below one will
want to use a hotkey to choose a work space.  If the `EdgeSwitch`
options is enabled in the `preferences` file (with sub-options
`HorizontalEdgeSwitch` and `VerticalEdgeSwitch`) then one can move to
the next or previous workspace by moving the mouse to the edge of the
screen.  The `ContinuousEdgeSwitch` option enables continuous movement
to subsequent workspaces.  The `EdgeSwitchDelay` option says how long
to wait before a change of workspace occurs.

To move an application window to a different work space one can use a
keyboard shortcut.  Another option is to select the _Move To_ submenu
in the window menu of the window frame.

## ADDRESS BAR

If **EnableAddressBar**=1 then **KeySysAddressBar**=`Alt+Ctrl+Space`
activates the address bar in the task bar.
If **ShowAddressBar**=1 it is always shown. This is a command line in
the task bar where a shell command can be typed.
Pressing `Enter` will execute the command.
**AddressBarCommand**=`/bin/sh` will be used to execute the command.
On `Control+Enter` the command is executed in a terminal
as given by **TerminalCommand**.
The address bar maintains a history which is navigable by the _Up_
and _Down_ keys.
It supports file completion using `Tab` or `Ctrl+I`.
A rich set of editing operations is supported,
including cut-/copy-/paste-operations.

## KEYBOARD SHORTCUTS

**icewm** supports a large number of hotkeys to activate some behaviour
with a single key combination.  These are all configurable in the
`preferences` file.  Here we give their default values, followed by
their preferences names and short descriptions of their effect:

- `Alt+F1`

    `KeyWinRaise` raises the window which currently has input focus.

- `Alt+F2`

    `KeyWinOccupyAll` makes the active window occupy all work spaces.

- `Alt+F3`

    `KeyWinLower` lowers the window which currently has input focus.

- `Alt+F4`

    `KeyWinClose` closes the active window.

- `Alt+F5`

    `KeyWinRestore` restores the active window to its visible state.

- `Alt+F6`

    `KeyWinNext` switches focus to the next window.

- `Alt+Shift+F6`

    `KeyWinPrev` switches focus to the previous window.

- `Alt+F7`

    `KeyWinMove` starts movement of the active window.

- `Alt+F8`

    `KeyWinSize` starts resizing of the active window.

- `Alt+F9`

    `KeyWinMinimize` iconifies the active window.

- `Alt+F10`

    `KeyWinMaximize` maximizes the active window with borders.

- `Alt+Shift+F10`

    `KeyWinMaximizeVert` maximizes the active window vertically.

- `undefined`

    `KeyWinMaximizeHoriz` maximizes the active window horizontally.

- `Alt+F11`

    `KeyWinFullscreen` maximizes the active window without borders.

- `Alt+F12`

    `KeyWinRollup` rolls up the active window.

- `Alt+Shift+F12`

    `KeyWinHide` hides the active window.

- `Alt+Space`

    `KeyWinMenu` posts the window menu.

- `Ctrl+Alt+KP_7`

    `KeyWinArrangeNW` moves the active window to the top left corner of the screen.

- `Ctrl+Alt+KP_8`

    `KeyWinArrangeN` moves the active window to the top middle of the screen.

- `Ctrl+Alt+KP_9`

    `KeyWinArrangeNE` moves the active window to the top right of the screen.

- `Ctrl+Alt+KP_6`

    `KeyWinArrangeE` moves the active window to the middle right of the screen.

- `Ctrl+Alt+KP_3`

    `KeyWinArrangeSE` moves the active window to the bottom right of the screen.

- `Ctrl+Alt+KP_2`

    `KeyWinArrangeS` moves the active window to the bottom middle of the screen.

- `Ctrl+Alt+KP_1`

    `KeyWinArrangeSW` moves the active window to the bottom left of the screen.

- `Ctrl+Alt+KP_4`

    `KeyWinArrangeW` moves the active window to the middle left of the screen.

- `Ctrl+Alt+KP_5`

    `KeyWinArrangeC` moves the active window to the center of the screen.

- `Shift+Esc`

    `KeySysWinMenu` posts the system window menu.

- `Alt+Esc`

    `KeySysWinNext` give focus to the next window and raise it.

- `Alt+Shift+Esc`

    `KeySysWinPrev` give focus to the previous window and raise it.

- `Alt+Ctrl+Del`

    `KeySysDialog` opens the IceWM system dialog in the center of the screen.

- `Ctrl+Esc`

    `KeySysMenu` activates the IceWM root menu in the lower left corner.

- `Alt+Ctrl+Esc`

    `KeySysWindowList` opens the IceWM system window list in the center of the screen.

- `Alt+Ctrl+Space`

    `KeySysAddressBar` opens the address bar in the task bar where a command can be typed.

- `Alt+Ctrl+Left`

    `KeySysWorkspacePrev` goes one workspace to the left.

- `Alt+Ctrl+Right`

    `KeySysWorkspaceNext` goes one workspace to the right.

- `Alt+Ctrl+Down`

    `KeySysWorkspaceLast` goes to the previous workspace.

- `Alt+Ctrl+Shift+Left`

    `KeySysWorkspacePrevTakeWin` takes the active window one workspace to the left.

- `Alt+Ctrl+Shift+Right`

    `KeySysWorkspaceNextTakeWin` takes the active window one workspace to the right.

- `Alt+Ctrl+Shift+Down`

    `KeySysWorkspaceLastTakeWin` takes the active window to the previous workspace.

- `Alt+Ctrl+1`

    `KeySysWorkspace1` goes to workspace 1.

- `Alt+Ctrl+2`

    `KeySysWorkspace2` goes to workspace 2.

- `Alt+Ctrl+3`

    `KeySysWorkspace3` goes to workspace 3.

- `Alt+Ctrl+4`

    `KeySysWorkspace4` goes to workspace 4.

- `Alt+Ctrl+5`

    `KeySysWorkspace5` goes to workspace 5.

- `Alt+Ctrl+6`

    `KeySysWorkspace6` goes to workspace 6.

- `Alt+Ctrl+7`

    `KeySysWorkspace7` goes to workspace 7.

- `Alt+Ctrl+8`

    `KeySysWorkspace8` goes to workspace 8.

- `Alt+Ctrl+9`

    `KeySysWorkspace9` goes to workspace 9.

- `Alt+Ctrl+0`

    `KeySysWorkspace10` goes to workspace 10.

- `Alt+Ctrl+bracketleft`

    `KeySysWorkspace11` goes to workspace 11.

- `Alt+Ctrl+bracketright`

    `KeySysWorkspace12` goes to workspace 12.

- `Alt+Ctrl+Shift+1`

    `KeySysWorkspace1TakeWin` takes the active window to workspace 1.

- `Alt+Ctrl+Shift+2`

    `KeySysWorkspace2TakeWin` takes the active window to workspace 2.

- `Alt+Ctrl+Shift+3`

    `KeySysWorkspace3TakeWin` takes the active window to workspace 3.

- `Alt+Ctrl+Shift+4`

    `KeySysWorkspace4TakeWin` takes the active window to workspace 4.

- `Alt+Ctrl+Shift+5`

    `KeySysWorkspace5TakeWin` takes the active window to workspace 5.

- `Alt+Ctrl+Shift+6`

    `KeySysWorkspace6TakeWin` takes the active window to workspace 6.

- `Alt+Ctrl+Shift+7`

    `KeySysWorkspace7TakeWin` takes the active window to workspace 7.

- `Alt+Ctrl+Shift+8`

    `KeySysWorkspace8TakeWin` takes the active window to workspace 8.

- `Alt+Ctrl+Shift+9`

    `KeySysWorkspace9TakeWin` takes the active window to workspace 9.

- `Alt+Ctrl+Shift+0`

    `KeySysWorkspace10TakeWin` takes the active window to workspace 10.

- `Alt+Ctrl+Shift+bracketleft`

    `KeySysWorkspace11TakeWin` takes the active window to workspace 11.

- `Alt+Ctrl+Shift+bracketright`

    `KeySysWorkspace12TakeWin` takes the active window to workspace 12.

- `Alt+Shift+F2`

    `KeySysTileVertical` tiles all windows from left to right maximized vertically.

- `Alt+Shift+F3`

    `KeySysTileHorizontal` tiles all windows from top to bottom maximized horizontally.

- `Alt+Shift+F4`

    `KeySysCascade` makes a horizontal cascade of all windows which are maximized vertically.

- `Alt+Shift+F5`

    `KeySysArrange` rearranges the windows.

- `Alt+Shift+F7`

    `KeySysUndoArrange` undoes arrangement.

- `Alt+Shift+F8`

    `KeySysArrangeIcons` rearranges icons.

- `Alt+Shift+F9`

    `KeySysMinimizeAll` minimizes all windows.

- `Alt+Shift+F11`

    `KeySysHideAll` hides all windows.

- `Alt+Ctrl+d`

    `KeySysShowDesktop` unmaps all windows to show the desktop.

- `Alt+Ctrl+h`

    `KeySysCollapseTaskBar` hides the task bar.

- `undefined`

    `KeyTaskBarSwitchNext` switches to the next window in the task bar.

- `undefined`

    `KeyTaskBarSwitchPrev` switches to the previous window in the task bar.

- `undefined`

    `KeyTaskBarMoveNext` moves the task bar button of the current window
    right.

- `undefined`

    `KeyTaskBarMovePrev` moves the task bar button of the current window
    left.

- `undefined`

    `KeySysWinListMenu` shows the window list menu.

- `Alt+Tab`

    `KeySysSwitchNext` opens the `QuickSwitch` popup (see ["INPUT FOCUS"](#input-focus))
    and/or moves the selector in the `QuickSwitch` popup.

- `Alt+Shift+Tab`

    `KeySysSwitchLast` works like `KeySysSwitchNext` but moving in the
    opposite direction.

- `Alt+grave`

    `KeySysSwitchClass` is like `KeySysSwitchNext` but only for windows
    with the same WM\_CLASS property as the currently focused window.

## MOUSE BINDINGS

You can control windows by a modified mouse button press:

- `Alt+Pointer_Button1`

    `MouseWinMove` moves the window under the mouse over the screen.

- `Alt+Pointer_Button3`

    `MouseWinSize` resizes the window.  Keep the key and button pressed.
    To enlarge the window move the mouse button away from the center.  To
    shrink it move towards the centre.

- `Ctrl+Alt+Pointer_Button1`

    `MouseWinRaise` raises the window under the mouse.

- `Ctrl+Alt+Pointer_Button1`

    `MouseWinLower` lowers the window under the mouse.
    If this is equal to `MouseWinRaise` and the window can be raised
    then `MouseWinRaise` takes preference over `MouseWinLower`.

Clicking on the desktop activates a menu.  The middle button shows the
window list (`DesktopWinListButton=2`).  The right button shows the
root menu (`DesktopMenuButton=3`).

The title frame of a window also listens for mouse clicks.  Left double
clicking maximizes the window (`TitleBarMaximizeButton=1`).  Middle
double clicking rolls up the window (`TitleBarRollupButton=2`).
Pressing a mouse button and moving it will move the window.  `Alt+left`
button lowers the window.

When the mouse is on the window frame then a left click raises the
window.  Dragging with the left button down resizes the window.
Clicking the right button pops up the context menu.  Dragging with the
right button moves the window.

# SIGNALS

**icewm** supports the following signals:

- **SIGHUP**

    **icewm** will restart itself. It is a way to reload the configuration.

- **SIGINT**, **SIGTERM**

    **icewm** will cease to manage application windows and terminate.

- **SIGQUIT**

    **icewm** will initiate the logout procedure.  If a `LogoutCommand`
    preferences option was configured it will be executed.

# ENVIRONMENT VARIABLES

- **ICEWM\_PRIVCFG**

    The directory for user private configuration files.  When this
    environment variable is not specified, the default directory is
    `$XDG_CONFIG_HOME/icewm` when that directory exists, otherwise the
    default value is `$HOME/.icewm`.

- **DISPLAY**

    The name of the X11 server.  See [Xorg(1)](https://manned.org/Xorg.1) or [Xserver(1)](https://manned.org/Xserver.1).  This
    value can be overridden by the **--display** option.

- **MAILPATH**, **MAIL**

    Gives the location of your mailbox.  If the schema is omitted the local
    "file" schema is assumed.  This is used by the mailbox applet in the
    task bar to show the status of your mailbox.  If the `MailBoxPath`
    option in the `preferences` file is set, then that one takes
    precedence.

# FILES

**icewm** looks for configuration files in the following directories, in
the given order, until it finds one:

- `$ICEWM_PRIVCFG/`

    Contains user-specific configurations.  When **ICEWM\_PRIVCFG** is
    specified, this directory takes precedence over
    `$XDG_CONFIG_HOME/icewm` and `$HOME/.icewm`.

- `$XDG_CONFIG_HOME/icewm/`

    Contains user-specific configurations.  When this directory exists it
    take precedence over `$HOME/.icewm`.

- `$HOME/.icewm/`

    Contains user-specific configurations.  This is the historical default
    directory.

- `/etc/icewm/`

    Contains system-wide customized defaults.  Please note that your local
    installation may have been configured to use a different system
    location.  The output of `icewm --directories` will show this location.

- `/usr/share/icewm/`

    Default local installation settings.

## CONFIGURATION FILES

- `env`

    [icewm-session(1)](icewm-session) loads additional environment variables from the file
    `env`.  Each line is subjected to POSIX shell expansion by
    [wordexp(3)](https://manned.org/wordexp.3).  Comment lines starting by a hash-sign (`#`) are ignored.
    [icewm-session(1)](icewm-session) will load those expanded lines which contain a name,
    followed by an equals sign, followed by the value (which may be empty).

    See [icewm-env(5)](icewm-env).

- `focus_mode`

    Defines the initial value for `FocusMode`.  Its default value is
    `FocusMode=1` (Click-to-focus).  This can be changed via the menu.
    **icewm** will save the Focus menu choice in this file.

    See [icewm-focus\_mode(5)](icewm-focus_mode).

- `keys`

    Global keybindings to launch applications, which need not be window
    manager related.  Each non-empty line starts with the word `key`.
    After one or more spaces follows a double-quoted string of the bound X11
    key combination like `Alt+Ctrl+Shift+X`.  Then after at least one space
    follows a shell command line which will be executed by **icewm** whenever
    this key combination is pressed.  For example, the following line
    creates a hotkey to reload the **icewm** configuration:

        key "Ctrl+Shift+r"      icesh restart

    See [icewm-keys(5)](icewm-keys).

- `menu`

    A menu of applications; usually customized by the user.  **icewm**
    provides the [icewm-menu-fdo(1)](icewm-menu-fdo) program to generate a default menu.
    Similar programs are [xdg\_menu(1)](https://manned.org/xdg_menu.1), [mmaker(1)](https://manned.org/mmaker.1) (MenuMaker),
    [xde-menu(1)](https://manned.org/xde-menu.1), [xdgmenumaker(1)](https://manned.org/xdgmenumaker.1).

    See [icewm-menu(5)](icewm-menu).

- `preferences`

    Contains general settings like paths, colors and fonts, but also options
    to control the **icewm** focus behaviour and the applets which are
    started in the task bar.  The **icewm** installation will provide a
    default `preferences` file, which can be copied to the **icewm** user
    configuration directory and modified.

    See [icewm-preferences(5)](icewm-preferences).

- `prefoverride`

    Settings which override the settings from a theme.  Some of the **icewm**
    configuration options from the preferences file which control the
    look-and-feel may be overridden by the theme, if the theme designer
    thinks this is desirable.  However, this `prefoverride` file will again
    override this for a few specific options of your choosing.  It is safe
    to leave this file empty initially.

    See [icewm-prefoverride(5)](icewm-prefoverride).

- `programs`

    An automatically generated menu of applications.  This could be used by
    [wmconfig(1)](https://manned.org/wmconfig.1), menu or similar programs to give easy access to all the
    desktop applications which are installed on the system.

    See [icewm-programs(5)](icewm-programs).

- `theme`

    This file contains the name of the default theme.  On startup **icewm**
    reads this file to obtain the theme name, unless **icewm** was started
    with the **--theme** option.  Whenever a different theme is selected from
    the **icewm** Menu then the theme file is overwritten with the name of
    the selected theme.  This theme file contains the keyword `Theme`,
    followed by an equals sign, followed by a double-quoted string with the
    theme name.  The theme name is the name of the theme directory, followed
    by a slash, followed by the theme file.  Usually the theme file is just
    `default.theme`, but a theme may have alternatives.  Alternatives are
    small tweaks of a theme.  These are specified in their own `.theme`
    file, which replaces `default.theme`.  If no theme file exists then
    **icewm** will use the default setting of
    `Theme="default/default.theme"`.

    See [icewm-theme(5)](icewm-theme).

- `toolbar`

    Contains names of quick to launch applications with icons for the task
    bar.  Each non-empty non-comment line starts with the keyword **prog**.
    After one or more spaces follows a name, which is displayed in a tool
    tip whenever the mouse cursor hovers over the toolbar icon.  This name
    may be a double quoted string.  Then follows the bare name of the icon
    to use without extensions.  This icon will be shown in the toolbar.  The
    last component is a shell command line which will be executed whenever
    the user presses the icon in the toolbar.  For example, the following
    line in toolbar will create a button with tool tip `Mozilla Firefox`
    with the `firefox` icon which launches [firefox(1)](https://manned.org/firefox.1) when clicked:

        prog  "Mozilla Firefox"  firefox  /usr/bin/firefox --private-window

    See [icewm-toolbar(5)](icewm-toolbar).

- `winoptions`

    Contains settings to control window appearance and behaviour which are
    specific to applications or groups of applications.  Options can control
    the border, whether it appears on the task bar, the window list, the
    system tray and the work spaces.  Also its layer, geometry, whether it
    can be moved, resized and closed.

    See [icewm-winoptions(5)](icewm-winoptions).

- `startup`

    Contains commands to be executed on **icewm** startup.  This is an
    executable script with commands to tweak X11 settings and launch some
    applications which need to be active whenever **icewm** is started.
    It is run by [icewm-session(1)](icewm-session) when **icewm** starts.

    See [icewm-startup(5)](icewm-startup).

- `shutdown`

    Contains commands to be executed on **icewm** shutdown.  This is an
    executable script with commands to be executed in the last stage of
    **icewm** termination.  Typically they may undo some of the effects of
    the `startup` script.  It is run by [icewm-session(1)](icewm-session) when **icewm**
    terminates.

    See [icewm-shutdown(5)](icewm-shutdown).

## CONFIGURATION SUBDIRECTORIES

- `icons`

    Contains icons which are used to identify applications.  Usually these
    files are in the XPM format, but the PNG and SVG image formats are also
    supported.  The names of icon files may follow a specific naming
    pattern, like `app_32x32.xpm`.  They start with a base name, usually
    this is just a single word.  Then follows an underscore, followed by a
    size specification in the format `SIZExSIZE`.  This is followed by a
    dot and the file extension, where the extension denotes the icon image
    format.  Common sizes are 16, 32 and 48 for small, large and huge icons.
    This depends on the respective `IconSize` preferences options.

- `ledclock`

    Pictures of digits for the LED clock which is displayed in the
    bottom-right corner of the task bar.  These can be seen when the
    `TaskBarShowClock` and `TaskBarClockLeds` options are both set to 1.

- `mailbox`

    Icons which are used to display different states of the mailbox applet
    in the task bar.  There are five states and each has its own icon:
    `mail.xpm`, `newmail.xpm`, `unreadmail.xpm`, `nomail.xpm`,
    `errmail.xpm`.

- `sounds`

    Audio files which are played by [icesound(1)](icesound) on GUI events.  These
    are: `startup.wav`, `shutdown.wav`, `restart.wav`, `launchApp.wav`,
    `workspaceChange.wav`, `windowOpen.wav`, `windowClose.wav`,
    `dialogOpen.wav`, `dialogClose.wav`, `windowMax.wav`,
    `windowRestore.wav`, `windowMin.wav`, `windowHide.wav`,
    `windowRollup.wav`, `windowMoved.wav`, `windowSized.wav`,
    `windowLower.wav`.

- `taskbar`

    Pictures to customize the look of the task bar.  These include:
    `taskbarbg.xpm`, `taskbuttonactive.xpm`, `taskbuttonbg.xpm`,
    `taskbuttonminimized.xpm`, `toolbuttonbg.xpm`,
    `workspacebuttonactive.xpm`, `workspacebuttonbg.xpm`.

- `themes`

    A directory to store themes.  Each theme is stored in its own
    sub-directory in the `themes` directory. A theme contains at least a
    `default.theme` file, and optionally theme alternatives which are
    additional files which have a `.theme` file name extension and which
    contain tweaks of the `default.theme` file.
    How to create a theme is explained in the
    [IceWM Theme Creation Howto](https://ice-wm.org/themes).

## OPACITY

> IceWM supports window opacity and transparency in connection with an
> external compositor like [compton(1)](https://manned.org/compton.1). If a client window sets the
> `_NET_WM_WINDOW_OPACITY` property on its window then **icewm** will copy
> this to the outer frame window where **compton** will read it to adjust
> the opacity of the client window. The opacity can also be controlled by
> **icewm** when this is configured in the [icewm-winoptions(5)](icewm-winoptions) file.
> Another way is to use [icewmhint(1)](icewmhint) to preset the opacity level
> immediately before starting the application.  The opacity level of
> running applications can always be queried or modified by [icesh(1)](icesh).
>
> The \_NET\_WM\_WINDOW\_TYPE properties which **icewm** sets on its windows
> are _DIALOG_, _NOTIFICATION_, _POPUP\_MENU_ and _TOOLTIP_. The output
> of `icesh windows` shows their WM\_CLASS values.

# EXAMPLES

Examples of the above configuration files can be found in the default
installation path or in the system-wide defaults.  See the output of
`icewm --directories` for their locations.

# CONFORMING TO

ICCCM 2.0: partial.  NetWM/EWMH: extensive.
See the file `COMPLIANCE` in the distribution for full details.

# SEE ALSO

[icehelp(1)](icehelp),
[icesh(1)](icesh),
[icesound(1)](icesound),
[icewm-env(5)](icewm-env),
[icewm-focus\_mode(5)](icewm-focus_mode),
[icewm-keys(5)](icewm-keys),
[icewm-menu(5)](icewm-menu),
[icewm-menu-fdo(1)](icewm-menu-fdo),
[icewm-menu-xrandr(1)](icewm-menu-xrandr),
[icewm-preferences(5)](icewm-preferences),
[icewm-prefoverride(5)](icewm-prefoverride),
[icewm-programs(5)](icewm-programs),
[icewm-session(1)](icewm-session),
[icewm-set-gnomewm(1)](icewm-set-gnomewm),
[icewm-shutdown(5)](icewm-shutdown),
[icewm-startup(5)](icewm-startup),
[icewm-theme(5)](icewm-theme),
[icewm-toolbar(5)](icewm-toolbar),
[icewm-winoptions(5)](icewm-winoptions),
[icewmbg(1)](icewmbg),
[icewmhint(1)](icewmhint),
[Xorg(1)](https://manned.org/Xorg.1),
[Xserver(1)](https://manned.org/Xserver.1),
[xinit(1)](https://manned.org/xinit.1),
[xprop(1)](https://manned.org/xprop.1),
[xwininfo(1)](https://manned.org/xwininfo.1),
[wmctrl(1)](https://manned.org/wmctrl.1).

# BUGS

**icewm** had no known bugs at the time of release.  Please report bugs
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
