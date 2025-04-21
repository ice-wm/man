---
title: "icewm-programs(5)"
---
## NAME

    icewm-programs - icewm programs configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/programs
    $XDG_CONFIG_HOME/icewm/programs
    $HOME/.icewm/programs
    /etc/icewm/programs
    /usr/share/icewm/programs

## DESCRIPTION

The `programs` file is an automatically generated menu configuration
file of installed programs. This file should be automatically generated
by xdg\_menu, wmconfig (Redhat), menu (Debian), or icewm-menu-fdo,
perhaps as part of the login or X startup sequence.

## FORMAT

The format of the file contains one of the following line syntax:

- **prog** \[**"**\]_title_\[**"**\] _icon_ _program_ _options_

    Specifies a program to execute when the menu item is selected.

- **restart** \[**"**\]_title_\[**"**\] _icon_ _program_ _options_

    Specifies a program to replace the window manager when the menu item is
    selected.  This is for launching other window managers from within
    [icewm(1)](icewm).

- **runonce** \[**"**\]_title_\[**"**\] _icon_ **"**\[_res\_name_\]\[**.**_res\_class_\]**"** _program_ _options_

    Specifies a program to execute when the menu item is selected; however,
    if a window of the specified _res\_name_ and _res\_class_ is present,
    the program will not be run again.

- **menu** \[**"**\]_title_\[**"**\] _icon_ **{**
 # contained items
 **}**

    Specifies a sub-menu.  The lines that appear between the braces can be
    any menu item described here.

- **menufile** \[**"**\]_title_\[**"**\] _icon_ \[**"**\]_filename_\[**"**\]

    Specifies a file from which to collect sub-menu items (lines) and place
    them at this point in the menu.

- **menuprog** \[**"**\]_title_\[**"**\] _icon_ _program_ _options_

    Specifies a program that will print sub-menu items on standard output
    and will be collected and placed in the sub-menu at this point.

- **menuprogreload** \[**"**\]_title_\[**"**\] _icon_ _timeout_
_program_ _options_

    Similar to **menuprog**, but after at least _timeout_ seconds
    the menu is regenerated.

- **include** \[**"**\]_filename_\[**"**\]

    Read additional entries from the file _filename_

- **includeprog** _program_ _options_

    Read additional entries from the output of _program_ _options_.

- **separator**

    A separator for menu items.

Where

- **prog**, **restart**, **runonce**, **menu**, **menufile**,
**menuprog**, **menuprogreload**, **include**, **includeprog**, **separator**

    These are literal string keywords.

- \[**"**\]_title_\[**"**\]

    This is the _title_ string associated with the menu item that is
    displayed in the menu.  When the _title_ contains spaces, the title
    must be surrounded by double quotes (`"`), although the _title_ may
    always be surrounded by double quotes if preferred.

- _icon_

    Is the name of the icon file (with or without extension) or the full
    path to an icon file.

- **"**\[_res\_name_\]\[**.**_res\_class_\]**"**

    _res\_name_ is the resource name of a window launched by _program_ and
    _res\_class_ is the resource class of the window.  Only one of
    _res\_name_ or _res\_class_ need be specified.  This is used to identify
    whether the program is already running and is for use with the
    **runonce** keyword.

- _program_ _options_

    _program_ is the name of the executable or full path to the executable file that will
    be run in response to selecting the menu item.  When used with the
    **menuprog** keyword, the _program_ must print on standard output the
    contents of the menu and is used for dynamic menus.

    _options_ is the options and arguments passed to the _program_
    verbatim.

- _filename_

    _filename_ is the name of the file relative to one of the [icewm(1)](icewm)
    configuration directories, or the full path to a file.  The file is used
    with the **menufile** keyword and specifies the file from which to read
    further menu items.

## EXAMPLES

Following is the example `programs` file that ships with [icewm(1)](icewm):

    # This file is intended to be customized by the distributions.
    # (they should place it in /etc/X11/icewm)
    #
    # mostly obsolete, fixme
    menu Editors folder {
        prog vim vim gvim
        prog emacs emacs emacs
        prog Lyx emacs lyx
    }
    menu "WWW" folder {
        prog Galeon galeon galeon
        prog Arena arena arena
        prog Lynx lynx xterm -e lynx
        prog Links lynx xterm -e links
    }
    menu "Document Viewers" folder {
        prog "DVI Previewer" xdvi xdvi
        prog "Ghostview" ghostview gv
    }
    menu Graphics folder {
        prog Gimp gimp gimp
        prog XV xv xv
        prog XPaint xpaint xpaint
        prog XFig xfig xfig
    }
    menu Games folder {
        prog Xboard xboard xboard
        prog "Tux Racer" tuxracer tuxracer
    }
    menu System folder {
        prog "Control Panel" redhat control-panel
    }
    menu Utilities folder {
        prog XPlayCD xplaycd xplaycd
        prog XMixer xmixer xmixer
        prog Clock xclock xclock
        prog Magnify xmag xmag
        prog Calculator xcalc xcalc
        prog Colormap xcolormap xcmap
        prog Clipboard xclipboard xclipboard
        prog xkill bomb xkill
        prog xload xload xload
        prog xosview xosview xosview
        separator
        prog "Screen Saver" xlock xlock -nolock
        prog "Screen Lock" xlock xlock
    }
    menu "Window Managers" folder {
        restart icewm - icewm
        restart metacity - metacity
        restart wmaker - wmaker
        restart fluxbox - fluxbox
        restart blackbox - blackbox
        restart enlightenment - enlightenment
        restart fvwm2 - fvwm2
        restart fvwm - fvwm
        restart sawfish - sawfish
        restart sawfish2 - sawfish2
    }

## FILES

Locations for the `programs` file are as follows:

    $ICEWM_PRIVCFG/programs
    $XDG_CONFIG_HOME/icewm/programs
    $HOME/.icewm/programs
    /etc/icewm/programs
    /usr/share/icewm/programs

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icewm-menu(5)](icewm-menu),
[icewm-menu-fdo(1)](icewm-menu-fdo).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
