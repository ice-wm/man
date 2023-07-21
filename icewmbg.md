---
title: "icewmbg(1)"
---
## NAME

    icewmbg - a background settings manager for the IceWM window manager

## SYNOPSIS

**icewmbg** \[_OPTIONS_\]

## DESCRIPTION

**icewmbg** can assign a colour or image to the _X11_ desktop background.
Common image formats are supported.  Each [icewm(1)](icewm) workspace can have
its own background.

When the background image changes, **icewmbg** can be notified to
update the background.  When switching workspaces, it checks the image
file modification time.  If the file has changed, it reloads the
image from file.

**icewmbg** supports semitransparency.  Semitransparent background
images and colours can be configured.

It uses RandR or Xinerama to support backgrounds on all connected
monitors.  When monitors appear/disappear, or change their resolution,
**icewmbg** will adjust.  It supports an option for one large background
over all monitors.

It will update the `_ICEWMBG_IMAGE` property of the root window to the
path of the background image whenever it changes the desktop background.

**icewmbg** is started automatically by [icewm-session(1)](icewm-session).
If there is just a single background for all workspaces, icewmbg may
conclude that it can safely exit after setting the desktop background,
to free its system memory.  If the screen size changes, icewm will then
attempt to restart icewmbg, preferably via icewm-session.

## OPTIONS

## SPECIFIC OPTIONS

Where multiple values can be given for images
or colours, they are separated by comma's.
Each such value may be enclosed in double quotes.
If _FILE_ is a directory, all images
from that directory are used in sorted order.
If the value starts with an exclamation mark, as in _!FILE_,
the images from the directory _FILE_ are permuted randomly.
Image file names or directory names may have [glob(7)](https://manned.org/glob.7) wildcards,
or they may start with a tilde or environment variable.

- **-p**, **--replace**

    Replace an existing **icewmbg**. If there is a running **icewmbg**,
    it is instructed to quit.  The new **icewmbg** will take over.

- **-q**, **--quit**

    Tell the running **icewmbg** to quit. This option is used by
    [icewm-session(1)](icewm-session) when [icewm(1)](icewm) exits.

- **-r**, **--restart**

    Tell the running **icewmbg** to restart itself.  This is useful when
    settings in have changed. If no icewmbg is active, it starts one.

- **-u**, **--shuffle**

    Shuffle the list of background images randomly.
    This option may be given again whenever the running
    **icewmbg** should reshuffle its list of background images.

- **-c**, **--config**=_FILE_

    Load preferences from _FILE_.

- **-t**, **--theme**=_THEME_

    Use the theme named _THEME_.

- **-i**, **--image**=_FILE_\[,_FILE_\]\*

    Load background images from each _FILE_.
    This overrules the `DesktopBackgroundImage` preference.
    When more than one image is given, they are assigned
    to each workspace in the given order.

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

    Disable or enable a single background over all monitors.
    This overrules the `DesktopBackgroundMultihead` preference.

- **-y**, **--cycle**=_SECONDS_

    Cycle over the list of background images every _SECONDS_.
    This overrules the `CycleBackgroundsPeriod` preference.

- **-o**, **--output=FILE**

    Redirect all output to _FILE_.
    A leading tilde or environment variable is expanded.

## GENERAL OPTIONS

- **-d**, **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    Otherwise use DISPLAY from the environment.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

- **--sync**

    Use a slow synchronous mode to communicate with the _X11_ server.

- **--verbose**

    Report on some of the activities.

## FILES

## PREFERENCES

By default **icewmbg** loads settings from the [icewm(1)](icewm)
preferences file. See [icewm-preferences(5)](icewm-preferences) for details.
The settings read are:

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

If these settings are set in the `preferences` file, they can
be overridden by the theme in the theme defaults file.
To enforce a certain setting, set it in the `prefoverride` file instead.
See [icewm-prefoverride(5)](icewm-prefoverride).

## WORKSPACES

Each workspace can have a unique image. Specify multiple images to
**DesktopBackgroundImage** separated by comma's.  Or give at least one
directory with images. The images are assigned to each workspace in
the order given. When icewm changes workspace, the running icewmbg
will adapt the desktop background to the assigned image.

If you specify more images then there are workspaces, then
**CycleBackgroundsPeriod** can set a period. When the period expires,
icewmbg will switch to the next set of images. If you give less images
than there are workspaces, then icewmbg will reuse previous images
for the remaining workspaces.

## IMAGE SCALING

Often a background image has a different width or height than the screen.
The image can then be replicated (tiled), centered or scaled. This is
controlled by `DesktopBackgroundCenter` and `DesktopBackgroundScaled`.
What happens for their combination is given by the following table:

    center:0 scaled:0 = The background is replicated in both directions.
    center:1 scaled:0 = The background is centered, but not scaled.
    center:1 scaled:1 = Fill one dimension and preserve the aspect ratio.
    center:0 scaled:1 = Fill both dimensions and preserve the aspect ratio.

## EXAMPLES

    # For four unique desktop backgrounds for four workspaces do:

    icewmbg -p -i image0,image1,image2,image3 &

    # Or create a directory with the four images and do:

    icewmbg -p -i /path/to/directory &

    # The images should have proper image filename extensions.

## SIGNALS

**icewmbg** supports the following signals:

- **SIGHUP**

    **icewmbg** will restart itself.

- **SIGINT**, **SIGTERM**

    **icewmbg** will terminate.

- **SIGUSR1**

    **icewmbg** will reshuffle the list of background images and
    update the backgrounds of all workspaces.

## SEE ALSO

[icewm(1)](icewm),
[icewm-preferences(5)](icewm-preferences),
[icewm-prefoverride(5)](icewm-prefoverride),
[wmsetbg(1)](https://manned.org/wmsetbg.1),
[xsetbg(1)](https://manned.org/xsetbg.1),
[xwallpaper(1)](https://manned.org/xwallpaper.1).

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
