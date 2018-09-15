---
title: "icewm-menu-fdo(1)"
---
# NAME

    icewm-menu-fdo - menu generator for .desktop files

# SYNOPSIS

**icewm-menu-fdo** \[_FILENAME_\]

# DESCRIPTION

**icewm-menu-fdo** introduces the XDG menu descriptors (aka
FreeDesktop.Org `.desktop` files) to the menus of **IceWM** window
manager.

# ARGUMENTS

- \[_FILENAME_\]

    When provided with the optional _FILENAME_ argument that is the name
    and location of a `.desktop` file, **icewm-menu-fdo** will open it and
    launch the application using the `Exec` line from the desktop file.

# OPTIONS

This program doesn't use command line options. In future, it might
support the pass-through of arguments to the command run from `.desktop`
file's `Exec` line.

# USAGE

This utility is not normally used directly, but is used as the
executable in a **menuprog** entry in a menu.

# ENVIRONMENT

**XDG\_DATA\_HOME** or **XDG\_DATA\_DIRS** are considered as suggested by XDG Base Directory Specification.

# CONFORMING TO

**icewm-menu-fdo** complies roughly to the XDG `.desktop` file and menu
specification, see ["Desktop Entry Specification"](https://standards.freedesktop.org/desktop-entry-spec/latest/), Version 1.2alpha,
2015-03-06 and ["Desktop Menu Specification"](https://specifications.freedesktop.org/menu-spec/latest/), Version 1.1-draft, 31
March 2011.

# CAVEATS

The **icewm-menu-fdo** program is only built when the [icewm(1)](icewm.md) package
is configured with the **--enable-menus-fdo** option.

# SEE ALSO

["Desktop Entry Specification"](https://standards.freedesktop.org/desktop-entry-spec/latest/),
["Desktop Menu Specification"](https://specifications.freedesktop.org/menu-spec/latest/),
[icewm(1)](icewm.md),
[icewm-menu(5)](icewm-menu.md),
[icewm-preferences(5)](icewm-preferences.md),
[icewm-programs(5)](icewm-programs.md).

# BUGS

**icewm-menu-fdo** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[https://github.com/bbidulock/icewm/issues](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.
