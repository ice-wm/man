---
title: "icewm-preferences(5)"
---
## NAME

    icewm-preferences - icewm preferences configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/preferences
    $XDG_CONFIG_HOME/icewm/preferences
    $HOME/.icewm/preferences
    /etc/icewm/preferences
    /usr/share/icewm/preferences

## DESCRIPTION

Contains general settings like paths, colors and fonts, but also options
to control the **icewm** focus behaviour and the applets that are
started in the task bar.  The **icewm** installation will provide a
default `preferences` file, that can be copied to the **icewm** user
configuration directory and modified.

## FORMAT

## FOCUS AND BEHAVIOR

The following preferences affect focus and general behavior of
[icewm(1)](icewm):

- **Alpha**=0

    Use a 32-bit visual for alpha blending

- **Synchronize**=0

    Synchronize X11 for debugging (slow)

- **LogEvents**=0

    Enable event logging for debugging

- **OutputFile**=""

    Redirect all output to _FILE_.
    A leading tilde or environment variable is expanded.
    This file is truncated on startup if it exceeds 5 KB.

- **Splash**=""

    Splash image on startup (IceWM.jpg)

- **Trace**=""

    Enable tracing for the given list of modules.
    Modules that are traceable include **conf, font, icon, prog, systray**.

- **ClickToFocus**=1

    Focus windows by clicking in them.

- **FocusOnAppRaise**=0

    Focus windows when applications request that they be raised.

- **RequestFocusOnAppRaise**=1

    Request focus (flashing in taskbar) when application requests raise.

- **RaiseOnFocus**=1

    Raise windows when focused.

- **FocusOnClickClient**=1

    Focus window when client area clicked.

- **RaiseOnClickClient**=1

    Raise window when client area clicked.

- **RaiseOnClickTitleBar**=1

    Raise window when title bar is clicked.

- **RaiseOnClickButton**=1

    Raise window when frame button is clicked.

- **RaiseOnClickFrame**=1

    Raise window when frame border is clicked.

- **LowerOnClickWhenRaised**=0

    Lower the active window when clicked again.

- **PassFirstClickToClient**=1

    Pass focusing click on client area to client.

- **FocusChangesWorkspace**=0

    Change to the workspace of newly focused windows.

- **FocusCurrentWorkspace**=0

    Move newly focused windows to current workspace.

- **FocusOnMap**=1

    Focus normal window when initially mapped.

- **FocusOnMapTransient**=0

    Focus dialog window when initially mapped.

- **FocusOnMapTransientActive**=1

    Focus dialog window when initially mapped only if parent frame focused.

- **MapInactiveOnTop**=1

    Put new windows on top even if not focusing them.

- **PointerColormap**=1

    Colormap focus follows pointer.

- **DontRotateMenuPointer**=1

    Don't rotate the cursor for popup menus.

- **LimitSize**=1

    Limit size of windows to screen.

- **LimitPosition**=1

    Limit position of windows to screen.

- **LimitByDockLayer**=0

    Let the Dock layer limit the workspace (incompatible with GNOME Panel).

- **ConsiderHBorder**=0

    Consider border frames when maximizing horizontally.

- **ConsiderVBorder**=0

    Consider border frames when maximizing vertically.

- **ConsiderSizeHintsMaximized**=1

    Consider XSizeHints if frame is maximized.
    Turning this off allows the titlebar to cover the width of the screen.

- **CenterMaximizedWindows**=0

    Center maximized windows that can't fit the screen (like terminals).

- **HideBordersMaximized**=0

    Hide window borders if window is maximized.

- **SizeMaximized**=0

    Maximized windows can be resized.

- **ShowMoveSizeStatus**=1

    Show position status window during move/resize.

- **ShowWorkspaceStatus**=1

    Show name of current workspace while switching.

- **MinimizeToDesktop**=0

    Display mini-icons on desktop for minimized windows.

- **MiniIconsPlaceHorizontal**=0

    Place the mini-icons horizontal instead of vertical.

- **MiniIconsRightToLeft**=0

    Place new mini-icons from right to left.

- **MiniIconsBottomToTop**=0

    Place new mini-icons from bottom to top.

- **StrongPointerFocus**=0

    Always maintain focus under mouse window. Makes some keyboard support
    non-functional or unreliable.

- **OpaqueMove**=1

    Opaque window move.

- **OpaqueResize**=1

    Opaque window resize.

- **ManualPlacement**=0

    Windows initially placed manually by user.

- **SmartPlacement**=1

    Smart window placement (minimal overlap).

- **HideTitleBarWhenMaximized**=0

    Hide title bar when maximized.

- **CenterLarge**=0

    Center large windows.

- **CenterTransientsOnOwner**=1

    Center dialogs on owner window.

- **MenuMouseTracking**=0

    Menus track mouse even with no mouse buttons held.

- **AutoRaise**=0

    Raise windows when the mouse pointer enters, after a delay of
    _AutoRaiseDelay_ milliseconds.  Note that `RaiseOnFocus=1`
    may interfere.

- **DelayPointerFocus**=1

    Delay pointer focusing when mouse moves.

- **Win95Keys**=1

    Support the Windows/Super key modifier to activate special functions.
    The left Super key toggles the Start menu, while the right Super key
    toggles the Window list window.

- **ModSuperIsCtrlAlt**=0

    Treat the Super/Win key modifier as a synonym for the Ctrl+Alt modifier
    combination. The default key bindings have many occurrences of Ctrl+Alt.
    If you enable this, then the Super modifier is an alternative way to
    activate them.

- **UseMouseWheel**=0

    Support mouse wheel. When pressing Ctrl+Alt rotating the mouse wheel
    on the root window will cycle the focus over the windows.

- **TaskBarTaskGrouping**=0

    Group applications with the same class name under a single task button.
    0 disables it, 1 shows the number of windows, 2 shows bread crumbs,
    3 shows a number + bread crumbs.

