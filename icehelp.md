---
title: "icehelp(1)"
---
# NAME

    icehelp - a very simple HTML browser

# SYNOPSIS

**icehelp** \[_OPTIONS_\] _FILENAME_

# DESCRIPTION

**icehelp** is a very simple HTML browser that displays the document
specified on the command line.  It is used by [icewm(1)](icewm.md) internal to
display the ["IceWM Manual"](/manual) and the manual pages.

# ARGUMENTS

- _FILENAME_

    Specifies the absolute or relative path (relative to the current working
    directory), that specifies the HTML file to browse.
    _FILENAME_ may also be the URL of a website.

# OPTIONS

## SPECIFIC OPTIONS

- **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    If this option is missing then _DISPLAY_
    is read from the environment variable `DISPLAY`.

- **--sync**

    Use a slower synchronous mode communication with _X11_ server.

- **-B**

    Display the IceWM icewmbg manpage.

- **-b**, **--bugs**

    Display the IceWM bug reports (primitively).

- **-f**, **--faq**

    Display the IceWM FAQ and Howto.

- **-g**

    Display the IceWM Github website.

- **-i**, **--icewm**

    Display the IceWM icewm manpage.

- **-m**, **--manual**

    Display the IceWM Manual (default).

- **-s**

    Display the IceWM icesound manpage.

- **-t**, **--theme**

    Display the IceWM themes Howto.

- **-w**, **--website**

    Display the IceWM website.

## GENERAL OPTIONS

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

# BUGS

**icehelp** had no known bugs at the time of release.  Please report bugs
for current versions to the source code repository at
[Github](https://github.com/bbidulock/icewm/issues).

# AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

# LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM][/images/logom.jpg]](https://ice-wm.org "ice-wm.org") |
