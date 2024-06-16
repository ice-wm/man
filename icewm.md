---
title: "icewm(1)"
---
## NAME

    icewm - lightweight X11 window manager

## SYNOPSIS

**icewm** \[_OPTIONS_\]

## DESCRIPTION

**icewm** is a small and fast window manager for the X11 window system.  It
is best started by [icewm-session(1)](icewm-session), which also starts [icewmbg(1)](icewmbg).

**icewm** is called _re-parenting_, because it draws frames around
application windows.  Drag this frame with the mouse, to move or resize
a window.

Because windows may overlap, **icewm** is also a stacking window manager.
Many windows may exist, some hidden behind others.

**icewm** supports a configurable number of virtual desktops.  These are
called workspaces. Related windows are grouped on a dedicated workspace.
By switching between workspaces, the user can attend to different tasks,
while keeping oversight.  This is supported by a task bar and a pager.

The installation comes with several themes. Choose a theme via a menu.
Install extra themes automatically with the **--install** option.

**icewm** is compliant with the ICCCM and EWMH window manager specifications.

## PROGRAMS

The **icewm** package includes several programs:

- [icewm(1)](icewm)

    The actual window manager. It positions application windows on screen
    and decorates them with borders. It gives input focus to the current
    active application. **icewm** supports different focus modes, which are
    explained below. It draws a small task bar at the bottom of the screen,
    that gives easy access to programs, to virtual desktops, to active
    applications, and to a small set of monitoring applets.

- [icewmbg(1)](icewmbg)

    The background setting application. It can assign plain background color
    or images in different formats to the X background.  Each workspace can
    have its own background.  It supports semitransparency. Semitransparent
    background image and colour can be configured. When the background image
    has changed then [icewmbg(1)](icewmbg) can be notified to update the background.
    Multi-head monitor setups are fully supported.  See the [icewmbg(1)](icewmbg).

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

    A small document browser that is used by **icewm** to display the
    'IceWM manual' and some man pages.

- [icewmhint(1)](icewmhint)

    A utility for passing IceWM-specific window options to **icewm**.
    The options are used to configure the first application that is started
    subsequently.  See [icewmhint(1)](icewmhint).

- [icesound(1)](icesound)

    Plays audio files on GUI events that are raised by **icewm**.
    It supports ALSA, AO and OSS.  See the [icesound(1)](icesound) man page.

- [icewm-menu-fdo(1)](icewm-menu-fdo)

    Generate an **icewm** menu with executable desktop applications
    according to XDG specifications. See the [icewm-menu-fdo(1)](icewm-menu-fdo) man page.

- [icewm-set-gnomewm(1)](icewm-set-gnomewm)

    Configures GNOME to start IceWM instead of its own WM.

## OPTIONS

## COMMON OPTIONS

Each of the IceWM executables supports the following options:

- **-c**, **--config**=_FILE_

    Use _FILE_ as the source of configuration options.  By default **icewm**
    looks for a file named `preferences`.  This is a readable text file
    that can be modified with the help of a text editor.

- **-t**, **--theme**=_NAME_

    Use _NAME_ as the name of the **icewm** theme to use.  A theme defines
    the look and feel of **icewm**, like colors, fonts and buttons.

- **-d**, **--display**=_DISPLAY_

    Connect to the X11 server on _DISPLAY_.  By default
    the environment variable `DISPLAY` is used.

- **-o**, **--output=FILE**

    Redirect all output to _FILE_.
    A leading tilde or environment variable is expanded.

- **--sync**

    This option specifies to use a slower synchronous communication mode
    with the X11 server.  This is irrelevant for normal use.

- **-h**, **--help**

    Gives a complete list of all the available command-line options with
    some very brief explanation.

- **-V**, **--version**

    Shows the software release version for this program.

## ICEWM OPTIONS

The **icewm** program supports some additional options:

- **-a**, **--alpha**

    Use a 32-bit visual for translucency. This can also be set in
    the preferences file as `Alpha=1`.

- **--replace**

    Instructs **icewm** to replace an existing window manager.  Provided that
    the window manager being replaced is ICCCM 2.0 compliant, once it
    notices that it is to be replaced it will cease operations and typically
    stop execution.  This allows **icewm** to establish itself as the only
    active window manager.

- **-r**, **--restart**

    Tell **icewm** to restart itself. This reloads the configuration from
    file. If no window manager is active, then it starts one.

- **-s**, **--splash**=_IMAGE_

    Briefly show _IMAGE_ on startup in the center of the screen.
    This can also be set in the preferences file as Splash=`image.jpg`.

- **--configured**

    Shows a list of configuration options that were enabled when **icewm**
    was compiled from source code.  This can be helpful if one suspects some
    functionality may be missing.

- **--directories**

    Gives a list of directories where **icewm** will look for configuration
    data.  This list is printed in the actual order in which **icewm** uses
    it to search for configuration files.

- **-l**, **--list-themes**

    **icewm** will search all the configuration directories for theme files
    and print a list of all found themes.