- **ShowPopupsAbovePointer**=0

    Show popup menus above mouse pointer.

- **ReplayMenuCancelClick**=0

    Send the clicks outside menus to target window.

- **ClientWindowMouseActions**=1

    Allow mouse actions on client windows. This is buggy with some programs.

- **GrabRootWindow**=1

    Manage root window (EXPERIMENTAL - normally enabled!).

- **SnapMove**=1

    Snap to nearest screen edge/window when moving windows.

- **SnapDistance**=8  \[0-64\]

    Distance in pixels before windows snap together.

- **ArrangeWindowsOnScreenSizeChange**=1

    Automatically arrange windows when screen size changes.

- **AllowFullscreen**=1

    Allow to switch a window to fullscreen.

- **FullscreenUseAllMonitors**=0

    Span over all available screens if window goes into fullscreen.

- **MsgBoxDefaultAction**=0  \[0-1\]

    Preselect to Cancel (0) or the OK (1) button in message boxes.

- **NetWorkAreaBehaviour**=0  \[0-2\]

    NET\_WORKAREA behaviour: 0 (single/multi-monitor with STRUT information,
    like metacity), 1 (always full desktop), 2 (single monitor with STRUT,
    multi-monitor without STRUT).

## QUICK SWITCH

- **QuickSwitch**=1

    Enable Alt+Tab window switching.

- **QuickSwitchToMinimized**=1

    Enable Alt+Tab to minimized windows.

- **QuickSwitchToHidden**=1

    Enable Alt+Tab to hidden windows.

- **QuickSwitchToUrgent**=1

    Prioritize Alt+Tab to urgent windows.

- **QuickSwitchToAllWorkspaces**=0

    Include windows from all workspaces in Alt+Tab.

- **QuickSwitchGroupWorkspaces**=1

    Group windows by workspace together in Alt+Tab.

- **QuickSwitchPersistence**=0

    Time in seconds to remember the state of Alt+Tab.

- **QuickSwitchPreview**=0

    Use a QuickSwitch that shows previews of applications.

- **QuickSwitchRaiseCandidate**=0

    Raise a selected window while Alt+Tabbing in the QuickSwitch.

- **QuickSwitchAllIcons**=1

    Show all reachable icons when quick switching.

- **QuickSwitchTextFirst**=0

    Show the window title above (all reachable) icons.

- **QuickSwitchSmallWindow**=0

    Create a smaller QuickSwitch window of 1/3 screen width.

- **QuickSwitchVertical**=1

    Place the icons and titles vertical instead of horizontal.

- **QuickSwitchHugeIcon**=0

    Show the huge (48x48) of the window icon for the active window.

- **QuickSwitchFillSelection**=0

    Fill the rectangle highlighting the current icon.

## EDGE SWITCHING

- **EdgeSwitch**=0

    Workspace switches by moving mouse to left/right screen edge.

- **HorizontalEdgeSwitch**=0

    Workspace switches by moving mouse to left/right screen edge.

- **VerticalEdgeSwitch**=0

    Workspace switches by moving mouse to top/bottom screen edge.

- **ContinuousEdgeSwitch**=1

    Workspace switches continuously when moving mouse to screen edge.

- **EdgeResistance**=32  \[0-10000\]

    Resistance in pixels when trying to move windows off the screen (10000 =
    infinite).

## TASK BAR

The following preferences affect the [icewm(1)](icewm) task bar:

- **ShowTaskBar**=1

    Show task bar.

- **TaskBarAtTop**=0

    Task bar at top of the screen.

- **TaskBarKeepBelow**=0

    Keep the task bar below regular windows.

- **TaskBarAutoHide**=0

    Auto hide task bar after delay.

- **TaskBarFullscreenAutoShow**=1

    Auto show task bar when fullscreen window active.

- **TaskBarShowClock**=1

    Show clock on task bar.

- **TaskBarShowAPMStatus**=0

    Show battery status monitor on task bar.

- **TaskBarShowAPMAuto**=1

    Enable TaskBarShowAPMStatus if a battery is present.

- **TaskBarShowAPMTime**=1

    Show battery status on task bar in time-format

- **TaskBarShowAPMGraph**=1

    Show battery status in graph mode.

- **TaskBarShowMailboxStatus**=1

    Show mailbox status on task bar.

- **TaskBarMailboxStatusBeepOnNewMail**=0

    Beep when new mail arrives.

- **TaskBarMailboxStatusCountMessages**=0

    Count messages in mailbox.

- **TaskBarShowWorkspaces**=1

    Show workspace switching buttons on task bar.

- **TaskBarShowWindows**=1

    Show windows on the taskbar.

- **TaskBarShowShowDesktopButton**=1

    Show 'show desktop' button on taskbar. If set to 2, it will move the icon to the right side, after the clock.

- **ShowEllipsis**=1

    Show Ellipsis in taskbar items.

- **TaskBarShowTray**=1

    Show windows in the tray.

- **TaskBarEnableSystemTray**=1

    Enable the system tray in the taskbar.

- **TrayShowAllWindows**=1

    Show windows from all workspaces on tray.

- **TaskBarShowTransientWindows**=1

    Show transient (dialogs, ...) windows on task bar.

- **TaskBarShowAllWindows**=0

    Show windows from all workspaces on task bar.

- **TaskBarShowWindowIcons**=1

    Show icons of windows on task buttons of the task bar.

- **TaskBarShowWindowTitles**=1

    Show titles of windows on task buttons of the task bar.

- **TaskBarShowStartMenu**=1

    Show 'Start' menu on task bar.

- **TaskBarShowWindowListMenu**=1

    Show 'window list' menu on task bar.

- **TaskBarShowCPUStatus**=1

    Show CPU status on task bar (Linux & Solaris).

