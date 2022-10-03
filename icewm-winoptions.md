---
title: "icewm-winoptions(5)"
---
## NAME

    icewm-winoptions - IceWM window options configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/winoptions
    $XDG_CONFIG_HOME/icewm/winoptions
    $HOME/.icewm/winoptions
    /etc/icewm/winoptions
    /usr/share/icewm/winoptions

## DESCRIPTION

Contains settings to control window appearance and behaviour. These are
specific to applications, or to groups of applications.  Options can
control the window border, whether the application appears on the task
bar, the window list, the system tray and the work spaces.
Also its layer, geometry, whether it can be moved, resized and closed.

Options are established when [icewm(1)](icewm) starts.  However, they can be
overridden later using [icesh(1)](icesh) or [icewmhint(1)](icewmhint). The command
`icesh winoptions` instructs icewm to reload the winoptions file.

## FORMAT

Each line in the file must be in one of the following formats:

> - _NAME_**.**_CLASS_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_OPTION_**:** _VALUE_
> - _ROLE_**.**_OPTION_**:** _VALUE_
> - **.**_OPTION_**:** _VALUE_

Where the fields are defined as follows:

- _CLASS_

    The resource class portion of the ICCCM **WM\_CLASS** property for the
    window.

- _NAME_

    The resource instance portion of the ICCCM **WM\_CLASS** property for the
    window.

- _ROLE_

    The ICCCM **WM\_WINDOW\_ROLE** property for the window.

