---
title: "icewmbg(1)"
---
# NAME

    icewmbg - a background settings manager for the IceWM window manager

# SYNOPSIS

**icewmbg** \[_OPTIONS_\]

# DESCRIPTION

**icewmbg** can assign a colour or image to the _X11_ desktop background.
Many image formats are supported.  Each [icewm(1)](icewm.md) work space can have
its own background.

When the background image has changed then **icewmbg** can be notified to
update the background.  When switching work spaces it checks the image
file modification time.  If the file has changed then it reloads the
background image from file.

**icewmbg** supports semi-transparency.  Semitransparent background
images and colours can be configured.  If these are not specified then
the default background is used.

It uses XINERAMA and RANDR to support backgrounds on all connected
monitors.  When monitors appear/disappear or change their resolution
**icewmbg** will adjust.  It supports an option for one large background
over all monitors.

It will update the `_ICEWMBG_IMAGE` property of the root window to the
path of the background image whenever it changes the desktop background.

It should be started before [icewm(1)](icewm.md), preferably by the
[icewm-session(1)](icewm-session.md) program.

# OPTIONS

## SPECIFIC OPTIONS

Where multiple values can be given for images
or colours they are separated by commas.
Each such value may be enclosed in double quotes.
When _FILE_ is a directory then all images
from that directory are used in sorted order.
If the value starts with an exclamation mark,
as in _!FILE_, then the images from the
directory _FILE_ are permuted randomly.
Image file names or directory names may have wildcards,
which will be expanded according to [glob(7)](https://manned.org/glob.7).

- **-p**, **--replace**

    Replace an existing **icewmbg**. If there is a running **icewmbg** it is
    instructed to quit.  The new **icewmbg** will take over.

- **-q**, **--quit**

    Tell the running **icewmbg** to quit. This option is used by
    [icewm-session(1)](icewm-session.md) when [icewm(1)](icewm.md) exits.

- **-r**, **--restart**

    Tell the running **icewmbg** to restart itself.  This is useful when a
    background file or directory has changed or when settings in preferences
    files have changed.

- **-u**, **--shuffle**

    Shuffle the list of background images randomly.
    This option may be given again whenever the running
    **icewmbg** should reshuffle its list of background images.

- **-c**, **--config**=_FILE_

    Load preferences from _FILE_.

- **-t**, **--theme**=_THEME_

    Load the theme named _THEME_.

- **-i**, **--image**=_FILE_\[,_FILE_\]\*

    Load background images from each _FILE_.
    This overrules the `DesktopBackgroundImage` preference.

- **-k**, **--color**=_COLOR_\[,_COLOR_\]\*

    Use background colours from each _COLOR_.
    This overrules the `DesktopBackgroundColor` preference.

- **-s**, **--semis**=_FILE_\[,_FILE_\]\*

    Load transparency images from each _FILE_.
    This overrules the `DesktopTransparencyImage` preference.

- **-x**, **--trans**=_NAME_\[,_NAME_\]

    Use transparency colours for each _NAME_.
    This overrules the `DesktopTransparencyColor` preference.

- **-e**, **--center**={_0_\|_1_}

    Disable/Enable centring background.
    This overrules the `DesktopBackgroundCenter` preference.

- **-a**, **--scaled**={_0_\|_1_}

    Disable/Enable scaling background.
    This overrules the `DesktopBackgroundScaled` preference.

- **-m**, **--multi**={_0_\|_1_}

    Disable/Enable multi-head background.
    This overrules the `DesktopBackgroundMultihead` preference.

- **-y**, **--cycle**={_SECONDS_}

    Cycle over the list of background images every SECONDS.
    This overrules the `CycleBackgroundsPeriod` preference.

- **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    If this option is missing then _DISPLAY_
    is read from the environment variable `DISPLAY`.

- **--sync**

    Use a slower synchronous mode communication with _X11_ server.

## GENERAL OPTIONS

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# FILES

## PREFERENCES

By default **icewmbg** will load the background settings from the
[icewm(1)](icewm.md) preferences files (see [icewm-preferences(5)](icewm-preferences.md)).  The
settings read are:

    DesktopBackgroundCenter    - Display desktop background centered
    DesktopBackgroundScaled    - Display desktop background scaled
    DesktopBackgroundColor     - Desktop background color(s)
    DesktopBackgroundImage     - Desktop background image(s)
    ShuffleBackgroundImages    - Shuffle the list of background images
    SupportSemitransparency    - Support for semitransparent terminals
    DesktopTransparencyColor   - Semitransparency background color(s)
    DesktopTransparencyImage   - Semitransparency background image(s)
    DesktopBackgroundMultihead - One background over all monitors
    CycleBackgroundsPeriod     - Seconds between cycling over backgrounds

First these settings are read from the `preferences` file.  Then the
theme file from the current theme is read, which may overrule the
`preferences` settings.  Lastly the `prefoverride` file is read, which
overrides again.  Therefore, if you want to allow the theme to set the
background use `preferences` for your settings, otherwise use
`prefoverride`.  See [icewm-prefoverride(5)](icewm-prefoverride.md).

## SCALING

Often a background image has a different width or height than the
screen.  The settings can specify to centre (`DesktopBackgroundCenter`)
or scale (`DesktopBackgroundScaled`) an image.  Either option is either
**0** (disabled) or **1** (enabled).  What happens for their combination
is given by the following table:

    center:0 scaled:0 = the background is replicated in both directions
    center:1 scaled:0 = the background is centered, but not scaled
    center:1 scaled:1 = fill one dimension and keep aspect the ratio
    center:0 scaled:1 = fill both dimensions and keep aspect the ratio

# SIGNALS

**icewmbg** supports the following signals:

- **SIGHUP**

    **icewmbg** will restart itself.

- **SIGINT**, **SIGTERM**

    **icewmbg** will terminate.

- **SIGUSR1**

    **icewmbg** will reshuffle the list of background images and
    update the backgrounds of all work spaces.

# SEE ALSO

[icewm(1)](icewm.md),
[icewm-preferences(5)](icewm-preferences.md),
[icewm-prefoverride(5)](icewm-prefoverride.md),
[wmsetbg(1)](https://manned.org/wmsetbg.1),
[xsetbg(1)](https://manned.org/xsetbg.1),
[xv(1)](https://manned.org/xv.1).

# BUGS

**icewmbg** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[https://github.com/bbidulock/icewm/issues](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.