- **CPUStatusShowRamUsage**=1

    Show RAM usage in CPU status tool tip.

- **CPUStatusShowSwapUsage**=1

    Show swap usage in CPU status tool tip.

- **CPUStatusShowAcpiTemp**=1

    Show ACPI temperature in CPU status tool tip.

- **CPUStatusShowAcpiTempInGraph**=0

    Show ACPI temperature in CPU status bar.

- **CPUStatusShowCpuFreq**=1

    Show CPU frequency in CPU status tool tip.

- **NetStatusShowOnlyRunning**=0

    Show network status only for connected devices, such as an active Ethernet link
    or associated wireless interface. If false, any network interface that has been
    brought up will be displayed.

- **TaskBarShowMEMStatus**=1

    Show memory usage status on task bar (Linux only).

- **TaskBarShowNetStatus**=1

    Show network status on task bar (Linux only).

- **TaskBarShowCollapseButton**=0

    Show a button to collapse the taskbar.

- **TaskBarDoubleHeight**=0

    Use double-height task bar.

- **TaskBarWorkspacesLeft**=1

    Place workspace pager on left, not right.

- **TaskBarWorkspacesTop**=0

    Place workspace pager on top row when using dual-height taskbar.

- **TaskBarWorkspacesLimit**=""

    Limit the number of taskbar workspaces buttons that are shown on the
    workspaces pane of the taskbar. If the numeric value has a `p` suffix
    then the limitation is in pixels. A `%` suffix limits by percentage of
    desktop width. By default a `B` suffix is assumed for number of buttons.

- **TaskBarUseMouseWheel**=1

    Enable mouse wheel cycling over workspaces and task buttons in taskbar.

- **PagerShowPreview**=1

    Show a mini desktop preview on each workspace button.

- **PagerShowWindowIcons**=1

    Draw window icons inside large enough preview windows on pager (if PagerShowPreview=1).

- **PagerShowMinimized**=1

    Draw even minimized windows as unfilled rectangles (if PagerShowPreview=1).

- **PagerShowBorders**=1

    Draw border around workspace buttons (if PagerShowPreview=1).

- **PagerShowLabels**=1

    Show workspace name label on workspace button (if PagerShowPreview=1)

- **PagerShowNumbers**=1

    Show number of workspace on workspace button (if PagerShowPreview=1).

- **TaskBarLaunchOnSingleClick**=1

    Execute taskbar applet commands (like MailCommand, ClockCommand, ...) on single click.

- **EnableAddressBar**=1

    Enable address bar functionality in taskbar.

- **ShowAddressBar**=1

    Show address bar in task bar.

- **MultiByte**=1

    Overrides automatic multiple byte detection.

- **ConfirmLogout**=1

    Confirm logout.

- **ShapesProtectClientWindow**=1

    Don't cut client windows by shapes set trough frame corner pixmap.

- **XRRDisable**=1

    Disable use of new XRANDR API for dual head (nvidia workaround).

- **PreferFreetypeFonts**=1

    Favour Xft fonts over core X11 fonts where possible.

- **MailBoxPath**=""

    A list of paths of your mailboxes separated by spaces.
    If this is empty, $MAILPATH or $MAIL is used instead.

    Path to a mbox file. Remote mail boxes are accessed by specifying an URL
    using the Common Internet Scheme Syntax (RFC 1738):

        `scheme://[user[:password]@]server[:port][/path]`.

    Supported schemes are `pop3`, `imap` and `file`.  When the scheme is
    omitted `file://` is prepended silently. IMAP subfolders can be
    accessed by using the  path component.  Reserved characters like
    _slash_ (`/`), _at_ (`@`) and _colon_ (`:`) can be specified using
    escape sequences with a hexadecimal encoding like `%2f` for the slash
    or `%40` for the at sign.  For example:

        file:///var/spool/mail/captnmark
        pop3://markus:%2f%40%3a@maol.ch/
        imap://mathias@localhost/INBOX.Maillisten.icewm-user

- **NetworkStatusDevice**="eth0 wlan0"

    Network devices for which to show status.

- **TimeFormat**="%X"

    The clock time format. See the strftime manpage for the meaning of all
    the percent options. It is possible to define multiple clocks for
    different time zones in a single _TimeFormat_.  A new clock is defined
    by the beginning of the string, and by each time zone specification
    that starts with `TZ=...`, followed by a space. For example,
    **TimeFormat**=`%X TZ=Asia/Aden %T TZ=Asia/Baku %T` defines 3 clocks.

- **TimeFormatAlt**=""

    Alternate Clock Time format shown every other second.

- **DateFormat**="%c"

    Clock Date format for tooltip (strftime format string).

- **DockApps**="right high desktop"

    Support DockApps (right, left, center, down, high, above, dock, ontop,
    normal, below, desktop, or empty to disable). The first five control
    positioning, while the next six set the layer. Control with Ctrl+Mouse.

- **XRRPrimaryScreenName**=""

    Screen/output name of the primary screen.

- **AcpiIgnoreBatteries**=""

    List of battery names (directories) in /proc/acpi/battery to ignore.
    Useful when more slots are built-in, but only one battery is used.

- **TaskBarCPUSamples**=20  \[2-1000\]

    The width of the CPU Monitor applet in pixels.

- **TaskBarMEMSamples**=20  \[2-1000\]

    The width of the Memory Monitor applet in pixels.

- **TaskBarNetSamples**=20  \[2-1000\]

    The width of the Net Monitor applet in pixels.

- **TaskbarButtonWidthDivisor**=3  \[1-25\]

    Default number of tasks in taskbar.

- **TaskBarWidthPercentage**=100  \[0-100\]

    Task bar width as percentage of the screen width.

- **TaskBarJustify**="left"

    Taskbar justify left, right or center.

- **TaskBarApmGraphWidth**=10  \[1-1000\]

    Width of battery Monitor.

