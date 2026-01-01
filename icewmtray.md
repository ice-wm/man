---
title: "icewmtray(1)"
---
## NAME

    icewmtray - a system tray for the IceWM panel

## SYNOPSIS

- **icewmtray** \[_OPTIONS_\]
- **icewmtray** {**-h**\|**--help**} \[_OPTIONS_\]
- **icewmtray** {**-V**\|**--version**}
- **icewmtray** {**-C**\|**--copying**}

## DESCRIPTION

**icewmtray** provides a system tray for the IceWM panel.  It catches the
system tray objects that are installed by various applications.

## OPTIONS

**icewmtray** recognizes the following options:

## COMMAND OPTIONS

Command options are mutually exclusive.  Only one command option can be
specified per invocation.  If no command option is specified, argument
parsing and processing is performed.

- **-h**, **--help**

    Print a brief usage statement to `stdout` and exit.

- **-V**, **--version**

    Print the program version to `stdout` and exit.

- **-C**, **--copying**

    Print copying permissions to `stdout` for the program and exit.

## GENERAL OPTIONS

**icewmtray** recognizes the following options:

- **-n**, **--notify**

    Specifies that **icewmtray** is to notify its parent process by sending
    the **SIGUSR1** signal.  This option is used by [icewm-session(1)](icewm-session) when
    starting up components so that it can wait for component startup to
    complete.

- **-c**, **--config** _FILENAME_

    Specifies the configuration file to use.

- **-t**, **--theme** _THEME_

    Specifies an override theme to use.

- **-d**, **--display**=_DISPLAY_

    Use _DISPLAY_ to connect to the X server.
    If this option is missing then _DISPLAY_
    is read from the environment variable `DISPLAY`.

- **--debug**

    Specifies that debugging is to be turned on.  **icewmtray** must have
    been compiled with debugging for this option to have an effect.

## USAGE

**icewmtray(1)** is typically launched and terminated by
[icewm-session(1)](icewm-session) with the appropriate options: it is usually
unnecessary to launch it directly.

## CONFORMING TO

**icewmtray** is compliant to the XDG system tray specification.

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
