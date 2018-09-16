---
title: "icewm-winoptions(5)"
---
# NAME

    icewm-winoptions - IceWM window options configuration file

# SYNOPSIS

- `$ICEWM_PRIVCFG/winoptions`
- `$XDG_CONFIG_HOME/icewm/winoptions`
- `$HOME/.icewm/winoptions`
- `/etc/icewm/winoptions`
- `/usr/share/icewm/winoptions`

# DESCRIPTION

The IceWM window options configuration file is used to configure
settings for individual application windows.  The window options that
are established by this file when [icewm(1)](icewm.md) starts can be overridden
while running using the [icesh(1)](icesh.md) or [icewmhint(1)](icewmhint.md) utilities.

Contains settings to control window appearance and behaviour which are
specific to applications or groups of applications.  Options can control
the border, whether it appears on the task bar, the window list, the
system tray and the work spaces.  Also its layer, geometry, whether it
can be moved, resized and closed.  Full details for this file are
explained in the ["IceWM Manual"](/manual).

# FORMAT

Each line in the file must be in one of the following formats:

> - _CLASS_**.**_NAME_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_NAME_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_OPTION_**:** _VALUE_
> - _ROLE_**.**_OPTION_**:** _VALUE_

Where the fields are defined as follows:

- _CLASS_

    The resource class portion of the ICCCM **WM\_CLASS** property for the
    window.

- _NAME_

    The resource name portion of the ICCCM **WM\_CLASS** property for the
    window.

- _ROLE_

    The resource name portion of the ICCCM **WM\_WINDOW\_ROLE** property for
    the window.

- _OPTION_: _VALUE_

    One of the options and values described below under ["OPTIONS"](#options).

Note that it is possible that the **WM\_WINDOW\_ROLE** may contain a period
(`.`).  When it does, the period should be escaped by a single
backslash when specifying the _ROLE_ in the file.

# OPTIONS

The options and values described in the format, above, consist of an
option name, _OPTION_ followed by a semicolon (`:`) a space (` `) and
an allowable value for the option, _VALUE_.  The available options are
as follows:

## GENERAL OPTIONS

The following option control general characteristics of windows:

- **icon**: _NAME_ (default: none)

    Specifies the icon name for the window.  _NAME_ is the name of the
    icon.

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
    in a format that can be parsed by [XParseGeometry(3)](https://manned.org/XParseGeometry.3):

        [=][<width>{xX}<height>][{+-}<xoffset>{+-}<yoffset>]

- **tray**: {**Ignore**\|**Minimized**\|**Exclusive**\|_NUMBER_} (default: 0)

    The default tray option for the window.  This affects both the tray and
    the task pane.  Tray can be one of the following strings or a number
    from zero (0) to two (2):

        Ignore     (0)  No icon added to tray.
        Minimized  (1)  Add to tray, no task when minimized.
        Exclusive  (2)  Add to tray, no task button.

## FUNCTION OPTIONS

Function options enable/disable (1/0) the ability to take an action on
the window.  The normal default for all options is enabled (1) unless
overridden by the application.  The following options are defined:

    fMove:     {0\|1}  can be moved.         (default: 1)
    fResize:   {0\|1}  can be resized.       (default: 1)
    fClose:    {0\|1}  can be closed.        (default: 1)
    fMinimize: {0\|1}  can be minimized.     (default: 1)
    fMaximize: {0\|1}  can be maximized.     (default: 1)
    fHide:     {0\|1}  can be hidden.        (default: 1)
    fRollup:   {0\|1}  can be shaded.        (default: 1)

## DECOR OPTIONS

Decor options enable/disable (1/0) decorations on the window.  The
normal default for all options is enabled (1) unless overridden by the
application.  The following options are defined:

    dTitleBar: {0\|1}  has title bar.        (default: 1)
    dSysMenu:  {0\|1}  has window menu.      (default: 1)
    dBorder:   {0\|1}  has border.           (default: 1)
    dResize:   {0\|1}  has resize grips.     (default: 1)
    dClose:    {0\|1}  has close button.     (default: 1)
    dMinimize: {0\|1}  has minimize button.  (default: 1)
    dMaximize: {0\|1}  has maximize button.  (default: 1)
    dHide:     {0\|1}  has hide button.      (default: 1)
    dRollup:   {0\|1}  has shade button.     (default: 1)
    dDepth:    {0\|1}  has depth button.     (default: 1)

## FEATURE OPTIONS

Feature options enable/disable (1/0) additional features of the window.
The normal default for all options is disabled (0) unless overridden by
the application.  The following options are defined:

    allWorkspaces:            {1\|0}  on all workspaces.
    ignoreTaskBar:            {1\|0}  not on task bar.
    noIgnoreTaskBar:          {1\|0}  on task bar.
    ignoreWinList:            {1\|0}  not on window list.
    ignoreQuickSwitch:        {1\|0}  not on quick switch.
    fullKeys:                 {1\|0}  provided more keys.
    noFocusOnAppRaise:        {1\|0}  no focus on raise.
    ignoreNoFocusHint:        {1\|0}  focus even no-input.
    ignorePositionHint:       {1\|0}  place automatically.
    doNotCover:               {1\|0}  limits workspace if sticky.
    doNotFocus:               {1\|0}  do not focus.
    startFullscreen:          {1\|0}  start full screen.
    startMinimized:           {1\|0}  start minimized.
    startMaximized:           {1\|0}  start maximized.
    startMaximizedVert:       {1\|0}  start maximized vertical.
    startMaximizedHorz:       {1\|0}  start maximized horizontal.
    nonICCCMconfigureRequest: {1\|0}  more configure requests.
    forcedClose:              {1\|0}  no close dialog.
    noFocusOnMap:             {1\|0}  do not focus when mapped.
    ignoreUrgentHint:         {1\|0}  ignore urgent hints.
    appTakesFocus:            {1\|0}  let application take focus.

# EXAMPLES

Following is the example window options file that ships with [icewm(1)](icewm.md)
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
    # workaround for XV window repositioning problems
    xv.nonICCCMconfigureRequest: 1
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

# FILES

Locations for the window options file are as follows:

- `$ICEWM_PRIVCFG/winoptions`
- `$XDG_CONFIG_HOME/icewm/winoptions`
- `$HOME/.icewm/winoptions`
- `/etc/icewm/winoptions`
- `/usr/share/icewm/winoptions`

# SEE ALSO

[icewm(1)](icewm.md),
[icesh(1)](icesh.md),
[icewmhint(1)](icewmhint.md),
[XParseGeometry(3)](https://manned.org/XParseGeometry.3).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
