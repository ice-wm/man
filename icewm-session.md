---
title: "icewm-session(1)"
---
# NAME

    icewm-session - X.Org session manager provider with IceWM

# SYNOPSIS

**icewm-session** \[_OPTIONS_\]

# DESCRIPTION

icewm-session is an implementation of X.Org session manager and can be
run from X11 session setup. It runs **icewm** as default window manager
and handles the startup and lifecycle control of the WM and all related
support applications.

# OPTIONS

## SPECIFIC OPTIONS

- **-c**, **--config=FILE**

    Let IceWM load preferences from _FILE_.

- **-t**, **--theme=FILE**

    Let IceWM load the theme from _FILE_.

- **-i**, **--icewm=FILE**

    Use _FILE_ as the IceWM window manager.

- **-n**, **--notray**

    Do not start icewmtray.
    This is only applicable if IceWM was explicitly configured
    to use an external icewmtray process.

- **-s**, **--sound**

    Also start icesound.

## GENERAL OPTIONS

- **--display**=_DISPLAY_

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

# BUGS

**icewm-session** had no known bugs at the time of release.  Please report bugs
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
| [Index](/man) | [![IceWM](/images/logom.jpg "ice-wm.org")](https://ice-wm.org "ice-wm.org") |
