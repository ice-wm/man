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

- **--no-sub-cats**

    Don't nest subcategories in submenus. The correctness of the
    pigeonholing depends on correct application description which shall
    always specify a main category. Incorrectly tagged descriptions will be
    sorted into the `Other` menu.

- **-o**, **--output=FILE**

    Write the output to _FILE_.

- **-t**, **--terminal=NAME**

    Use _NAME_ to start a terminal emulator that supports the '-e' option.

- **-s**, **--no-lone-app**

    Attempt to detect a single application with no other content in lower
    submenus and move this one to the parent submenu. This also detects
    menus with just one submenu inside, attempting to move it's application
    items to the parent menu where possible.

- **-S**, **--no-lone-hint**

    Decorate app entries moved by the **-s** option with a hint about the
    original menu where it would be displayed otherwise. Implies **-s**.

- **-d TIMEOUT**, **--deadline-apps=TIMEOUT**

    Specifies a certain timeout value in milliseconds, so that the reading
    of \*.desktop files (for applications) is aborted by that time (or soon
    after). This can help to avoid extended blocking of the caller.
    Also see **-D** for the subsequent operation.

- **-D TIMEOUT**, **--deadline-all=TIMEOUT**

    Specifies a total timeout in milliseconds after which the application
    has to terminate, regardless of the final menu construction and
    decoration reading (applied after \*.desktop file reading) was finished
    or not. This would cause a printing of menu contents which were
    calculated so far, therefore the timeout should be set a certain time
    before the actual hard deadline by which the program should be
    terminated. The output may lack translations and icons.

- **-L MAX**, **--limit-max-len=MAX**

    Cut the calculated program titles (after translation and adding
    hints, see `-C` and `-g`) at `MAX` characters, followed by an
    ellipsis. This can help to restrict the width of the menus in cases
    where some entry length might get out of hand.

- **--flat**

    Display apps from all categories in one level with the title containing
    the category information as prefix.

- **-F sep**, **--flat-sep=sep**

    When used with `--flat`, the specified character sequence is used as
    separator between the section titles.

- **-m filter**, **--match=filter**

    Specifies a filter to show only apps that contain this as substring
    within their title.

- **-M filter**, **--imatch=filter**

    Like `--match` but applied with any letter case. Might deliver
    incorrect results with some locale settings.

- **--match-sec**

    Apply the filter from `--match` or `--imatch` to both, apps and
    section titles.

- **--match-osec**

    Apply the filter from `--match` or `--imatch` to only to section titles.

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
a comprehensive set of menus for easy access to `.desktop` files, added
in a submenu called `Desktop Apps`.

    menuprog "Desktop Apps" folder icewm-menu-fdo

It can also be embedded directly into the loading menu like in the
following example. There could be a separator line added before or after
(or both) in case where the program could generate useful content.

    includeprog icewm-menu-fdo --seps

## ENVIRONMENT

**XDG\_DATA\_HOME** or **XDG\_DATA\_DIRS** are considered as suggested by XDG
Base Directory Specification.

**TERMINAL** may define a terminal emulator that supports the '-e'
option. The option is ignored if the specified command could not be
found and a default is used instead.

## CONFORMING TO

**icewm-menu-fdo** complies roughly to the XDG `.desktop` file and menu
specification, see ["Desktop Entry Specification"](https://standards.freedesktop.org/desktop-entry-spec/latest/) (Date: 2020-04-27,
Version: Version 1.5) and ["Desktop Menu Specification"](https://specifications.freedesktop.org/menu-spec/latest/) (Date: 20 August
2016, Version: Version 1.1).

## CAVEATS

The **icewm-menu-fdo** program is only built when the [icewm(1)](icewm) package
is configured with the **--enable-menus-fdo** option and only works with
**--enable-i18n** option.

Integration of XDG menu files is somewhat of varying quality, heavily
depending on the correctness of metadata like translations and sections
(menu category) hints.

## SEE ALSO

[Base Directory Specification](https://www.freedesktop.org/wiki/Specifications/basedir-spec/),
[Desktop Entry Specification](https://www.freedesktop.org/wiki/Specifications/desktop-entry-spec/),
[Desktop Menu Specification](https://www.freedesktop.org/wiki/Specifications/menu-spec/),
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
