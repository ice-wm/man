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

The IceWM `winoptions` file contains settings to control
_application specific_ window appearance and behavior.
For instance, they control the window border, placement and size,
the window layer, its workspace, its visibility on the task bar
and its focus behavior.

The winoptions are established when [icewm(1)](icewm) starts.  However,
they can be overridden later using [icesh(1)](icesh) or [icewmhint(1)](icewmhint).
The command `icesh winoptions` instructs icewm to reload the
`winoptions` file, while `icewmhint` tunes a specific application
instance when it starts.

## FORMAT

Each line in the file must be in one of the following formats:

> - _NAME_**.**_CLASS_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_ROLE_**.**_OPTION_**:** _VALUE_
> - _CLASS_**.**_OPTION_**:** _VALUE_
> - _NAME_**.**_OPTION_**:** _VALUE_
> - _ROLE_**.**_OPTION_**:** _VALUE_
> - **.**_OPTION_**:** _VALUE_

Here _NAME_ and _CLASS_ are from the **WM\_CLASS** property of the
window. This can be found in the output of `icesh -a getClass`.

While _ROLE_ refers to the **WM\_WINDOW\_ROLE** property of the window,
which is the application instance specific name. Only a minority of
windows have it. See the output of `icesh -a list prop WM_WINDOW_ROLE`.

In rare cases, a name, class or role may contain a period. If it does,
the period should be escaped by a single backslash.

Lastly, the _OPTION: VALUE_ pair refer to the options and values
described below. A line with just a dot, followed by an option/value
pair, applies to all windows.

## OPTIONS

There are four categories: _general_, _function_, _decor_ and
_feature_.

## GENERAL OPTIONS

These control general characteristics of windows:

- **icon**: _NAME_ (default: none)

    Specifies the icon name for the window.  _NAME_ is the icon name, like
    `utilities-terminal`. It can also be a file, like `xterm.png`, a full
    path, or a prefix of a path without sizes or suffix.

- **workspace**: _WORKSPACE_ (default: current)

    Specifies the default workspace for the window.  _WORKSPACE_ is the
    workspace number counting from zero (0).

- **layer**: {_LAYER_\|_NUMBER_} (default: Normal)

    Specifies the default layer for the window.  Layer can be one of the
    following names or a number from zero to fifteen:

        Desktop     (0)  Desktop window.
        Below       (2)  Below the default layer.
        Normal      (4)  Default layer for windows.
        OnTop       (6)  Above the default layer.
        Dock        (8)  Docked windows at edge of screen.
        AboveDock  (10)  Windows above the dock.
        Menu       (12)  The layer for menu's.
        Fullscreen (14)  When fullscreen and focused.
        AboveAll   (15)  Always above anything.

- **geometry** _geometry_ (default: WM\_SIZE\_HINTS property)

    The default geometry for the window.  This geometry should be specified
    in a format that can be parsed by [XParseGeometry(3)](https://tronche.com/gui/x/xlib/utilities/XParseGeometry.html):

        [=][<width>{xX}<height>][{+-}<xoffset>{+-}<yoffset>]

    The default geometry is taken from the WM\_SIZE\_HINTS property of the
    window or else from the initial window geometry. This option overrides
    the default.

- **tray**: {**Ignore**\|**Minimized**\|**Exclusive**\|_NUMBER_} (default: 0)

    The default tray option for the window.  This affects both the tray and
    the task pane.  Tray can be one of the following three strings or a number
    from zero (0) to two (2):

        Ignore     (0)  No icon is added to the tray.
        Minimized  (1)  Add to tray, no task when minimized.
        Exclusive  (2)  Add to tray, no task button.

- **order**: _NUMBER_ (default: 0)

    The sorting order for task buttons, tray icons, quick switch and window
    list. The default value is zero. Increasing positive values go right,
    while decreasing negative values go left.

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

- **frame**: _label_ (default: none)

    All windows with the same frame label become tabs in a single frame.

## FUNCTION OPTIONS

Function options enable/disable (1/0) the ability to take an action on
the window.  The normal default for all options is enabled (1) unless
overridden by the application:

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
application or the theme:

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
the application:

    allWorkspaces:            {1|0}  on all workspaces.
    appTakesFocus:            {1|0}  let application take focus.
    doNotCover:               {1|0}  limits workspace if sticky.
    doNotFocus:               {1|0}  do not focus.
    forcedClose:              {1|0}  no close confirmation dialog.
    fullKeys:                 {1|0}  don't install icewm key bindings.
    ignoreNoFocusHint:        {1|0}  focus even when no-input is set.
    ignorePagerPreview:       {1|0}  do not show in pager preview.
    ignorePositionHint:       {1|0}  always let icewm place the window.
    ignoreQuickSwitch:        {1|0}  not on quick switch.
    ignoreTaskBar:            {1|0}  not on task bar.
    ignoreUrgentHint:         {1|0}  ignore urgent hints.
    ignoreWinList:            {1|0}  not on window list.
    ignoreActivationMessages: {1|0}  only user can focus window.
    ignoreOverrideRedirect:   {1|0}  ignore the override redirect flag.
    noFocusOnAppRaise:        {1|0}  no automatic focus on raise.
    noFocusOnMap:             {1|0}  do not focus when mapped.
    noIgnoreTaskBar:          {1|0}  always show on task bar.
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

Following shows how a shaped output-only application is shown
without titlebar and minimal functionality.

    xeyes.tray: Exclusive
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

# POD ERRORS

Hey! **The above document had some coding errors, which are explained below:**

- Around line 69:

    &#x3d;back without =over

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
