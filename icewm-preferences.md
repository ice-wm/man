# NAME

    icewm-preferences - icewm preferences configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/preferences`
- `$XDG_CONFIG_HOME/icewm/preferences`
- `$HOME/.icewm/preferences`
- `/etc/icewm/preferences`
- `/usr/share/icewm/preferences`

# DESCRIPTION

Contains general settings like paths, colors and fonts, but also options
to control the **icewm** focus behaviour and the applets which are
started in the task bar.  The **icewm** installation will provide a
default `preferences` file, which can be copied to the **icewm** user
configuration directory and modified.

# FORMAT

## FOCUS AND BEHAVIOR

The following preferences affect focus and general behavior of
[icewm(1)](icewm.md):

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

- **CenterMaximizedWindows**=0

    Center maximized windows which can't fit the screen (like terminals).

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

    Always maintain focus under mouse window (makes some keyboard support
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

    Auto raise windows after delay.

- **DelayPointerFocus**=1

    Delay pointer focusing when mouse moves.

- **Win95Keys**=1

    Support win95 keyboard keys (Penguin/Meta/Win\_L,R shows menu).

- **ModSuperIsCtrlAlt**=1

    Treat Super/Win modifier as Ctrl+Alt.

- **UseMouseWheel**=0

    Support mouse wheel.

- **ShowPopupsAbovePointer**=0

    Show popup menus above mouse pointer.

- **ReplayMenuCancelClick**=0

    Send the clicks outside menus to target window.

- **ClientWindowMouseActions**=1

    Allow mouse actions on client windows (buggy with some programs).

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

### Quick Switch List

- **QuickSwitch**=1

    Alt+Tab window switching.

- **QuickSwitchToMinimized**=1

    Alt+Tab to minimized windows.

- **QuickSwitchToHidden**=1

    Alt+Tab to hidden windows.

- **QuickSwitchToUrgent**=1

    Priorize Alt+Tab to urgent windows.

- **QuickSwitchToAllWorkspaces**=0

    Alt+Tab to windows on other workspaces.

- **QuickSwitchGroupWorkspaces**=1

    Alt+Tab: group windows on current workspace.

- **QuickSwitchAllIcons**=1

    Show all reachable icons when quick switching.

- **QuickSwitchTextFirst**=0

    Show the window title above (all reachable) icons.

- **QuickSwitchSmallWindow**=0

    Attempt to create a small QuickSwitch window (1/3 instead of 3/5 of

- **QuickSwitchMaxWidth**=0

    Go through all window titles and choose width of the longest one.

- **QuickSwitchVertical**=1

    Place the icons and titles vertical instead of horizontal.

- **QuickSwitchHugeIcon**=0

    Show the huge (48x48) of the window icon for the active window.

- **QuickSwitchFillSelection**=0

    Fill the rectangle highlighting the current icon.

### Edge Workspace Switching

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

The following preferences affect the [icewm(1)](icewm.md) task bar:

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

    Show APM/ACPI/Battery/Power status monitor on task bar.

- **TaskBarShowAPMAuto**=1

    Enable TaskBarShowAPMStatus if a battery is present.

- **TaskBarShowAPMTime**=1

    Show APM status on task bar in time-format.

- **TaskBarShowAPMGraph**=1

    Show APM status in graph mode.

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

    Show 'show desktop' button on taskbar.

- **ShowEllipsis**=1

    Show Ellipsis in taskbar items.

- **TaskBarShowTray**=1

    Show windows in the tray.

- **TrayShowAllWindows**=1

    Show windows from all workspaces on tray.

- **TaskBarShowTransientWindows**=1

    Show transient (dialogs, ...) windows on task bar.

- **TaskBarShowAllWindows**=0

    Show windows from all workspaces on task bar.

- **TaskBarShowWindowIcons**=1

    Show icons of windows on the task bar.

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

- **PagerShowPreview**=1

    Show a mini desktop preview on each workspace button.

- **PagerShowWindowIcons**=1

    Draw window icons inside large enough preview windows on pager (if PagerShowPreview=1).

- **PagerShowMinimized**=1

    Draw even minimized windows as unfilled rectangles (if PagerShowPreview=1).

- **PagerShowBorders**=1

    Draw border around workspace buttons (if PagerShowPreview=1).

- **PagerShowNumbers**=1

    Show number of workspace on workspace button (if PagerShowPreview=1).

- **TaskBarLaunchOnSingleClick**=1

    Execute taskbar applet commands (like MailCommand,     ClockCommand,   ...) on single click.

- **EnableAddressBar**=1

    Enable address bar functionality in taskbar.

- **ShowAddressBar**=1

    Show address bar in task bar.

- **MailBoxPath**=""

    Mailbox path (use \\$MAIL instead).

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

    Network device for which to show status.

- **TimeFormat**="%X"

    Clock Time format (strftime format string).

- **TimeFormatAlt**=""

    Alternate Clock Time format (e.g. for blinking effects).

- **DateFormat**="%c"

    Clock Date format for tooltip (strftime format string).

- **TaskBarCPUSamples**=20  \[2-1000\]

    Width of CPU Monitor.

- **TaskBarMEMSamples**=20  \[2-1000\]

    Width of Memory Monitor.

- **TaskBarNetSamples**=20  \[2-1000\]

    Width of Net Monitor.

- **TaskbarButtonWidthDivisor**=3  \[1-25\]

    Default number of tasks in taskbar.

- **TaskBarWidthPercentage**=100  \[0-100\]

    Task bar width as percentage of the screen width.

- **TaskBarJustify**="left"

    Taskbar justify left, right or center.

- **TaskBarApmGraphWidth**=10  \[1-1000\]

    Width of APM Monitor.

- **TaskBarGraphHeight**=20  \[16-1000\]

    Height of taskbar monitoring applets.

- **XineramaPrimaryScreen**=0  \[0-63\]

    Primary screen for xinerama (taskbar, ...).

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

- **ToolTipDelay**=1000  \[0-5000\]

    Delay before tooltip window is displayed.

- **ToolTipTime**=0  \[0-60000\]

    Time before tooltip window is hidden (0 means never.

- **AutoHideDelay**=300  \[0-5000\]

    Delay before task bar is hidden.

- **AutoShowDelay**=500  \[0-5000\]

    Delay before task bar is shown.

- **AutoRaiseDelay**=400  \[0-5000\]

    Delay before windows are auto raised.

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

## BUITTONS AND KEYS

- **UseRootButtons**=255  \[0-255\]

    Bitmask of root window button click to use in window manager.

- **ButtonRaiseMask**=1  \[0-255\]

    Bitmask of buttons that raise the window when pressed.

- **DesktopWinMenuButton**=0  \[0-20\]

    Desktop mouse-button click to show the window list menu.

- **DesktopMenuButton**=3  \[0-20\]

    Desktop mouse-button click to show the root menu.

- **TitleBarMaximizeButton**=1  \[0-5\]

    TitleBar mouse-button double click to maximize the window.

- **TitleBarRollupButton**=2  \[0-5\]

    TitleBar mouse-button double click to rollup the window.

## WORKSPACES

## PATHS

- **IconPath**="/usr/share/icons/hicolor:/usr/share/icons:/usr/share/pixmaps"

    Icon search path (colon separated).

- **MailBoxPath**=""

    Mailbox path (use \\$MAIL instead).

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

    Open command.

- **TerminalCommand**="xterm"

    Terminal emulator must accept -e option.

- **LogoutCommand**=""

    Command to start logout.

- **LogoutCancelCommand**=""

    Command to cancel logout.

- **ShutdownCommand**="/bin/sh -c "{ test -e /run/systemd/system && systemctl poweroff; } \|\|:""

    Command to shutdown the system.

- **RebootCommand**="/bin/sh -c "{ test -e /run/systemd/system && systemctl reboot; } \|\|:""

    Command to reboot the system.

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

## WINDOW MENUS

## THEME SETTINGS

This section shows settings that can be set in theme files.  They can
also be set in the `preferences` file, but themes will override the
values set there.  To override the theme values, the settings should be
set in `prefoverrides` file: see [icewm-prefoverrides(5)](icewm-prefoverrides.md).  Default
values are shown following the equal sign.

### Description

- **ThemeAuthor**=""

    Theme author, e-mail address, credits.

- **ThemeDescription**=""

    Description of the theme, credits.

### Borders, Icons, Margins and Buttons

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

### Fonts

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

### Colors

- **ColorDialog** = "rgb:C0/C0/C0"

    Background of dialog windows.

- **ColorNormalBorder** = "rgb:C0/C0/C0"

    Border of inactive windows.

- **ColorActiveBorder** = "rgb:C0/C0/C0"

    Border of active windows.

- **ColorNormalButton** = "rgb:C0/C0/C0"

    Background of regular buttons.

- **ColorNormalButtonText** = "rgb:00/00/00"

    Textcolor of regular buttons.

- **ColorActiveButton** = "rgb:E0/E0/E0"

    Background of pressed buttons.

- **ColorActiveButtonText** = "rgb:00/00/00"

    Textcolor of pressed buttons.

- **ColorNormalTitleButton** = "rgb:C0/C0/C0"

    Background of titlebar buttons.

- **ColorNormalTitleButtonText** = "rgb:00/00/00"

    Textcolor of titlebar buttons.

- **ColorToolButton** = ""

    Background of toolbar buttons, ColorNormalButton is used if empty.

- **ColorToolButtonText** = ""

    Textcolor of toolbar buttons, ColorNormalButtonText is used if empty.

- **ColorNormalWorkspaceButton** = ""

    Background of workspace buttons, ColorNormalButton is used if empty.

- **ColorNormalWorkspaceButtonText** = ""

    Textcolor of workspace buttons, ColorNormalButtonText is used if empty.

- **ColorActiveWorkspaceButton** = ""

    Background of the active workspace button, ColorActiveButton is used if empty.

- **ColorActiveWorkspaceButtonText** = ""

    Textcolor of the active workspace button, ColorActiveButtonText is used if empty.

- **ColorNormalTitleBar** = "rgb:80/80/80"

    Background of the titlebar of regular windows.

- **ColorNormalTitleBarText** = "rgb:00/00/00"

    Textcolor of the titlebar of regular windows.

- **ColorNormalTitleBarShadow** = ""

    Textshadow of the titlebar of regular windows.

- **ColorActiveTitleBar** = "rgb:00/00/A0"

    Background of the titlebar of active windows.

- **ColorActiveTitleBarText** = "rgb:FF/FF/FF"

    Textcolor of the titlebar of active windows.

- **ColorActiveTitleBarShadow** = ""

    Textshadow of the titlebar of active windows.

- **ColorNormalMinimizedWindow** = "rgb:C0/C0/C0"

    Background for mini icons of regular windows.

- **ColorNormalMinimizedWindowText** = "rgb:00/00/00"

    Textcolor for mini icons of regular windows.

- **ColorActiveMinimizedWindow** = "rgb:E0/E0/E0"

    Background for mini icons of active windows.

- **ColorActiveMinimizedWindowText** = "rgb:00/00/00"

    Textcolor for mini icons of active windows.

- **ColorNormalMenu** = "rgb:C0/C0/C0"

    Background of pop-up menus.

- **ColorNormalMenuItemText** = "rgb:00/00/00"

    Textcolor of regular menu items.

- **ColorActiveMenuItem** = "rgb:A0/A0/A0"

    Background of selected menu item, leave empty to force transparency.

- **ColorActiveMenuItemText** = "rgb:00/00/00"

    Textcolor of selected menu items.

- **ColorDisabledMenuItemText** = "rgb:80/80/80"

    Textcolor of disabled menu items.

- **ColorDisabledMenuItemShadow** = ""

    Shadow of regular menu items.

- **ColorMoveSizeStatus** = "rgb:C0/C0/C0"

    Background of move/resize status window.

- **ColorMoveSizeStatusText** = "rgb:00/00/00"

    Textcolor of move/resize status window.

- **ColorQuickSwitch** = "rgb:C0/C0/C0"

    Background of the quick switch window.

- **ColorQuickSwitchText** = "rgb:00/00/00"

    Textcolor in the quick switch window.

- **ColorQuickSwitchActive** = ""

    Rectangle around the active icon in the quick switch window.

- **ColorDefaultTaskBar** = "rgb:C0/C0/C0"

    Background of the taskbar.

- **ColorNormalTaskBarApp** = "rgb:C0/C0/C0"

    Background for task buttons of regular windows.

- **ColorNormalTaskBarAppText** = "rgb:00/00/00"

    Textcolor for task buttons of regular windows.

- **ColorActiveTaskBarApp** = "rgb:E0/E0/E0"

    Background for task buttons of the active window.

- **ColorActiveTaskBarAppText** = "rgb:00/00/00"

    Textcolor for task buttons of the active window.

- **ColorMinimizedTaskBarApp** = "rgb:A0/A0/A0"

    Background for task buttons of minimized windows.

- **ColorMinimizedTaskBarAppText** = "rgb:00/00/00"

    Textcolor for task buttons of minimized windows.

- **ColorInvisibleTaskBarApp** = "rgb:80/80/80"

    Background for task buttons of windows on other workspaces.

- **ColorInvisibleTaskBarAppText** = "rgb:00/00/00"

    Textcolor for task buttons of windows on other workspaces.

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

    Textcolor in listboxes.

- **ColorListBoxSelection** = "rgb:80/80/80"

    Background of selected listbox items.

- **ColorListBoxSelectionText** = "rgb:00/00/00"

    Textcolor of selected listbox items.

- **ColorToolTip** = "rgb:E0/E0/00"

    Background of tooltips.

- **ColorToolTipText** = "rgb:00/00/00"

    Textcolor of tooltips.

- **ColorLabel** = "rgb:C0/C0/C0"

    Background of labels, leave empty to force transparency.

- **ColorLabelText** = "rgb:00/00/00"

    Textcolor of labels.

- **ColorInput** = "rgb:FF/FF/FF"

    Background of text entry fields (e.g. the addressbar).

- **ColorInputText** = "rgb:00/00/00"

    Textcolor of text entry fields (e.g. the addressbar).

- **ColorInputSelection** = "rgb:80/80/80"

    Background of selected text in an entry field.

- **ColorInputSelectionText** = "rgb:00/00/00"

    Selected text in an entry field.

- **ColorClock** = "rgb:00/00/00"

    Background of non-LCD clock, leave empty to force transparency.

- **ColorClockText** = "rgb:00/FF/00"

    Background of non-LCD monitor.

- **ColorApm** = "rgb:00/00/00"

    Background of APM monitor, leave empty to force transparency.

- **ColorApmText** = "rgb:00/FF/00"

    Textcolor of APM monitor.

- **ColorApmBattary** = "rgb:FF/FF/00"

    Color of APM monitor in battary mode.

- **ColorApmLine** = "rgb:00/FF/00"

    Color of APM monitor in line mode.

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

- **DesktopBackgroundColor**=""

    Desktop background color(s).

- **DesktopTransparencyColor**=""

    Color(s) to announce for semitransparent windows.

### Desktop Background

The following preferences are read by [icewmbg(1)](icewmbg.md):

- **DesktopBackgroundCenter**=0  0/1

    Display desktop background centered and not tiled.

- **DesktopBackgroundScaled**=0  0/1

    Resize desktop background to full screen.

- **DesktopBackgroundColor**=""

    Desktop background color(s).

- **DesktopBackgroundImage**=""

    Desktop background image(s).

- **SupportSemitransparency**=1  0/1

    Support for semitransparent terminals like Eterm or gnome-terminal.

- **DesktopTransparencyColor**=""

    Color(s) to announce for semitransparent windows.

- **DesktopTransparencyImage**=""

    Image(s) to announce for semitransparent windows.

- **DesktopBackgroundMultihead**=0  0/1

    Paint the background image over all multihead monitors combined.

### Task Bar

# EXAMPLES

# FILES

Locations for the `preferences` file are as follows:

- `$ICEWM_PRIVCFG/preferences`
- `$XDG_CONFIG_HOME/icewm/preferences`
- `$HOME/.icewm/preferences`
- `/etc/icewm/preferences`
- `/usr/share/icewm/preferences`

# SEE ALSO

[icewm(1)](icewm.md).

# AUTHOR

Brian Bidulock [mailto:bidulock@openss7.org](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.