- **-i**, **--install**=_THEME_

    Install _THEME_ from icewm-extra and exit. When _THEME_ is _list_,
    print a listing of available themes to install. This option requires
    the presence of the _lzip_, _tar_ and _wget_ or _curl_ commands.

- **-p**, **--postpreferences**

    This gives a long list of all the internal **icewm** options with their
    actual values after **icewm** has processed all of the configuration and
    theme files. In some advanced scenarios this can be helpful to inspect
    which configuration was chosen or whether option formatting was correct.

- **--rewrite-preferences**

    Overwrite an existing preferences file with an icewm default preferences,
    but preserve all modifications insofar they deviate from the defaults.

- **--extensions**

    Give a list of the current X extensions, their versions and status.

- **--trace**=_conf_,_font_,_icon_,_prog_,_systray_

    Enable tracing of the paths that are used to load configuration,
    fonts, icons, executed programs, and/or system tray applets.

## USAGE

## TASKBAR

On startup **icewm** launches the task bar at the bottom of the screen.
The task bar consists from left to right  of the following components:

The _Menu_ button in the lower left corner gives access to the **icewm**
root menu. This menu has sub-menus to start applications, to control
**icewm** settings, and the **icewm** _Logout_ menu.

The _Show Desktop_ button unmaps all application windows to fully
uncover the desktop.

The _Window List Menu_ button gives access to a menu with a list of
active windows for the current workspace and a list of workspaces
with sub-menus for their active application windows.

The _Toolbar_ is a list of icons for applications that are defined in
the toolbar configuration file.

The _Workspace Pane_ shows one button for each workspace.  The current
workspace is indicated by a pressed button.  Clicking another workspace
switches to that workspace.  Press left mouse, then the Shift key, then
release the left mouse, takes the current window to that workspace.
Press left, then Alt, then release left, moves only the focused window
to other workspace, without changing the current workspace.

The workspaces are defined in the `preferences` file.  To change a name
for only this session, double-click, edit the name and hit Enter.
When `PagerShowPreview` is turned on, a small graphical window summary
for each workspace is shown. They support drag-and-drop: dragging a
Firefox tab to a workspace button changes the current workspace.
Then releasing it moves that tab to a new window in that workspace.

The _Task Pane_ consists of a list of wide buttons for each application
that is running on the current workspace, or all workspaces if
`TaskBarShowAllWindows=1`.  Each task button shows the
application icon and the application title.  The active application is
indicated by a pressed button.  This is the application that has input
focus.  Pressing another button activates that application: it is
brought to the foreground and receives input focus.  Other mouse
controlled activities on the window buttons are: dragging window buttons
with the left mouse button to rearrange the order, closing the application
window with `Alt` + middle button, lowering the application window with
`Ctrl` + middle button, or bringing the application window to the current
workspace with `Shift` + middle button if `TaskBarShowAllWindows=1`.

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

The _Mailbox Applet_ monitors mailbox status changes.
See the section MAILBOX MONITORING below.

The _Clock Applet_ shows the current time and date.  It is configured
by the `TimeFormat` option.

The _Task Bar Collapse_ button collapses the task bar and hides it.

Not all **icewm** applets may show up on the task bar.  They must have
been enabled during configuration of the **icewm** software.  Their
appearance is also controlled by options in the `preferences` file.

## INPUT FOCUS

Of all visible windows only one can be the active window.  This is the
window that has input focus.  It is the primary receiver of keyboard
and mouse events and hence one can interact with the application that
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
    application that raises to the front automatically receives focus.

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

    A focus mode that is defined by the following ten options:
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
ways by keyboard.  By pressing `Alt+Esc` or `Alt+Shift+Esc`,
input focus is immediately changed to the next or previous window,
which will be raised to make it fully visible. The other method
involves the quick switch.

## QUICK SWITCH

The **QuickSwitch** is a means to quickly and interactively change
the input focus to another window.  It is activated by pressing the
`Alt+Tab` or `Alt+Shift+Tab` key combination.  A window pops up
in the centre of the screen with a list of windows to choose from.
A narrow band indicates a selection: the candidate window that will
be activated to receive input focus when the Alt key is released.

The selection can be changed by repeatedly pressing the Tab key, while
keeping the Alt key down. If a Shift key is also down, the direction of
traversal is reversed. Or use the scroll wheel of the mouse.  Or use
one of the digit keys to select the corresponding window from the list.
Arrow keys are also supported, as well as the Home and End key.

To make a selected window the active window, just release the Alt key,
or hit the Return key, or click on it.  To cancel the QuickSwitch,
press Escape or click outside of the QuickSwitch window.

A selected window can be closed by Delete, `Alt+F4`, or the middle
mouse button.  While the QuickSwitch window is up, one can still change
workspace with the usual workspace hotkeys.

The QuickSwitch has two distinct modes: vertical and horizontal.
The window list can include all windows or be limited to the current
workspace. There is an option to raise the selected candidate.
See the many preferences available for the QuickSwitch.

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

## TABBED WINDOWS

