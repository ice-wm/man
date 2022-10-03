---
title: "icewm-menu-fdo(1)"
---
## NAME

    icewm-menu-fdo - menu generator for .desktop files

## SYNOPSIS

**icewm-menu-fdo** \[_OPTIONS_\] \[_FILENAME_\]

## DESCRIPTION

**icewm-menu-fdo** generates a menu for the **IceWM** window manager
from XDG menu descriptors (aka FreeDesktop.Org `.desktop` files).
By including this in the [icewm-menu(1)](icewm-menu), the system applications
become available in the icewm start menu.

## ARGUMENTS

- \[_FILENAME_\]

    The optional _FILENAME_ argument is the location of a `.desktop` file.
    When given, **icewm-menu-fdo** launches the application using the `Exec`
    line from the desktop file.

## OPTIONS

- **-g**, **--generic**

    Include the generic name in parentheses in the title of **prog** entries.

- **--seps**

    Print a leading and a trailing separator.

- **--sep-before**

    Print a leading separator.

- **--sep-after**

    Print a trailing separator.

- **--no-sep-others**

    Don't print the `Other` category last.

- **--no-sub-cats**

    Don't nest subcategories in submenus.

- **-o**, **--output=FILE**

    Write the output to _FILE_.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## USAGE

This utility is not normally used directly. It is used as the
executable in a **menuprog** entry in a [icewm-menu(5)](icewm-menu).

## EXAMPLES

The following line in a [icewm-menu(5)](icewm-menu) file will dynamically generate
a comprehensive set of menus for easy access to `.desktop` files.

    menuprog "Desktop Apps" folder icewm-menu-fdo

## ENVIRONMENT

**XDG\_DATA\_HOME** or **XDG\_DATA\_DIRS** are considered as suggested by XDG
Base Directory Specification.

## CONFORMING TO

**icewm-menu-fdo** complies roughly to the XDG `.desktop` file and menu
specification, see ["Desktop Entry Specification"](https://standards.freedesktop.org/desktop-entry-spec/latest/), Version 1.2alpha,
2015-03-06 and ["Desktop Menu Specification"](https://specifications.freedesktop.org/menu-spec/latest/), Version 1.1-draft, 31
March 2011.

## CAVEATS

The **icewm-menu-fdo** program is only built when the [icewm(1)](icewm) package
is configured with the **--enable-menus-fdo** option, which requires the
**glib2-dev** package dependency.

## SEE ALSO

["Desktop Entry Specification"](https://standards.freedesktop.org/desktop-entry-spec/latest/),
["Desktop Menu Specification"](https://specifications.freedesktop.org/menu-spec/latest/),
[icewm(1)](icewm),
[icewm-menu(5)](icewm-menu),
[icewm-preferences(5)](icewm-preferences),
[icewm-programs(5)](icewm-programs).

## BUGS

Please report bugs at [Github](https://github.com/bbidulock/icewm/issues).

## AUTHOR

[Eduard Bloch](mailto:edi@gmx.de).

See **--copying** for full copyright notice and copying permissions.

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