- **XineramaPrimaryScreen**=0  \[0-63\]

    Primary screen for xinerama (taskbar, ...).

- **KeyboardLayouts**=""

    A comma-separated list of keyboard layouts.
    A layout may be enclosed in double quotes.
    Each layout is a name with optional arguments,
    that is to be parsed by the `setxkbmap` program.
    To support changing keyboard layouts, the
    `setxkbmap` program must be installed.
    The first in the list is the default layout.
    Programs may have their own keyboard layout
    defined in the `winoptions` file.
    The first two letters of a layout are used
    to locate an icon image file.

## MENUS

- **AutoReloadMenus**=1

    Reload menu files automatically.

- **ShowProgramsMenu**=0

    Show programs submenu.

- **ShowSettingsMenu**=1

    Show settings submenu.

- **ShowFocusModeMenu**=1

    Show focus mode submenu.

- **ShowThemesMenu**=1

    Show themes submenu.

- **ShowLogoutMenu**=1

    Show logout menu.

- **ShowHelp**=1

    Show the help menu item.

- **ShowLogoutSubMenu**=1

    Show logout submenu.

- **ShowAbout**=1

    Show the about menu item.

- **ShowRun**=1

    Show the run menu item.

- **ShowWindowList**=1

    Show the window menu item.

- **MenuMaximalWidth**=0  \[0-16384\]

    Maximal width of popup menus,  2/3 of the screen's width if set to zero.

- **NestedThemeMenuMinNumber**=25  \[0-1234\]

    Minimal number of themes after which the Themes menu becomes nested (0=disabled).

## TIMINGS

- **DelayFuzziness**=10  (0-100)

    Delay fuzziness, to allow merging of multiple timer timeouts into one
    (notebook power saving).

- **ClickMotionDistance**=4  \[0-32\]

    Pointer motion distance before click gets interpreted as drag.

- **ClickMotionDelay**=200  \[0-2000\]

    Delay before click gets interpreted as drag.

- **MultiClickTime**=400  \[0-5000\]

    Multiple click time.

- **MenuActivateDelay**=40  \[0-5000\]

    Delay before activating menu items.

- **SubmenuMenuActivateDelay**=300  \[0-5000\]

    Delay before activating menu submenus.

- **ToolTipIcon**=1

    Show an application icon in toolbar and tray tooltips.

- **ToolTipDelay**=1000  \[0-5000\]

    Delay before tooltip window is displayed.

- **ToolTipTime**=0  \[0-60000\]

    Time before tooltip window is hidden (0 means never).

- **AutoHideDelay**=300  \[0-5000\]

    Delay before task bar is hidden.

- **AutoShowDelay**=500  \[0-5000\]

    Delay before task bar is shown.

- **AutoRaiseDelay**=400  \[0-5000\]

    Delay before windows are auto raised if `AutoRaise=1`.

- **PointerFocusDelay**=200  \[0-1000\]

    Delay for pointer focus switching.

- **EdgeSwitchDelay**=600  \[0-5000\]

    Screen edge workspace switching delay.

- **ScrollBarStartDelay**=500  \[0-5000\]

    Initial scroll bar autoscroll delay.

- **ScrollBarDelay**=30  \[0-5000\]

    Scroll bar autoscroll delay.

- **AutoScrollStartDelay**=500  \[0-5000\]

    Auto scroll start delay.

- **AutoScrollDelay**=60  \[0-5000\]

    Auto scroll delay.

- **WorkspaceStatusTime**=2500  \[0-2500\]

    Time before workspace status window is hidden.

- **MailCheckDelay**=30  \[0-86400\]

    Delay between new-mail checks. (seconds).

- **TaskBarCPUDelay**=500  \[10-3600000\]

    Delay between CPU Monitor samples in ms.

- **TaskBarMEMDelay**=500  \[10-3600000\]

    Delay between Memory Monitor samples in ms.

- **TaskBarNetDelay**=500  \[10-3600000\]

    Delay between Net Monitor samples in ms.

- **FocusRequestFlashTime**=0  \[0-86400\]

    Number of seconds the taskbar app will blink when requesting focus (0 = forever).

- **FocusRequestFlashInterval**=250  \[0-30000\]

    Taskbar blink interval (ms) when requesting focus (0 = blinking disabled).

- **BatteryPollingPeriod**=10  \[2-3600\]

    Delay between power status updates (seconds).

- **PingTimeout**=3  \[0-86400\]

    Timeout in seconds for applications to respond to the \_NET\_WM\_PING protocol.

## BUTTONS AND KEYS

- **UseRootButtons**=255  \[0-255\]

    Bitmask of root window button click to use in window manager.

- **ButtonRaiseMask**=1  \[0-255\]

    Bitmask of buttons that raise the window when pressed.

- **DesktopWinMenuButton**=0  \[0-20\]

    Desktop mouse-button click to show the window list menu.

- **DesktopWinListButton**=2 # \[0-20\]

    Desktop mouse-button click to show the window list

- **DesktopMenuButton**=3  \[0-20\]

    Desktop mouse-button click to show the root menu.

- **TitleBarMaximizeButton**=1  \[0-5\]

    Title bar mouse-button double-click to maximize the window to full
    screen with the frame border visible.
    Press Shift to maximize only in the vertical direction.
    Press Alt+Shift to maximize only in the horizontal direction.

- **TitleBarRollupButton**=2  \[0-5\]

    Title bar mouse-button double-click to rollup the window.
    Press Shift to maximize in the horizontal direction.

## WORKSPACES

- **WorkspaceNames**=" 1 ", " 2 ", " 3 ", " 4 "

    Create four workspaces with names ` 1 `, ` 2 `, ` 3 ` and ` 4 `.

## PATHS