A window frame may contain multiple client windows. Only one client can
be visible, while the others are hidden. This is called tabbing.  This
can be helpful to reduce the number of visible windows. To create a tab,
drag the title bar with the middle mouse button, while holding down a
shift key, onto the title bar of another frame. The two title bars will
start to flash to indicate that they can merge. Release the mouse button
to merge the client of the upper window to the lower frame.  Now the
lower frame will have multiple clients, called tabs. The title bar will
show a vertical bar with triple dots to indicate this.
To change the current tab either:

- Click on the triple dots next to the vertical bar.
- Use `KeyWinNext=Alt+F6` to select the next tab.
- Use `KeyWinPrev=Alt+Shift+F6` for the previous tab.
- Use the QuickSwitch.
- Use the window list window.
- Use a submenu in the window menu.

To change the mouse binding for creating tabs, modify
**MouseWinTabbing**=`Shift+Pointer_Button2`.  Another
useful setting is **MouseWinTabbing**=`Pointer_Button1`.

`Alt+F4` closes all tabs. To close just the active tab add to `keys`:

    key "Ctrl+Shift+F4"     icesh -f close

To move the active tab to its own window frame by key, add to `keys`:

    key "Alt+u"             icesh -f untab

To open all chrome windows in the same frame add this to `winoptions`:

    google-chrome.frame:    chrome

## WORKSPACES

**icewm** supports multiple virtual desktops called workspaces.  A
workspace is like a screen where a subset of all application windows are
mapped.  Thanks to multiple workspaces we can more easily manage a
large number of applications.  The number of workspaces and their names
are configurable in the `preferences` file through the
`WorkspaceNames` option.  By default four workspaces are created
with the names 1, 2, 3 and 4 thus:

    WorkspaceNames=" 1 ", " 2 ", " 3 ", " 4 "

This syntax is typical for **icewm** options that receive multiple
values.  It is a list of comma-separated values each of which can be
quoted.

The workspaces are visible on the toolbar.  One can switch to a
different workspace by pressing the workspace button in the toolbar,
but after becoming familiar with the 'keyboard shortcuts' below one will
want to use a hotkey to choose a workspace.  If the `EdgeSwitch`
options is enabled in the `preferences` file (with sub-options
`HorizontalEdgeSwitch` and `VerticalEdgeSwitch`) then one can move to
the next or previous workspace by moving the mouse to the edge of the
screen.  The `ContinuousEdgeSwitch` option enables continuous movement
to subsequent workspaces.  The `EdgeSwitchDelay` option says how long
to wait before a change of workspace occurs.

To move an application window to a different workspace one can use a
keyboard shortcut.  Another option is to select the _Move To_ submenu
in the window menu of the window frame.

## DRAG AND DROP

The task bar supports drag and drop operations. When a drag
is in progress, the destination window can be activated by
hovering the drag icon over the task button for that window.
Alternatively, the current workspace can be changed by
hovering the drag icon over the desired workspace button.
When edge switching is enabled, the current workspace can
also be changed by bringing the drag icon to the screen edge.

## ADDRESS BAR

The task bar contains a command-line prompt called the address bar,
if **EnableAddressBar**=1. It is always shown when **ShowAddressBar**=1,
otherwise it is activated by **KeySysAddressBar**=`Alt+Ctrl+space`.
In it a shell command can be typed. On _Enter_ it is executed by the
**AddressBarCommand**=`/bin/sh`.  On _Control+Enter_ this command is
executed in a new terminal as given by **TerminalCommand**.
_Escape_ cancels editing the address bar command.

Commands are executed relative to the working directory of icewm.
This is shown by `pwd`. Change it with `cd`.  Without argument `cd`
defaults to the home directory. With one argument it is changed.
This argument is expanded when it starts with a dollar or tilde.
When it is equal to `-`, it reverts to the previous directory.

The address bar has a history that is navigable by _Up_ and _Down_.
This history is saved in a file `ahistory` in your icewm directory
and restored when icewm starts.

Completion is supported using _Tab_ or _Ctrl+I_. The leading command
is completed from directories in your PATH, while file arguments are
expanded from the location in the file system. In addition usernames
and environment variables can also be expanded. For example, `echo $TMP`
and _Tab_ may expand to `echo $TMPDIR` and `echo ~ro` and _Tab_ may
expand to `echo ~root`.

The address bar implements cut/copy/paste and these editing operations:

- Ctrl+a: select all
- Ctrl+backslash: deselect all
- Ctrl+u: delete selected or to line start
- Ctrl+v: paste selected
- Ctrl+w: delete selected or previous word
- Ctrl+x: cut selection
- Ctrl+c: copy selection
- Ctrl+i: completion
- Ctrl+Left: back a word
- Ctrl+Right: forward a word
- Ctrl+Shift+Backspace: delete to beginning
- Ctrl+Shift+Delete: delete to end
- Ctrl+Delete: delete word
- Ctrl+Backspace: delete previous word
- Shift+Delete: cut selection
- Shift+Insert: paste selected
- Tab: completion
- Left: move cursor left
- Right: move cursor right
- Home: move cursor to line start
- End: move cursor to line end
- Delete: delete next character
- Backspace: delete previous character