- _OPTION_: _VALUE_

    One of the options and values described below under ["OPTIONS"](#options).

Note that it is possible that the **WM\_WINDOW\_ROLE** may contain a period
(`.`).  When it does, the period should be escaped by a single
backslash when specifying the _ROLE_ in the file.

## OPTIONS

The options and values described in the format, above, consist of an
option name, _OPTION_ followed by a semicolon (`:`) a space (` `) and
an allowable value for the option, _VALUE_.  The available options are
as follows:

## GENERAL OPTIONS

The following option control general characteristics of windows:

- **icon**: _NAME_ (default: none)

    Specifies the icon name for the window.  _NAME_ is the name of the
    icon, like `utilities-terminal`. It can also be a file, like
    `xterm.png`, a full path, or a prefix of a path without sizes or suffix.

- **workspace**: _WORKSPACE_ (default: current)

    Specifies the default workspace for the window.  _WORKSPACE_ is the
    workspace number counting from zero (0).

- **layer**: {**Desktop**\|**Below**\|**Normal**\|**OnTop**\|**Dock**\|**AboveDock**\|**Menu**\|_NUMBER_} (default: 4)

    Specifies the default layer for the window.  Layer can be one of the
    following strings or a number from zero (0) to fifteen (15):

        Desktop     (0)  Desktop window.
        Below       (2)  Below the default layer.
        Normal      (4)  Default layer for windows.
        OnTop       (6)  Above the default layer.
        Dock        (8)  Docked windows at edge of screen.
        AboveDock  (10)  Windows above the dock.
        Menu       (12)  Windows above the dock.

- **geometry** _geometry_ (default: WM\_SIZE\_HINTS)

    The default geometry for the window.  This geometry should be specified
    in a format that can be parsed by [XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html):

        [=][<width>{xX}<height>][{+-}<xoffset>{+-}<yoffset>]

- **tray**: {**Ignore**\|**Minimized**\|**Exclusive**\|_NUMBER_} (default: 0)

    The default tray option for the window.  This affects both the tray and
    the task pane.  Tray can be one of the following strings or a number
    from zero (0) to two (2):

        Ignore     (0)  No icon added to tray.
        Minimized  (1)  Add to tray, no task when minimized.
        Exclusive  (2)  Add to tray, no task button.

- **order**: _NUMBER_ (default: 0)

    The sorting order of task buttons and tray icons. The default value is
    zero. Increasing positive values go farther right, while decreasing
    negative values go farther left. The order option applies to the task
    pane, the tray pane and the system tray.

- **opacity**: _NUMBER_ (default: 0)

    Set the \_NET\_WM\_WINDOW\_OPACITY property if _NUMBER_ is a value between
    1 and 100. _NUMBER_ is interpreted as percentage of maximum opaqueness.

- **keyboard**: _layout_ (default: none)

    Specifies the keyboard layout to use for this window. 
    The _layout_ is the name of a keyboard layout.
    It can be a space-separated list of arguments to the
    **setxkbmap** program. Please note that **setxkbmap**
    must be installed for this to work. Also define
    a default keyboard layout in `preferences`.

## FUNCTION OPTIONS

Function options enable/disable (1/0) the ability to take an action on
the window.  The normal default for all options is enabled (1) unless
overridden by the application.  The following options are defined:

    fClose:    {0|1}  can be closed.        (default: 1)
    fHide:     {0|1}  can be hidden.        (default: 1)
    fMaximize: {0|1}  can be maximized.     (default: 1)
    fMinimize: {0|1}  can be minimized.     (default: 1)
    fMove:     {0|1}  can be moved.         (default: 1)
    fResize:   {0|1}  can be resized.       (default: 1)
    fRollup:   {0|1}  can be shaded.        (default: 1)

## DECOR OPTIONS

Decor options enable/disable (1/0) decorations on the window.  The
normal default for all options is enabled (1) unless overridden by the
application.  The following options are defined:

    dBorder:   {0|1}  has border.           (default: 1)
    dClose:    {0|1}  has close button.     (default: 1)
    dDepth:    {0|1}  has depth button.     (default: 1)
    dHide:     {0|1}  has hide button.      (default: 1)
    dMaximize: {0|1}  has maximize button.  (default: 1)
    dMinimize: {0|1}  has minimize button.  (default: 1)
    dResize:   {0|1}  has resize grips.     (default: 1)
    dRollup:   {0|1}  has shade button.     (default: 1)
    dSysMenu:  {0|1}  has window menu.      (default: 1)
    dTitleBar: {0|1}  has title bar.        (default: 1)

## FEATURE OPTIONS

Feature options enable/disable (1/0) additional features of the window.
The normal default for all options is disabled (0) unless overridden by
the application.  The following options are defined:

    allWorkspaces:            {1|0}  on all workspaces.
    appTakesFocus:            {1|0}  let application take focus.
    doNotCover:               {1|0}  limits workspace if sticky.
    doNotFocus:               {1|0}  do not focus.
    forcedClose:              {1|0}  no close dialog.
    fullKeys:                 {1|0}  provided more keys.
    ignoreNoFocusHint:        {1|0}  focus even no-input.
    ignorePagerPreview:       {1|0}  do not show in pager preview.
    ignorePositionHint:       {1|0}  place automatically.
    ignoreQuickSwitch:        {1|0}  not on quick switch.
    ignoreTaskBar:            {1|0}  not on task bar.
    ignoreUrgentHint:         {1|0}  ignore urgent hints.
    ignoreWinList:            {1|0}  not on window list.
    ignoreActivationMessages: {1|0}  only user can focus window.
    ignoreOverrideRedirect:   {1|0}  ignore override redirect.
    noFocusOnAppRaise:        {1|0}  no focus on raise.
    noFocusOnMap:             {1|0}  do not focus when mapped.
    noIgnoreTaskBar:          {1|0}  on task bar.
    startClose:               {1|0}  close the window immediately.
    startFullscreen:          {1|0}  start full screen.
    startMaximized:           {1|0}  start maximized.
    startMaximizedHorz:       {1|0}  start maximized horizontal.
    startMaximizedVert:       {1|0}  start maximized vertical.
    startMinimized:           {1|0}  start minimized.

## EXAMPLES

This example uses the WM\_WINDOW\_ROLE property value `pop-up` to deny
input focus to _Chrome_ pop-ups and asks to close them immediately.

    google-chrome.pop-up.doNotFocus: 1
    google-chrome.pop-up.forcedClose: 1
    google-chrome.pop-up.ignorePagerPreview: 1
    google-chrome.pop-up.ignoreUrgentHint: 1
    google-chrome.pop-up.layer: Below
    google-chrome.pop-up.noFocusOnAppRaise: 1
    google-chrome.pop-up.noFocusOnMap: 1
    google-chrome.pop-up.startClose: 1
    google-chrome.pop-up.startMinimized: 1

IceWM places dockapps in a container automatically, but for those
which fail to comply with the protocol it can also be emulated.
An emulated dockapp should appear on all workspaces, have
no decorations, and always be visible in a fixed location.

    wmtime.wmtime.allWorkspaces: 1
    wmtime.wmtime.ignoreTaskBar: 1
    wmtime.wmtime.ignoreQuickSwitch: 1
    wmtime.wmtime.ignoreWinList: 1
    wmtime.wmtime.layer: Below
    wmtime.wmtime.dTitleBar: 0
    wmtime.wmtime.dBorder: 1
    wmtime.wmtime.geometry: 64x64-74-100

Following is the example window options file that ships with [icewm(1)](icewm)
and typically installs to `/usr/share/icewm/winoptions`.

    # This is an example for IceWM's window options file.
    #
    # Place your variants in @CFGDIR@ or in $HOME/.icewm
    # since modifications to this file will be discarded when you
    # (re)install icewm.

    xterm.icon: xterm
    rxvt.icon: xterm
    nxterm.icon: xterm
    fte.icon: fte
    emacs.Emacs.icon: emacs
    AWTapp.icon: java
    xeyes.ignoreWinList: 0
    xeyes.ignoreTaskBar: 1
    xeyes.allWorkspaces: 1
    xeyes.dTitleBar: 0
    xeyes.dBorder: 0
    xeyes.dSysMenu: 0
    xeyes.dResize: 0
    xeyes.dClose: 0
    xeyes.dMinimize: 0
    xeyes.dMaximize: 0
    xeyes.ignoreNoFocusHint: 1

    XClock.ignoreNoFocusHint: 1
    Vim.icon: vim

    applix.ignoreNoFocusHint: 1
    XDdts.noFocusOnAppRaise: 1
    Wingz.noFocusOnAppRaise: 1
    WingzPro.noFocusOnAppRaise: 1

    gkrellm.Gkrellm.allWorkspaces: 1
    gkrellm.Gkrellm.ignoreTaskBar: 1
    gkrellm.Gkrellm.layer: Below
    #gkrellm.Gkrellm.doNotCover: 1

    MainWindow.licq.allWorkspaces: 1
    MainWindow.licq.ignoreQuickSwitch: 1
    MainWindow.licq.ignoreWinList: 1
    MainWindow.licq.layer: Below
    #MainWindow.licq.doNotCover: 1

## FILES

Locations for the `winoptions` file are as follows:

    $ICEWM_PRIVCFG/winoptions
    $XDG_CONFIG_HOME/icewm/winoptions
    $HOME/.icewm/winoptions
    /etc/icewm/winoptions
    /usr/share/icewm/winoptions

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icesh(1)](icesh),
[icewmhint(1)](icewmhint),
[setxkbmap(1)](https://manned.org/setxkbmap.1),
[XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