- **IconPath**="/usr/local/share/icons:/usr/local/share/pixmaps:/usr/share/icons:/usr/share/pixmaps"

    Icon search path (colon separated). Also, the icons/ subdirectory in
    IceWM resource folders are searched first.

- **IconThemes**="\*:-HighContrast"

    List of icon themes (colon separated), acting as additional filter of
    icon subdirectories in any of the **IconPath** folders. Expressions can be
    wildcards, also special wildcards (starting with **-**) can exclude matched
    themes from selection.

- **MailBoxPath**=""

    A colon separated list of paths of your mailboxes.
    If this is empty, $MAILPATH or $MAIL is used instead.

## PROGRAMS

- **MailCommand**="xterm -name mutt -e mutt"

    Command to run on mailbox.

- **MailClassHint**="mutt.XTerm"

    **WM\_CLASS** to allow **runonce** for **MailCommand**.

- **NewMailCommand**=""

    Command to run when new mail arrives.

- **LockCommand**=""

    Command to lock display/screensaver.

- **ClockCommand**="xclock -name icewm -title Clock"

    Command to run on clock.

- **ClockClassHint**="icewm.XClock"

    **WM\_CLASS** to allow **runonce** for **ClockCommand**.

- **RunCommand**=""

    Command to select and run a program.

- **OpenCommand**=""

    Command to open a file or directory from the Start menu.

- **TerminalCommand**="xterm"

    Terminal emulator must accept -e option.

- **LogoutCommand**=""

    Command to start logout.

- **LogoutCancelCommand**=""

    Command to cancel logout.

- **ShutdownCommand**="/bin/sh -c "{ test -e /run/systemd/system && systemctl poweroff \|\| loginctl poweroff; }""

    Command to shutdown the system.

- **RebootCommand**="/bin/sh -c "{ test -e /run/systemd/system && systemctl reboot \|\| loginctl reboot; }""

    Command to reboot the system.

- **SuspendCommand**="test -e /run/systemd/system && systemctl suspend \|\| loginctl suspend"

    Command to send the system to standby mode

- **SuspendCommand**="test -e /run/systemd/system && systemctl hibernate \|\| loginctl hibernate"

    Command to hibernate the system.

- **CPUStatusCommand**="xterm -name top -title Process\\ Status -e top"

    Command to run on CPU status.

- **CPUStatusClassHint**="top.XTerm"

    **WM\_CLASS** to allow **runonce** for **CPUStatusCommand**.

- **CPUStatusCombine**=1  0/1

    Combine all CPUs to one.

- **NetStatusCommand**="xterm -name netstat -title 'Network Status' -e netstat -c"

    Command to run on Net status.

- **NetStatusClassHint**="netstat.XTerm"

    **WM\_CLASS** to allow **runonce** for **NetStatusCommand**.

- **AddressBarCommand**=""

    Command to run for address bar entries.

- **InputIgnorePrefix**="nohup\|(nice\[\[:space:\]\]+-n\[\[:space:\]\]\*\[\[:digit:\]\]+)\|sudo\|(LANG\|LC\_\[\[:alnum:\]\]\]\*)(=\|=\[^\[:space:\]\]+)"

    Regular expression (POSIX Extended flavor) which marks the begin of a
    command line in command input fields. Such prefixes are ignored while
    the auto-completion action is performed, typically for commands acting
    as pass-through wrapper, executing the specified command.

## WINDOW MENUS

- **WinMenuItems**="rmsnxfhualytiecw"

    Items supported in menu window (rmsnxfhualytieckw)

- **RolloverButtonsSupported**=0

    Does it support the 'O' title bar button images (for mouse rollover).

- **ShowMenuButtonIcon**=1 # 0/1

    Show application icon over menu button

## THEME SETTINGS

The following sections show settings that can be set in theme files.
They can also be set in the `preferences` file, but themes will override
the values set there.  To override the theme values, the settings should
be set in `prefoverrides` file: see [icewm-prefoverrides(5)](icewm-prefoverrides).  Default
values are shown following the equal sign.

### THEME DESCRIPTION

- **ThemeAuthor**=""

    Theme author, e-mail address, credits.

- **ThemeDescription**=""

    Description of the theme, credits.

- **Look**="nice"

    Choose a theme look from one of:
    "win95", "motif", "warp3", "warp4",
    "nice", "metal2", "gtk2", and some others.

- **Gradients**=""

    List of gradient pixmaps in the current theme.

### THEME BORDERS, ICONS, MARGINS AND BUTTONS

- **BorderSizeX**=6  \[0-128\]

    Horizontal window border.

- **BorderSizeY**=6  \[0-128\]

    Vertical window border.

- **DlgBorderSizeX**=2  \[0-128\]

    Horizontal dialog window border.

- **DlgBorderSizeY**=2  \[0-128\]

    Vertical dialog window border.

- **CornerSizeX**=24  \[0-64\]

    Resize corner width.

- **CornerSizeY**=24  \[0-64\]

    Resize corner height.

- **TitleBarHeight**=20  \[0-128\]

    Title bar height.

- **TitleBarJustify**=0  \[0-100\]

    Justification of the window title.

- **TitleBarHorzOffset**=0  \[-128-128\]

    Horizontal offset for the window title text.

- **TitleBarVertOffset**=0  \[-128-128\]

    Vertical offset for the window title text.

- **MenuButtonIconVertOffset**=0  \[-128-128\]

    Vertical offset for the menu button icon.

- **ScrollBarX**=16  \[0-64\]

    Scrollbar width.

- **ScrollBarY**=16  \[0-64\]

    Scrollbar (button) height.

- **MenuIconSize**=16  \[8-128\]

    Menu icon size.

- **SmallIconSize**=16  \[8-128\]

    Dimension of the small icons.

- **LargeIconSize**=32  \[8-128\]

    Dimension of the large icons.

- **HugeIconSize**=48  \[8-128\]

    Dimension of the large icons.