## WINDOW LIST

The window list window shows a list of all workspaces. For each
workspace it shows the window titles of the windows that are mapped
on it. The bottom entry reads `All Workspaces`. It holds the sticky
windows. These windows are mapped in all workspaces.

The window list window is normally hidden. Choose one of the following
four methods to make it visible:

- Select the bottom window list menu entry.
- Press the `KeySysWindowList=Ctrl+Alt+Esc` key.
- Press the right Windows key if `Win95Keys=1`
- Press the `DesktopWinListButton=2` mouse button in the root window.
- Press the middle mouse button in a workspace button on the task bar.

A single-click on a window entry selects it. A group of windows can
be selected by `Shift+Pointer_Button1` or by dragging with the left
mouse button. Use `Ctrl+Pointer_Button1` to individually select
windows in a multi-selection. A right mouse click over a selection
will popup the system menu for this selection.  To close the selected
windows, press `Delete`. Press `Shift+Delete` to forcefully kill them.
Right mouse click below the sticky windows for a menu with window
arranging actions.

Double-click on a workspace to switch to it.  Double-click on a window
to activate it.  Or navigate by arrow keys and press Enter.
The space bar toggles a selection of a window. `Ctrl+a` and `Ctrl+/`
will select the entire list of windows. `Ctrl+\\` deselects everything.
Press the first letter of a window title to navigate to it and select
it. If titles of multiple windows start with the same letter then
repeatedly pressing the first letter cycles over those windows.
`Home` selects the first entry and `End` the last. `PageUp` and
`PageDown` move up or down by ten entries. Combine this with the
`Shift` key to extend a selection over the range of motion.

## SYSTEM DIALOG

The system dialog offers quick access to a set of general controls.
It can lock the screen, suspend the system, logout or cancel a pending
logout, reboot the system, shutdown the system, show the window list,
restart icewm, show the about dialog, reload the winoptions file or
the keys file. It is activated by **KeySysDialog**=`Ctrl+Alt+Del`.
To cancel it, hit the Escape key.

## MAILBOX MONITORING

The task bar can show one or more icons to reflect the status of a
mailbox. The mailbox can be a local file or a remote POP or IMAP
account. For this a couple of options must be set. First,
`TaskBarShowMailboxStatus` must be enabled, which it is by default.
Then the location of the mailbox must be set.  Icewm first looks for
`MailBoxPath` in preferences. If this is unset, it looks at the
environment variables `MAILPATH` and `MAIL`.  `MailBoxPath` may
contain a space-separated list of mailboxes, while `MAILPATH` may
contain a colon-separated list of mailboxes.  If a mailbox starts
with a slash `/`, then it is a local file, otherwise a URL.
These are six examples of possible mailboxes:

    file:///var/spool/mail/captnmark
    file:///home/captnmark/Maildir/
    pop3://markus:%2f%40%3a@maol.ch/
    pop3s://markus:password@pop.gmail.com/
    imap://mathias@localhost/INBOX.Maillisten.icewm-user
    imaps://mathias:password@imap.gmail.com/INBOX

The POP3S and IMAPS schemes use `openssl` for TLS/SSL encryption.
Note that for IceWM to access Gmail you must first configure
your Gmail account to enable POP3 or IMAP access.
Make sure you have secure file permissions on your IceWM
preferences file and the directory that contains it.

Reserved characters in the password, like _slash_, _at_ and _colon_
can be specified using escape sequences with a hexadecimal encoding
like `%2f` for the slash or `%40` for the at sign.
For example, to hex-encode `!p@a%s&s~` use this Perl snippet:

    perl -e 'foreach(split("", $ARGV[0])) { printf "%%%02x", ord($_); };
    print "\n";' '!p@a%s&s~'

Which will print:

    %21%40%23%24%25%5e%26%2a%7e

This is the hex-encoded password. However, it is unwise to store a
password in your preferences. Consider a wallet extension for IceWM.

IceWM will check a mailbox periodically. The period in seconds can
be set by the `MailCheckDelay` option, which is 30 seconds by default.

Whenever new mail arrives, the mailbox icon will be highlighted.
The color will indicate if the mail has been read or not. Hovering
the mouse over the mailbox icon will show a tooltip with more details.
A command can be also be run on new mail. Set the `NewMailCommand`
option. Its environment will have these variables set by IceWM:

- ICEWM\_MAILBOX

    The mailbox index number of `MailBoxPath` starting from 1.

- ICEWM\_COUNT

    The total number of messages in this mailbox.

- ICEWM\_UNREAD

    The number of unread messages in this mailbox.

## KEYBOARD LAYOUT SWITCHING

To control keyboard layouts on the task bar, define in `preferences`
the option **KeyboardLayouts** to a comma-separated list of your
preferred keyboard layouts. For example:

    KeyboardLayouts = "de", "fr", "jp"

