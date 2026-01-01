---
title: "icehelp(1)"
---
## NAME

    icehelp - a very simple HTML browser

## SYNOPSIS

**icehelp** \[_OPTIONS_\] _FILENAME_

## DESCRIPTION

**icehelp** is a very simple HTML browser, which is used by [icewm(1)](icewm)
to display the [IceWM Manual](https://ice-wm.org/manual) and the manpages.

The document can be navigated by cursor keys, navigation keys and
a scrollbar. To find text, hit `Ctrl+F` for a search window.
Hit the `F3` function key to repeat a search.

The top right corner shows a button, which opens a menu. This menu
can also be opened by a right mouse button click.

## ARGUMENTS

- _FILENAME_

    Specifies the file to browse.  It can also be the URL of a website.

## OPTIONS

## SPECIFIC OPTIONS

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

- **-d**, **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    If this option is missing then _DISPLAY_
    is read from the environment variable `DISPLAY`.

- **--sync**

    Use a slower synchronous mode communication with _X11_ server.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## BUGS

Please report bugs at [Github](https://github.com/ice-wm/icewm/issues).

## AUTHOR

[Brian Bidulock](mailto:bidulock@openss7.org).

See **--copying** for full copyright notice and copying permissions.

## LICENSE

**IceWM** is licensed under the GNU Library General Public License.
See the `COPYING` file in the distribution or use the **--copying** flag
to display copying permissions.

| ------------: | :--------- |
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