- **QuickSwitchHorzMargin**=3  \[0-64\]

    Horizontal margin of the quickswitch window.

- **QuickSwitchVertMargin**=3  \[0-64\]

    Vertical margin of the quickswitch window.

- **QuickSwitchIconMargin**=4  \[0-64\]

    Vertical margin in the quickswitch window.

- **QuickSwitchIconBorder**=2  \[0-64\]

    Distance between the active icon and it's border.

- **QuickSwitchSeparatorSize**=6  \[0-64\]

    Height of the separator between (all reachable) icons and text, 0 to avoid it.

- **TitleButtonsLeft**="s"

    Titlebar buttons from left to right (x=close, m=max, i=min, h=hide, r=rollup, s=sysmenu, d=depth).

- **TitleButtonsRight**="xmir"

    Titlebar buttons from right to left (x=close, m=max, i=min, h=hide, r=rollup, s=sysmenu, d=depth).

- **TitleButtonsSupported**="xmis"

    Titlebar buttons supported by theme (x,m,i,r,h,s,d).

- **TitleBarCentered**=0 # 0/1

    Draw window title centered (obsoleted by TitleBarJustify).

- **TitleBarJoinLeft**=0 # 0/1

    Join title\*S and title\*T.

- **TitleBarJoinRight**=0 # 0/1

    Join title\*T and title\*B.

- **TaskBarClockLeds**=0 # 0/1

    Task bar clock/battery monitor uses nice pixmap LCD display (but then it
    doesn't display correctly in many languages anymore, e.g., for
    Japanese and Korean it works only when a real font is used and not
    the LCD pixmaps.)

- **TaskBarGraphHeight**=20  \[16-1000\]

    Height of taskbar monitoring applets.

- **TaskbuttonIconOffset**=0 # \[0-16\]

    Width of taskbutton side icons.

- **TrayIconMaxWidth**=32 # \[16-128\]

    Maximum scaled width of tray icons.

- **TrayIconMaxHeight**=24 # \[16-128\]

    Maximum scaled height of tray icons.

- **TrayDrawBevel**=0 # 0/1

    Surround the tray with plastic border.

### THEME FONTS

- **TitleFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **TitleFontNameXft**="sans-serif:size=12"

    Name of the title bar font.

- **MenuFontName**="-\*-sans-bold-r-\*-\*-\*-100-\*-\*-\*-\*-\*-\*"
- **MenuFontNameXft**="sans-serif:size=10:bold"

    Name of the menu font.

- **StatusFontName**="-\*-monospace-bold-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **StatusFontNameXft**="monospace:size=12:bold"

    Name of the status display font.

- **QuickSwitchFontName**="-\*-monospace-bold-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **QuickSwitchFontNameXft**="monospace:size=12:bold"

    Name of the font for Alt+Tab switcher window.

- **NormalButtonFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **NormalButtonFontNameXft**="sans-serif:size=12"

    Name of the normal button font.

- **ActiveButtonFontName**="-\*-sans-bold-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ActiveButtonFontNameXft**="sans-serif:size=12:bold"

    Name of the active button font.

- **NormalTaskBarFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **NormalTaskBarFontNameXft**="sans-serif:size=12"

    Name of the normal task bar item font.

- **ActiveTaskBarFontName**="-\*-sans-bold-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ActiveTaskBarFontNameXft**="sans-serif:size=12:bold"

    Name of the active task bar item font.

- **ToolButtonFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ToolButtonFontNameXft**="sans-serif:size=12"

    Name of the tool button font (fallback: NormalButtonFontName).

- **NormalWorkspaceFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **NormalWorkspaceFontNameXft**="sans-serif:size=12"

    Name of the normal workspace button font (fallback: NormalButtonFontName).

- **ActiveWorkspaceFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ActiveWorkspaceFontNameXft**="sans-serif:size=12"

    Name of the active workspace button font (fallback: ActiveButtonFontName).

- **MinimizedWindowFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **MinimizedWindowFontNameXft**="sans-serif:size=12"

    Name of the mini-window font.

- **ListBoxFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ListBoxFontNameXft**="sans-serif:size=12"

    Name of the window list font.

- **ToolTipFontName**="-\*-sans-medium-r-\*-\*-\*-120-\*-\*-\*-\*-\*-\*"
- **ToolTipFontNameXft**="sans-serif:size=12"

    Name of the tool tip font.

- **ClockFontName**="-\*-monospace-medium-r-\*-\*-\*-140-\*-\*-\*-\*-\*-\*"
- **ClockFontNameXft**="monospace:size=12"

    Name of the task bar clock font.

- **TempFontName**="-\*-monospace-medium-r-\*-\*-\*-140-\*-\*-\*-\*-\*-\*"
- **TempFontNameXft**="monospace:size=12"

    Name of the task bar temperature font.

- **ApmFontName**="-\*-monospace-medium-r-\*-\*-\*-140-\*-\*-\*-\*-\*-\*"
- **ApmFontNameXft**="monospace:size=12"

    Name of the task bar battery font.

- **InputFontName**="-\*-monospace-medium-r-\*-\*-\*-140-\*-\*-\*-\*-\*-\*"
- **InputFontNameXft**="monospace:size=12"

    Name of the input field font.

- **LabelFontName**="-\*-sans-medium-r-\*-\*-\*-140-\*-\*-\*-\*-\*-\*"
- **LabelFontNameXft**="sans-serif:size=12"

    Name of the label font.

### THEME COLORS

- **ColorDialog** = "rgb:C0/C0/C0"

    Background of dialog windows.

- **ColorNormalBorder** = "rgb:C0/C0/C0"

    Border of inactive windows.

- **ColorActiveBorder** = "rgb:C0/C0/C0"

    Border of active windows.

- **ColorNormalButton** = "rgb:C0/C0/C0"

    Background of regular buttons.