A keyboard layout can simply be a name. Usually this is a two-letter
country code. See the directory `/usr/share/X11/xkb/symbols` for
a list of available keyboard layouts for your system.  If it is
enclosed in double quotes, it can also be a space-separated list of
command-line arguments to an invocation of the `setxkbmap` program.

The first layout is the default. It will be installed when icewm starts.
The task bar will show the current keyboard layout. If an icon can
be found for the first two letters of the layout, then that icon
will be shown. Otherwise the first two letters of the name of the
layout will be shown.

Click on the current keyboard layout to cycle through all the
available keyboard layouts, or use the **KeySysKeyboardNext** key.
Click with the right mouse button to open a menu of all available
keyboard layouts.

It is also possible to configure a default keyboard layout for
each program individually in the [icewm-winoptions(5)](icewm-winoptions) file.
Whenever such a program receives input focus, icewm will install
this configured keyboard layout automatically. The keyboard status
on the task bar will be updated to reflect this.

Please note that for keyboard layout switching to work, the
`setxkbmap` program must be installed. To see your current
keyboard layout settings, do `setxkbmap -query`.

## KEYBOARD SHORTCUTS

**icewm** supports a large number of hotkeys to activate some behaviour
with a single key combination.  These are all configurable in the
`preferences` file.  Here we give their preferences name, followed by
their default value in double quotes, and a short descriptions of their
effect.

Note that all use one or more key modifiers. Icewm supports the
following modifiers: Alt, AltGr, Ctrl, Hyper, Meta, Shift, Super.
Setting **ModSuperIsCtrlAlt=1** makes the Super modifier an alias
for Ctrl+Alt.

- **KeyWinRaise**=`Alt+F1`

    Raises the window that currently has input focus.

- **KeyWinOccupyAll**=`Alt+F2`

    Makes the active window occupy all workspaces.

- **KeyWinLower**=`Alt+F3`

    Lowers the window that currently has input focus.

- **KeyWinClose**=`Alt+F4`

    Closes the active window.

- **KeyWinRestore**=`Alt+F5`

    Restores the active window to its visible state.

- **KeyWinNext**=`Alt+F6`

    Switches focus to the next window.

- **KeyWinPrev**=`Alt+Shift+F6`

    Switches focus to the previous window.

- **KeyWinMove**=`Alt+F7`

    Starts movement of the active window.

- **KeyWinSize**=`Alt+F8`

    Starts resizing of the active window.

- **KeyWinMinimize**=`Alt+F9`

    Iconifies the active window.

- **KeyWinMaximize**=`Alt+F10`

    Maximizes the active window with borders.

- **KeyWinMaximizeVert**=`Alt+Shift+F10`

    Maximizes the active window vertically.

- **KeyWinMaximizeHoriz**=`undefined`

    Maximizes the active window horizontally.

- **KeyWinFullscreen**=`Alt+F11`

    Maximizes the active window without borders.

- **KeyWinRollup**=`Alt+F12`

    Rolls up the active window.

- **KeyWinHide**=`Alt+Shift+F12`

    Hides the active window.

- **KeyWinMenu**=`Alt+space`

    Posts the window menu.

- **KeyWinArrangeNW**=`Ctrl+Alt+KP_7`

    Moves the active window to the top left corner of the screen.

- **KeyWinArrangeN**=`Ctrl+Alt+KP_8`

    Moves the active window to the top middle of the screen.

- **KeyWinArrangeNE**=`Ctrl+Alt+KP_9`

    Moves the active window to the top right of the screen.

- **KeyWinArrangeE**=`Ctrl+Alt+KP_6`

    Moves the active window to the middle right of the screen.

- **KeyWinArrangeSE**=`Ctrl+Alt+KP_3`

    Moves the active window to the bottom right of the screen.

- **KeyWinArrangeS**=`Ctrl+Alt+KP_2`

    Moves the active window to the bottom middle of the screen.

- **KeyWinArrangeSW**=`Ctrl+Alt+KP_1`

    Moves the active window to the bottom left of the screen.

- **KeyWinArrangeW**=`Ctrl+Alt+KP_4`

    Moves the active window to the middle left of the screen.

- **KeyWinArrangeC**=`Ctrl+Alt+KP_5`

    Moves the active window to the center of the screen.

- **KeyWinTileLeft**=""

    Let the active window occupy the left half of the screen.

- **KeyWinTileRight**=""

    Let the active window occupy the right half of the screen.

- **KeyWinTileTop**=""

    Let the active window occupy the top half of the screen.

- **KeyWinTileBottom**=""

    Let the active window occupy the bottom half of the screen.

- **KeyWinTileTopLeft**=""

    Let the active window occupy the top left quarter of the screen.

- **KeyWinTileTopRight**=""

    Let the active window occupy the top right quarter of the screen.

- **KeyWinTileBottomLeft**=""

    Let the active window occupy the bottom left quarter of the screen.

- **KeyWinTileBottomRight**=""

    Let the active window occupy the bottom right quarter of the screen.

- **KeyWinTileCenter**=""

    Let the active window occupy the center quarter of the screen.

