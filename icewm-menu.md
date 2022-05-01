---
title: "icewm-menu(5)"
---
## NAME

    icewm-menu - icewm menu configuration file

## SYNOPSIS

    $ICEWM_PRIVCFG/menu
    $XDG_CONFIG_HOME/icewm/menu
    $HOME/.icewm/menu
    /etc/icewm/menu
    /usr/share/icewm/menu

## DESCRIPTION

The `menu` file is responsible for configuring most of the [icewm(1)](icewm)
root menu and start menu.

A menu of applications; usually customized by the user.  **icewm**
provides the [icewm-menu-fdo(1)](icewm-menu-fdo) program to generate a default menu.
Similar programs are [xdg\_menu(1)](https://manned.org/xdg_menu.1), [mmaker(1)](https://manned.org/mmaker.1) (MenuMaker),
[xde-menu(1)](https://manned.org/xde-menu.1), [xdgmenumaker(1)](https://manned.org/xdgmenumaker.1).

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

    This is the _title_ string associated with the menu item which is
    displayed in the menu.  When the _title_ contains spaces, the title
    must be surrounded by double quotes (``).

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

    _program_ is the name of the executable or full path to the executable
    file that will be run in response to selecting the menu item.
    When used with the **menuprog** keyword, the _program_ must print on
    standard output the contents of the menu and is used for dynamic menus.

    _options_ is the options and arguments passed to the _program_
    verbatim.

- _filename_

    _filename_ is the name of the file relative to one of the [icewm(1)](icewm)
    configuration directories, or the full path to a file.  The file is used
    with the **menufile** keyword and specifies the file from which to read
    further menu items.

## EXAMPLES

Following is the example `menu` file that ships with [icewm(1)](icewm):

    # This is an example for IceWM's menu definition file.
    #
    # Place your variants in @CFGDIR@ or in $HOME/.icewm
    # since modifications to this file will be discarded when you
    # (re)install icewm.
    #
    prog xterm xterm xterm
    prog rxvt xterm rxvt -bg black -cr green -fg white -C -fn 9x15 -sl 500
    prog fte fte fte
    prog NEdit nedit nedit
    prog Mozilla mozilla mozilla
    prog XChat xchat xchat
    prog Gimp gimp gimp
    separator
    menuprog "Desktop Apps" folder icewm-menu-fdo
    menufile Programs folder programs
    menufile Tool_bar folder toolbar

## FILES

Locations for the `menu` file are as follows:

    $ICEWM_PRIVCFG/menu
    $XDG_CONFIG_HOME/icewm/menu
    $HOME/.icewm/menu
    /etc/icewm/menu
    /usr/share/icewm/menu

The locations are searched in the order listed; the first file found is
read and the remainder ignored.

## SEE ALSO

[icewm(1)](icewm),
[icewm-menu-fdo(1)](icewm-menu-fdo).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