- **ColorNormalButtonText** = "rgb:00/00/00"

    Text color of regular buttons.

- **ColorActiveButton** = "rgb:E0/E0/E0"

    Background of pressed buttons.

- **ColorActiveButtonText** = "rgb:00/00/00"

    Text color of pressed buttons.

- **ColorNormalTitleButton** = "rgb:C0/C0/C0"

    Background of titlebar buttons.

- **ColorNormalTitleButtonText** = "rgb:00/00/00"

    Text color of titlebar buttons.

- **ColorToolButton** = ""

    Background of toolbar buttons, ColorNormalButton is used if empty.

- **ColorToolButtonText** = ""

    Text color of toolbar buttons, ColorNormalButtonText is used if empty.

- **ColorNormalWorkspaceButton** = ""

    Background of workspace buttons, ColorNormalButton is used if empty.

- **ColorNormalWorkspaceButtonText** = ""

    Text color of workspace buttons, ColorNormalButtonText is used if empty.

- **ColorActiveWorkspaceButton** = ""

    Background of the active workspace button, ColorActiveButton is used if empty.

- **ColorActiveWorkspaceButtonText** = ""

    Text color of the active workspace button, ColorActiveButtonText is used if empty.

- **ColorNormalTitleBar** = "rgb:80/80/80"

    Background of the titlebar of regular windows.

- **ColorNormalTitleBarText** = "rgb:00/00/00"

    Text color of the titlebar of regular windows.

- **ColorNormalTitleBarShadow** = ""

    Text shadow of the titlebar of regular windows.

- **ColorActiveTitleBar** = "rgb:00/00/A0"

    Background of the titlebar of active windows.

- **ColorActiveTitleBarText** = "rgb:FF/FF/FF"

    Text color of the titlebar of active windows.

- **ColorActiveTitleBarShadow** = ""

    Text shadow of the titlebar of active windows.

- **ColorNormalMinimizedWindow** = "rgb:C0/C0/C0"

    Background for mini icons of regular windows.

- **ColorNormalMinimizedWindowText** = "rgb:00/00/00"

    Text color for mini icons of regular windows.

- **ColorActiveMinimizedWindow** = "rgb:E0/E0/E0"

    Background for mini icons of active windows.

- **ColorActiveMinimizedWindowText** = "rgb:00/00/00"

    Text color for mini icons of active windows.

- **ColorNormalMenu** = "rgb:C0/C0/C0"

    Background of pop-up menus.

- **ColorNormalMenuItemText** = "rgb:00/00/00"

    Text color of regular menu items.

- **ColorActiveMenuItem** = "rgb:A0/A0/A0"

    Background of selected menu item, leave empty to force transparency.

- **ColorActiveMenuItemText** = "rgb:00/00/00"

    Text color of selected menu items.

- **ColorDisabledMenuItemText** = "rgb:80/80/80"

    Text color of disabled menu items.

- **ColorDisabledMenuItemShadow** = ""

    Shadow of regular menu items.

- **ColorMoveSizeStatus** = "rgb:C0/C0/C0"

    Background of move/resize status window.

- **ColorMoveSizeStatusText** = "rgb:00/00/00"

    Text color of move/resize status window.

- **ColorQuickSwitch** = "rgb:C0/C0/C0"

    Background of the quick switch window.

- **ColorQuickSwitchText** = "rgb:00/00/00"

    Text color in the quick switch window.

- **ColorQuickSwitchActive** = ""

    Rectangle around the active icon in the quick switch window.

- **ColorQuickSwitchBorder** = ""

    The color for the quick switch border. When empty, a one pixel wide
    elevation border will be drawn, based on the quick switch background.

- **ColorDefaultTaskBar** = "rgb:C0/C0/C0"

    Background of the taskbar.

- **ColorNormalTaskBarApp** = "rgb:C0/C0/C0"

    Background for task buttons of regular windows.

- **ColorNormalTaskBarAppText** = "rgb:00/00/00"

    Text color for task buttons of regular windows.

- **ColorActiveTaskBarApp** = "rgb:E0/E0/E0"

    Background for task buttons of the active window.

- **ColorActiveTaskBarAppText** = "rgb:00/00/00"

    Text color for task buttons of the active window.

- **ColorMinimizedTaskBarApp** = "rgb:A0/A0/A0"

    Background for task buttons of minimized windows.

- **ColorMinimizedTaskBarAppText** = "rgb:00/00/00"

    Text color for task buttons of minimized windows.

- **ColorInvisibleTaskBarApp** = "rgb:80/80/80"

    Background for task buttons of windows on other workspaces.

- **ColorInvisibleTaskBarAppText** = "rgb:00/00/00"

    Text color for task buttons of windows on other workspaces.

- **ColorScrollBar** = "rgb:A0/A0/A0"

    Scrollbar background (sliding area).

- **ColorScrollBarSlider** = "rgb:C0/C0/C0"

    Background of the slider button in scrollbars.

- **ColorScrollBarButton** = "rgb:C0/C0/C0"

    Background of the arrow buttons in scrollbars.

- **ColorScrollBarArrow** = "rgb:C0/C0/C0"

    Background of the arrow buttons in scrollbars (obsolete).

- **ColorScrollBarButtonArrow** = "rgb:00/00/00"

    Color of active arrows on scrollbar buttons.

- **ColorScrollBarInactiveArrow** = "rgb:80/80/80"

    Color of inactive arrows on scrollbar buttons.

- **ColorListBox** = "rgb:C0/C0/C0"

    Background of listboxes.

- **ColorListBoxText** = "rgb:00/00/00"

    Text color in listboxes.

- **ColorListBoxSelection** = "rgb:80/80/80"

    Background of selected listbox items.

- **ColorListBoxSelectionText** = "rgb:00/00/00"

    Text color of selected listbox items.

- **ColorToolTip** = "rgb:E0/E0/00"

    Background of tooltips.