- **KeyWinSmartPlace**=`Ctrl+Alt+Shift+KP_5`

    Smart place the active window.

- **KeySysWinMenu**=`Shift+Esc`

    Posts the system window menu.

- **KeySysWinNext**=`Alt+Esc`

    Give focus to the next window and raise it.

- **KeySysWinPrev**=`Alt+Shift+Esc`

    Give focus to the previous window and raise it.

- **KeySysDialog**=`Ctrl+Alt+Del`

    Opens the IceWM system dialog in the center of the screen.

- **KeySysMenu**=`Ctrl+Esc`

    Activates the IceWM root menu in the lower left corner.

- **KeySysWindowList**=`Alt+Ctrl+Esc`

    Opens the IceWM system window list in the center of the screen.

- **KeySysAddressBar**=`Alt+Ctrl+space`

    Opens the address bar in the task bar where a command can be typed.

- **KeySysWorkspacePrev**=`Alt+Ctrl+Left`

    Goes one workspace to the left.

- **KeySysWorkspaceNext**=`Alt+Ctrl+Right`

    Goes one workspace to the right.

- **KeySysWorkspaceLast**=`Alt+Ctrl+Down`

    Goes to the previous workspace.

- **KeySysWorkspacePrevTakeWin**=`Alt+Ctrl+Shift+Left`

    Takes the active window one workspace to the left.

- **KeySysWorkspaceNextTakeWin**=`Alt+Ctrl+Shift+Right`

    Takes the active window one workspace to the right.

- **KeySysWorkspaceLastTakeWin**=`Alt+Ctrl+Shift+Down`

    Takes the active window to the previous workspace.

- **KeySysWorkspace1**=`Alt+Ctrl+1`

    Goes to workspace 1.

- **KeySysWorkspace2**=`Alt+Ctrl+2`

    Goes to workspace 2.

- **KeySysWorkspace3**=`Alt+Ctrl+3`

    Goes to workspace 3.

- **KeySysWorkspace4**=`Alt+Ctrl+4`

    Goes to workspace 4.

- **KeySysWorkspace5**=`Alt+Ctrl+5`

    Goes to workspace 5.

- **KeySysWorkspace6**=`Alt+Ctrl+6`

    Goes to workspace 6.

- **KeySysWorkspace7**=`Alt+Ctrl+7`

    Goes to workspace 7.

- **KeySysWorkspace8**=`Alt+Ctrl+8`

    Goes to workspace 8.

- **KeySysWorkspace9**=`Alt+Ctrl+9`

    Goes to workspace 9.

- **KeySysWorkspace10**=`Alt+Ctrl+0`

    Goes to workspace 10.

- **KeySysWorkspace11**=`Alt+Ctrl+minus`

    Goes to workspace 11.

- **KeySysWorkspace12**=`Alt+Ctrl+equal`

    Goes to workspace 12.

- **KeySysWorkspace1TakeWin**=`Alt+Ctrl+Shift+1`

    Takes the active window to workspace 1.

- **KeySysWorkspace2TakeWin**=`Alt+Ctrl+Shift+2`

    Takes the active window to workspace 2.

- **KeySysWorkspace3TakeWin**=`Alt+Ctrl+Shift+3`

    Takes the active window to workspace 3.

- **KeySysWorkspace4TakeWin**=`Alt+Ctrl+Shift+4`

    Takes the active window to workspace 4.

- **KeySysWorkspace5TakeWin**=`Alt+Ctrl+Shift+5`

    Takes the active window to workspace 5.

- **KeySysWorkspace6TakeWin**=`Alt+Ctrl+Shift+6`

    Takes the active window to workspace 6.

- **KeySysWorkspace7TakeWin**=`Alt+Ctrl+Shift+7`

    Takes the active window to workspace 7.

- **KeySysWorkspace8TakeWin**=`Alt+Ctrl+Shift+8`

    Takes the active window to workspace 8.

- **KeySysWorkspace9TakeWin**=`Alt+Ctrl+Shift+9`

    Takes the active window to workspace 9.

- **KeySysWorkspace10TakeWin**=`Alt+Ctrl+Shift+0`

    Takes the active window to workspace 10.

- **KeySysWorkspace11TakeWin**=`Alt+Ctrl+Shift+minus`

    Takes the active window to workspace 11.

- **KeySysWorkspace12TakeWin**=`Alt+Ctrl+Shift+equal`

    Takes the active window to workspace 12.

- **KeySysTileVertical**=`Alt+Shift+F2`

    Tiles all windows from left to right maximized vertically.

- **KeySysTileHorizontal**=`Alt+Shift+F3`

    Tiles all windows from top to bottom maximized horizontally.

- **KeySysCascade**=`Alt+Shift+F4`

    Makes a horizontal cascade of all windows which are maximized vertically.

- **KeySysArrange**=`Alt+Shift+F5`

    Rearranges the windows.

- **KeySysUndoArrange**=`Alt+Shift+F7`

    Undoes arrangement.

- **KeySysArrangeIcons**=`Alt+Shift+F8`

    Rearranges icons.