- **ColorToolTipText** = "rgb:00/00/00"

    Text color of tooltips.

- **ColorLabel** = "rgb:C0/C0/C0"

    Background of labels, leave empty to force transparency.

- **ColorLabelText** = "rgb:00/00/00"

    Text color of labels.

- **ColorInput** = "rgb:FF/FF/FF"

    Background of text entry fields (e.g., the addressbar).

- **ColorInputText** = "rgb:00/00/00"

    Text color of text entry fields (e.g., the addressbar).

- **ColorInputSelection** = "rgb:80/80/80"

    Background of selected text in an entry field.

- **ColorInputSelectionText** = "rgb:00/00/00"

    Selected text in an entry field.

- **ColorClock** = "rgb:00/00/00"

    Background of non-LCD clock, leave empty to force transparency.

- **ColorClockText** = "rgb:00/FF/00"

    Text color of non-LCD clock.

- **ColorKeyboardLayoutText** = ""

    Color of keyboard layout indicator.

- **ColorApm** = "rgb:00/00/00"

    Background of battery monitor, leave empty to force transparency.

- **ColorApmText** = "rgb:00/FF/00"

    Text color of battery monitor.

- **ColorApmBattery** = "rgb:FF/FF/00"

    Color of battery monitor when discharging.

- **ColorApmLine** = "rgb:00/FF/00"

    Color of battery monitor when charging.

- **ColorApmGraphBg** = "rgb:00/00/00"

    Background color for graph mode.

- **ColorCPUStatusUser** = "rgb:00/FF/00"

    User load on the CPU monitor.

- **ColorCPUStatusSystem** = "rgb:FF/00/00"

    System load on the CPU monitor.

- **ColorCPUStatusInterrupts** = "rgb:FF/FF/00"

    Interrupts on the CPU monitor.

- **ColorCPUStatusIoWait** = "rgb:60/00/60"

    IO Wait on the CPU monitor.

- **ColorCPUStatusSoftIrq** = "rgb:00/FF/FF"

    Soft Interrupts on the CPU monitor.

- **ColorCPUStatusNice** = "rgb:00/00/FF"

    Nice load on the CPU monitor.

- **ColorCPUStatusIdle** = "rgb:00/00/00"

    Idle (non) load on the CPU monitor, leave empty to force
    transparency.

- **ColorCPUStatusSteal** = "rgb:FF/8A/91"

    Involuntary Wait on the CPU monitor.

- **ColorCPUStatusTemp** = "rgb:60/60/C0"

    Temperature of the CPU.

- **ColorMEMStatusUser** = "rgb:40/40/80"

    User program usage in the memory monitor.

- **ColorMEMStatusBuffers** = "rgb:60/60/C0"

    OS buffers usage in the memory monitor.

- **ColorMEMStatusCached** = "rgb:80/80/FF"

    OS cached usage in the memory monitor.

- **ColorMEMStatusFree** = "rgb:00/00/00"

    Free memory in the memory monitor.

- **ColorNetSend** = "rgb:FF/FF/00"

    Outgoing load on the network monitor.

- **ColorNetReceive** = "rgb:FF/00/FF"

    Incoming load on the network monitor.

- **ColorNetIdle** = "rgb:00/00/00"

    Idle (non) load on the network monitor, leave empty to force transparency.

### DESKTOP BACKGROUND

The following themeable preferences are read by [icewmbg(1)](icewmbg):

- **DesktopBackgroundCenter**=0  0/1

    Display desktop background centered and not tiled.

- **DesktopBackgroundScaled**=0  0/1

    Resize desktop background to full screen.

- **DesktopBackgroundColor**=""

    A comma-separated list of zero or more desktop background colors.

- **DesktopBackgroundImage**=""

    A comma-separated list of zero or more desktop background images.
    Each image may be a path with a [glob(7)](https://manned.org/glob.7) pattern, or start with a
    tilde or environment variable.

- **ShuffleBackgroundImages**=0  0/1

    Choose a random selection from the list of background images.

- **SupportSemitransparency**=1  0/1

    Support for semitransparent terminals like Eterm or gnome-terminal.

- **DesktopTransparencyColor**=""

    Color(s) to announce for semitransparent windows.

- **DesktopTransparencyImage**=""

    Image(s) to announce for semitransparent windows.
    This is a list similar to **DesktopBackgroundImage**.

- **DesktopBackgroundMultihead**=0  0/1

    Paint the background image over all multihead monitors combined.

- **CycleBackgroundsPeriod**=0

    Seconds between cycling over all background images, default zero is off.

## EXAMPLES

    Alpha=1
    Splash="IceWM.jpg"
    LimitSize=0
    LimitPosition=0
    LimitByDockLayer=1
    QuickSwitchToAllWorkspaces=1
    QuickSwitchHugeIcon=1
    QuickSwitchFillSelection=1
    TaskBarMailboxStatusBeepOnNewMail=1
    TaskBarMailboxStatusCountMessages=1
    TaskBarShowMEMStatus=0
    TaskBarShowCollapseButton=1
    TaskBarWorkspacesLimit="8"
    ShowProgramsMenu=1
    ShowAddressBar=0
    ToolTipDelay=200
    ToolTipTime=5000
    AutoHideDelay=900
    AutoShowDelay=100
    EdgeResistance=3
    KeySysWinMenu=""
    KeySysWinListMenu="Shift+Ctrl+Esc"

The above example shows how to tell **icewm** to not bind a specific key:
_KeySysWinMenu_ in this case.

## FILES

Locations for the `preferences` file are as follows:

    $ICEWM_PRIVCFG/preferences
    $XDG_CONFIG_HOME/icewm/preferences
    $HOME/.icewm/preferences
    /etc/icewm/preferences
    /usr/share/icewm/preferences

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icewm-prefoverride(5)](icewm-prefoverride).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