- **KeySysMinimizeAll**=`Alt+Shift+F9`

    Minimizes all windows.

- **KeySysHideAll**=`Alt+Shift+F11`

    Hides all windows.

- **KeySysShowDesktop**=`Alt+Ctrl+d`

    Unmaps all windows to show the desktop.

- **KeySysCollapseTaskBar**=`Alt+Ctrl+h`

    Hides the task bar.

- **KeyTaskBarSwitchNext**=`undefined`

    Switches to the next window in the task bar.

- **KeyTaskBarSwitchPrev**=`undefined`

    Switches to the previous window in the task bar.

- **KeyTaskBarMoveNext**=`undefined`

    Moves the task bar button of the current window
    right.

- **KeyTaskBarMovePrev**=`undefined`

    Moves the task bar button of the current window
    left.

- **KeySysWinListMenu**=`undefined`

    Shows the window list menu.

- **KeySysKeyboardNext**=`undefined`

    Switch to the next keyboard layout in the KeyboardLayouts list.

- **KeySysSwitchNext**=`Alt+Tab`

    Opens the `QuickSwitch` popup (see ["INPUT FOCUS"](#input-focus))
    and/or moves the selector in the `QuickSwitch` popup.

- **KeySysSwitchLast**=`Alt+Shift+Tab`

    Works like `KeySysSwitchNext` but moving in the
    opposite direction.

- **KeySysSwitchClass**=`Alt+grave`

    Is like `KeySysSwitchNext` but only for windows
    with the same WM\_CLASS property as the currently focused window.

## MOUSE BINDINGS

You can control windows by a modified mouse button press:

- **MouseWinMove**=`Alt+Pointer_Button1`

    Moves the window under the mouse over the screen.

- **MouseWinSize**=`Alt+Pointer_Button3`

    Resizes the window.  Keep the key and button pressed.
    To enlarge the window move the mouse button away from the center.  To
    shrink it move towards the centre.

- **MouseWinRaise**=`Ctrl+Alt+Pointer_Button1`

    Raises the window under the mouse.

- **MouseWinLower**=`Ctrl+Alt+Pointer_Button1`

    Lowers the window under the mouse.
    If this is equal to `MouseWinRaise` and the window can be raised
    then `MouseWinRaise` takes preference over `MouseWinLower`.

- **MouseWinTabbing**="Shift+Pointer\_Button2"

    Mouse binding to create tabs.
    Drag the title bar with this button over another title bar.
    When they start to flash, release the button to merge the frame tabs.

The title frame of a window also listens for mouse clicks.  A left
double-click maximizes the window (`TitleBarMaximizeButton=1`).
When Shift is also pressed it only maximizes vertically.
Press Alt+Shift to maximize horizontally.

Middle double-clicking rolls up the window (`TitleBarRollupButton=2`).
Also press Shift to maximize horizontally. If **TitleBarRollupButton**
is either 4 or 5 then the scroll wheel controls rolling up or down.

Press a mouse button on the title bar and drag it to move the window.
A `Alt+Pointer_Button1` click lowers the window.

When the mouse is on the window frame then a left click raises the
window.  Dragging with the left button down resizes the window.
Clicking the right button pops up the context menu.  Dragging with the
right button moves the window.

Double-clicking on the frame border (or corner) maximizes just that side
of the window. Another double-click restores that side. Double-clicking
on the border can also undo a maximization in that dimension.

Clicking on the desktop activates a menu.  The middle button shows the
window list (`DesktopWinListButton=2`).  The right button shows the
root menu (`DesktopMenuButton=3`). If you press `Ctrl+Alt` then
the mouse wheel will focus all applications in turn.

## SIGNALS

**icewm** supports the following signals:

- **SIGHUP**

    **icewm** will restart itself. It is a way to reload the configuration.

- **SIGINT**, **SIGTERM**

    **icewm** will cease to manage application windows and terminate.

- **SIGQUIT**

    **icewm** will initiate the logout procedure.  If a `LogoutCommand`
    preferences option was configured it will be executed.

- **SIGUSR2**

    Toggle the logging of X11 events, if `logevents` was configured.

## ENVIRONMENT VARIABLES

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

## FILES

## CONFIGURATION DIRECTORIES

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
    [icewm-session(1)](icewm-session) will load those expanded lines that contain a name,
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
    follows a shell command-line that will be executed by **icewm** whenever
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
    to control the **icewm** focus behaviour and the applets that are
    started in the task bar.  The **icewm** installation will provide a
    default `preferences` file, which can be copied to the **icewm** user
    configuration directory and modified.

    See [icewm-preferences(5)](icewm-preferences).

- `prefoverride`

    Settings which override the settings from a theme.  Some of the **icewm**
    configuration options from the preferences file that control the
    look-and-feel may be overridden by the theme, if the theme designer
    thinks this is desirable.  However, this `prefoverride` file will again
    override this for a few specific options of your choosing.  It is safe
    to leave this file empty initially.

    See [icewm-prefoverride(5)](icewm-prefoverride).

- `programs`

    An automatically generated menu of applications.  This could be used by
    [wmconfig(1)](https://manned.org/wmconfig.1), menu or similar programs to give easy access to all the
    desktop applications that are installed on the system.

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
    last component is a shell command-line that will be executed whenever
    the user presses the icon in the toolbar.  For example, the following
    line in toolbar will create a button with tool tip `Mozilla Firefox`
    with the `firefox` icon that launches [firefox(1)](https://manned.org/firefox.1) when clicked:

        prog  "Mozilla Firefox"  firefox  /usr/bin/firefox --private-window

    See [icewm-toolbar(5)](icewm-toolbar).

- `winoptions`

    Contains settings to control window appearance and behaviour that are
    specific to applications or groups of applications.  Options can control
    the border, whether it appears on the task bar, the window list, the
    system tray and the workspaces.  Also its layer, geometry, whether it
    can be moved, resized and closed.

    See [icewm-winoptions(5)](icewm-winoptions).

- `startup`

    Contains commands to be executed on **icewm** startup.  This is an
    executable script with commands to tweak X11 settings and launch some
    applications that need to be active whenever **icewm** is started.
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

- `cursors`

    May contain cursor icons in the XPM image format. These overrule cursors
    provided by a theme. There are 3 direction cursors: `left.xpm`,
    `right.xpm`, `move.xpm`, 8 resize cursors: `sizeR.xpm`, `sizeTR.xpm`,
    `sizeT.xpm`, `sizeTL.xpm`, `sizeL.xpm`, `sizeBL.xpm`, `sizeB.xpm`,
    `sizeBR.xpm`, and 4 scroll cursors: `scrollL.xpm`, `scrollR.xpm`,
    `scrollU.xpm`, and `scrollD.xpm`.
    By default an XPM header defines four dimensions: width, height, colors
    and chars-per-pixel. For cursors this must be extended to six. The last
    two are the _x-hotspot_ and the _y-hotspot_. These define which point
    in the XPM image is the sensitive point for the mouse pointer.

- `icons`

    Contains icons for applications and keyboard layouts. These can be in
    XPM, PNG or SVG format.  The filename of an _application icon_ may
    follow a specific naming pattern, like `app_32x32.xpm`.  They start
    with a base name, which usually is just a single word.  Then follows
    an underscore, followed by a size specification, as in `SIZExSIZE`.
    This is followed by a dot and the file extension, where the extension
    denotes the icon image format.  Common sizes are 16, 32 and 48.
    This depends on the respective `IconSize` preferences options.

- `ledclock`

    Pictures of digits for the LED clock which is displayed in the
    bottom-right corner of the task bar.  These can be seen when the
    `TaskBarShowClock` and `TaskBarClockLeds` options are both set to 1.

- `mailbox`

    Icons that are used to display different states of the mailbox applet
    in the task bar.  There are five states and each has its own icon:
    `mail.xpm`, `newmail.xpm`, `unreadmail.xpm`, `nomail.xpm`,
    `errmail.xpm`.

- `sounds`

    Audio files that are played by [icesound(1)](icesound) on GUI events.  These
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
    additional files that have a `.theme` file name extension and that
    contain tweaks of the `default.theme` file.
    How to create a theme is explained in the
    [IceWM Theme Creation Howto](https://ice-wm.org/themes).

- `workspace`

    If `PagerShowPreview` is disabled, icewm looks in the `workspace`
    directory for images to draw on a workspace button. The image filename
    should have the name of the workspace. The image extension is optional.

## OPACITY

IceWM supports window opacity and transparency in connection with an
external compositor like [compton(1)](https://manned.org/compton.1) or [picom(1)](https://manned.org/picom.1).
If a client window sets the `_NET_WM_WINDOW_OPACITY` property on
its window, then **icewm** will copy this to the outer frame window,
where the compositor will read it and adjust the opacity accordingly.

The opacity can also be set in the [icewm-winoptions(5)](icewm-winoptions) file.
[icesh(1)](icesh) can control the opacity level of running applications.

The \_NET\_WM\_WINDOW\_TYPE properties that **icewm** sets on its windows
are _DIALOG_, _NOTIFICATION_, _POPUP\_MENU_ and _TOOLTIP_. The output
of `icesh windows` shows their WM\_CLASS values. These can be helpful
to configure compton.

## EXAMPLES

Examples of the above configuration files can be found in the default
installation path or in the system-wide defaults.  See the output of
`icewm --directories` for their locations.

## CONFORMING TO

ICCCM 2.0: partial.  NetWM/EWMH: extensive.
See the file `COMPLIANCE` in the distribution for full details.

## SEE ALSO

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
[setxkbmap(1)](https://manned.org/setxkbmap.1),
[Xorg(1)](https://manned.org/Xorg.1),
[Xserver(1)](https://manned.org/Xserver.1),
[xinit(1)](https://manned.org/xinit.1),
[xprop(1)](https://manned.org/xprop.1),
[xwininfo(1)](https://manned.org/xwininfo.1),
[wmctrl(1)](https://manned.org/wmctrl.1).

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
